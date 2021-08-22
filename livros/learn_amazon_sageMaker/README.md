# Livro Learn Amazon SageMaker
[Link Livro](https://www.packtpub.com/product/learn-amazon-sagemaker/9781800208919)

## Chapter 2 

- Amazon SageMaker Ground Truth
	- Serviço que permite compartilhar um dataset(pode ser texto ou imagens) com um grupo de pessoas(workers) de dentro da propria empresa ou ao redor do mundo
	- O que essas pessoas(workers) farão?
		- Para treinar um modelo de machine learning para fazer reconhecimento de imagens por exemplo, é necessario treina-lo com imagens que estejam rotuladas(Esse rótulo deve ser feito por um humano)
		- Ex: Eu tenho uma imagem de um gato e eu tenho um metadado que diz que aquela imagem tem um gato
		- Para disponibilizar essas imagens "rotuladas"
			- Podemos obter uma base de dados rotulada
			- Ou, podemos nós mesmos rotular uma base de imagens/dados
			- Dependendo da quantidade de imagens/dados a serem rotulados "manualmente", precisaremos de um time de pessoas para fazer isso, e é ai que o SageMaker Ground Truth entra
		
- Amazon SageMaker Processing
  - Serviço representado por um container docker com python, jupyter, scikit-learn quer permite rodar as principais tarefas de Pre-Processamento(Limpeza de dados)
  - Todos os logs são disponibilizados no CloudWatch
  - Basicamente consumimos um dataset do S3, fazemos uma limpeza e gravamos o dataset limpo e ajustado no S3
  - Utilizando a função SKLearnProcessor do sagemaker, podemos rodar nosso script com todas as etapas de limpeza
	- Teremos um arquivo python com uma função onde dentro dela temos todas as etapas de limpeza
	- Teremos um outro arquivo python, onde nele utilizando SKLearnProcessor, chamamos a função do arquivo anterior
	- Exemplos:
	  - https://github.com/PacktPublishing/Learn-Amazon-SageMaker/blob/master/sdkv2/ch2/smprocessing/DM%20processing.ipynb
	  - https://github.com/PacktPublishing/Learn-Amazon-SageMaker/blob/master/sdkv2/ch2/smprocessing/preprocessing.py

- Amazon Elastic Map Reduce - AEMR
  - Serviço que permite em uma instância do jupyter notebook processar dados no Spark utilizando PySpark
  - SparkMagic - Recurso que permite rodar o conteúdo de uma instância do jupyter notebook em um cluster de máquinas(AWS EMR)

- AWS Glue
  - Plataforma Gerenciada de ETL

- Amazon Athena
  - Servless que permite consultar dados disponiveis no S3(Arquivos) utilizando queries SQL


## Chapter 3

- Amazon SageMaker Autopilot
  - Ferramenta AutoML
	  - Executa sem nessidade de codificação principais steps de um fluxo de Machine Learning de forma automatizada e pré-configurada
		  - Algoritmos suportados
			  - Linear regression, binary classification, and multi-class classification
	- Seleciona automaticamente o melhor algoritmo baseado na estrutura dos dados
	- Disponibiliza um jupyter notebook com todo o código gerado para os steps do ML(pre-processing, feature engineering and so on)
	- Quando configuramos um novo "Experiment" AutoPilot Job, podemos definir que a saída do mesmo será a execução ou apenas a geração do notebook com o código
	- Irá realizar N execuções(podem ser especificadas via conf) e baseado na métrica que escolhermos, aponta na listagem qual modelo melhor performou
	- Após isso, com alguns cliques podemos fazer deploy do modelo(disponibilizar o mesmo em um endpoint)


## Chapter 4

- AWS criou e mantém algoritmos de ML próprios
  - Linear Regression, Factorization Matrix, PCA and so on...
- Após treinar o modelo, podemos facilmente expor o mesmo como um endpoint através do método deploy

## Chapter 7

- Podemos usar algoritmos de Machine Learning que não estejam presentes nos container pre-buildados da AWS
  - Uma forma de fazer isso é utilizar o Script Mode
	  - Script Mode
		  - Consiste em utilizar containers pre montados com python e principais libs de machine learning e através de um script externo podemos executar todos os steps de ML
  - A idéia aqui é baixar containers que ja possuem uma instalação basica(Python e principais libs de ML) para rodarmos ML
	  - Podemos ainda instalar e usar outras libs que não esteja presente nas mesmas
		- Ainda assim, estaremos usando um bult-in container(Container já configurado)
  - Podemos usar o sckit-learn ou o XGBoost por exemplo
	- Necessário baixar do Dockerfile de um dos containers ML pre montados da AWS(https://aws.amazon.com/pt/machine-learning/containers/)
	  - Caso precisemos de libs adicionais, incluir no Dockerfile a instalação dos mesmos("pip install")
	- Depois de ajustado o Dockerfile e buildado a imagem, devemos fazer o push dessa imagem ajustada para o Amazon ECR
	- Na hora de instânciar o modelo podemos usar o objeto Estimator do sagemaker ou um objeto que represente a base da instalação do container que ajustamos(XGBoost, ScikitLearn e etc...)
	  - Nesse objeto informamos o nosso container ajustado e disponibilizado no Amazon ECR
	- Script Mode
	  - Precisamos de um script onde terá todos os steps de pre-processamento, treinamento e gravação do modelo final no S3
	    - Esse script tem que seguir a seguinte estrutura(https://github.com/PacktPublishing/Learn-Amazon-SageMaker/blob/master/sdkv2/ch7/xgb/xgb-dm.py)
	  - O script é passado como parâmetro(entry point script) do objeto para o qual passamos nosso container disponibilizado no Amazon ECR
	- Implementar função "model_fn()" que será chamada no "deployment time"

## Chapter 9

  - Princípios de uma boa customização
	  - Recursos AWS são cobrados por tempo de uso, então quanto menos tempo, menos custo
		- Utilizar o máximo do recurso obtido, visando diminuir o tempo de treinamento
		  - Se o processamento consumiu apenas 50% da CPU, podemos fazer, de duas, uma
			  - Escolher uma instância com 50% menos CPU(Desde que mantenha o mesmo tempo de treinamento)
				- Alterar os parâmetros do treinamento de forma que possa utilizar próximo dos 100% de processamento, o que em tese acelerará o tempo gasto no treinamento
		- As dimensões analisadas são CPU x GPU x Memory x Disk Size 
  - Métrica interessante para avaliar
	  - Quantidade de samples processadas por segundo no treinamento do modelo
  - Outras métricas a serem consideradas
    - CPU and GPU utilization of the training container
    - Memory utilization of the training container (percentage of total memory available)
    - Disk utilization (percentage of total disk available)
    - Training throughput (samples per second)
	- Formas de Tunar o Treinamento
	  - Vertical(Aumentando a instância - Com mais processamento e memória)
		- Horizontal(Multiplas instâncias)
		- Distributed Training - Tem a ver com Horizontal (Verificar se o algoritmo suporta)
		- Pipe Mode - Pode ser usado tanto na Vertical quanto na Horizontal
		- Utilizando FileServers tunados além do S3
	- Caso o algoritmo de ML suporte GPU, escolher instâncias com GPU irão fazer processar mais rápido e barato
	- Utilizar o Pipe Mode(modo de consumir/ler o dataset) pode ajudar a melhorar a performance
		- Existem duas formas de obter o arquivo pelo algoritmo
			- File Mode
				- O Algoritmo copia o arquivo inteiro para a instância de treinamento
			- Pipe Mode
				- O Algoritmo consome o arquivo como streaming, ou seja, não existe cópia do arquivo para a instância e conforme vai lendo da origem já vai treinando o modelo
				- Os algoritmos built-in já tem suporte nativo ao Pipe Mode
				- Para uso de outros algoritmos ncessário implementar o modo Pipe Mode dentro do container
					- https://github.com/awslabs/amazon-sagemaker-examples/tree/master/advanced_functionality/pipe_bring_your_own
	- 


## Chapter 10

- Otimizando custos
  - Usar Managed Spots
    - Managed Spots são instâncias disponíveis na AWS 
		- Visando não deixar máquina parada eles disponibilizam elas com custo menor 
		- Custam até 70% menos que instâncias on-demand
		- Podemos especificar na configuração do modelo via SageMaker se queremos usar uma instância Managed Spot
    - Instâncias Managed Spot podem ser requeridas a qualquer momento pela AWS, o que pode interromper o uso dela em 2 minutos
    - Uma vez requerido a instância Spot sendo usada, temos dois minutos para preparar o fim forçado do processamento
    - Treinamento em Instâncias Spot devem durar até 1 hora
    - Caso leve mais tempo que isso, devemos otimizar o processamento distribuindo o processamento por exemplo
    - Para evitar ter que começar um training do zero em caso de interrupção, podemos implementar checkpoints na execução do algoritmo de ML
    - O checkpoint deve ser gravado no S3
		- Ao restartar o treinamento após achar outra instância Spot, nosso algoritmo deve ser capaz de ler esse checkpoint no S3 e informar ao algoritmo ML de onde ele deve startar  		
  - Automatic Model Tuning
    - Permite especificar um range de cada hyperparamater do modelo, treinando o modelo com várias configurações, tendo assim ao final o modelo com melhor acurácia
  - SageMaker Debuger
    - Possui Rules(Classes ou Funções) que adicionadas na configuração da execucação do Modelo, permite registrar alguns pontos específicos no step da execução do Modelo. Seria um console.log na execução do Modelo.


## Chapter 11

- Estrutura básica de deploy
  - Modelo treinado é um arquivo que deve ser armazenado no S3 ou em um repositório GIT
	- Criar um script que baixa esse modelo, importa no SageMaker SDK ou boto3 SDK e deploya o mesmo através de um endpoint
- Deploy Realtime endpoints
	- Ao utilizar o método "deploy" do sagemaker para criar o endpoint, podemos atualizar um endpoint existente através da propriedade "update_endpoint"
	- Para fazer deploy em um modelo em PROD através de um endpoint podemos usar:
		- SageMaker SDK - Menos verboso, porém como menos opções
		- boto3 - SKD Python que permite configurarmos mais opções de para o deploy do modelo
			- Podemos especificar dois modelos e definirmos um peso para cada modelo
				- Dessa forma, as requisições serão direcionadas para cada modelo de acordo com o peso dado ao mesmo
				- Para que serve isso?
					- Imagina que estamos querendo testar um novo modelo em PROD
						- Dessa forma não queremos direcionar tudo para ele, apenas uma parte das requisições
- Deploy Batch Tranformers
  - Podemos querer executar predições offline em 10GB de dados por exemplo e depois armazenar isso em algum lugar
  - Para isso utilizamos o recurso de Batch Transformers
  - Os endpoints criados na instânciação do transformer, serão excluídos ao final do processamento
- Deploy Inference Pipelines
  - Recurso que permite processarmos a inferência passando por mais de um modelo em um mesmo endpoint
- Monitorar Predições
  - AWS SageMaker Monitor(https://aws.amazon.com/pt/sagemaker/model-monitor/)
  - Recurso que permite registrar inputs e outputs(predições) dos endpoints/modelo
  - Para que?
    - Identificar a deterioração da acurácia do Modelo
  - Possui built-in containers, porém pode ser configurado um próprio 		
  - Permite registrar e quantificar "bad request", com dados inválidos para a predição
	

## Chapter 12 - Machine Learning Workflows

- Model, Endpoint configuration e Endpoint
- AWS CloudFormation
  - Recurso que via script permite automatizar o processo de deploy de um modelo de ML em PROD
  - Permite fazer deploy utilizando técnicas como "canary" e "blue-green"
    - Técnicas que gradativamente vão direcionando as requests para o novo modelo
    - Quando o novo modelo estiver devidamente estável, derruba a instância do modelo antigo
    - Caso ocorra erro no novo modelo, faz rollback de toda instalação do modelo novo e redireciona novamente 100% das requisições para o antigo
- Cloud Development Kit - CDK
  - SDK MultiLinguagem quer permite codificar toda a infraestrutura de um deploy qualquer, inclusive um de Machine Learning
- AWS Step Functions
  - Recurso que permite automatizar todo o processo de Machine Learning(Treinamento do Modelo, Teste e Deploy do Endpoint)
