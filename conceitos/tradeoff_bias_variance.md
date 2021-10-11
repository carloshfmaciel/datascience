## Viés(Bias) x Variância(Variance)
- O que são?
  - Viés e Variância são dois erros de previsão que ocorrem principalmente durante o processo de aprendizagem de máquina(no processo de treino e teste)

## Modelo
O principal objetivo de um modelo de ML é aprender um padrão e identificar onde esse padrão se repete sobre novos dados
- O que é um bom modelo?
  - É aquele que consegue aprender os padrões, ou seja, generalizar os dados de treinamento e prever com acurácia/baixo erro, padrões de novos dados
  - Possuir Baixo Viés e Baixa Variância

## O que é trade-off
Expressão em inglês que significa escolher uma coisa em detrimento de outra, ou seja, seria a busca de um meio termo
			
## Viés(Bias)
- O que é Viés(Bias)?
  - A diferença entre o MONTANTE do valor real/alvo e o valor previsto pelo modelo, ou seja, o quanto o modelo ERRA em prever sobre os dados de treinamento
  - O conceito de Viés em ML sempre está relacionado aos dados de treinamento
- Portanto um bom modelo deve ter BAIXO VIÉS(baixo erro)
- Tipos de Viés(Bias)
  - Viés Alto/High Bias
    - Quando o modelo erra muito sobre os dados de treinamento
  - Viés Baixo/Low Bias
    - Quando o modelo erra pouco sobre os dados de treinamento
						
## Variância(Variance)
- O que é Variância(Variance)?
  - É a diferença que ocorre entre a quantidade de erros/acertos sobre os dados de treinamento, versus o montante de erros/acertos sobre os dados de teste
  - O conceito de Variância aqui sempre está relacionado aos dados de teste
- Tipos de Variância
  - Alta Variância/High Variance
    - Quando o modelo erra muito sobre os dados de teste
  - Baixa Variância/Low Variance
    - Quando o modelo erra pouco sobre os dados de teste			

## O que faz o modelo ter viés alto(errar muito sobre os dados de treinamento) e/ou variância alta?
  - Seleção de um modelo(algoritmo de ML) não apropriado para o dataset/tipo do problema
  - Baixa qualidade dos dados(inclusão de dados que são inúteis para a previsão - ruído)
  - Adição de complexidade
			
## Overfitting e Underfitting
Dependendo da qualidade dos dados de treinamento e dos ajustes que realizamos no modelo, o modelo pode se ajustar demais ou menos do que deveria.<br>
Quando o modelo não se ajusta, ou seja, não consegue capturar os padrões dos dados de treinamento, ele também é incapaz de prever com acerto sobre novos dados.	<br>		
Por outro lado, se o modelo se ajusta demais sobre os dados de treinamento, significa que ele decorou os dados e ele será incapaz de prever com acerto quando tiver que prever sobre dados novos.<br>
- Overfitting
  - Quando o modelo se ajusta muito bem aos dados do treinamento(Overfitting), mas quando executado sobre os dados de teste, performa mal, ou seja, ele não aprendeu, ele decorou os dados do treinamento
  - Viés Baixo
  - Variância Alta
- Underfitting
  - Modelo que se ajusta mal aos dados do passado
  - Viés Alto
  - Variância Alta
      			
## Desafio
Para que um modelo seja bom, ele precisa passar por otimização que significa adição de complexidade
- O que é otimização/complexidade do modelo?
  - Quando fazemos ajustes para melhorar a acurácia do modelo, estamos adicionando complexidade 
    - Esses ajustes podem ser
      - Adição de neurônios ou camadas(Redes Neurais)
      - Adição de mais nós(Árvores de Decisão)
      - Adição de mais features
      - HyperParameters
Temos aqui um cobertor curto, pois conforme o viés é reduzido, temos o aumento da variância e vice-versa.<br>
O grande desafio aqui é calibrar ambos até o momento que se deve parar a otimização do modelo)
  - Quando se deve parar de otimizar o modelo?
    - Remédio x Veneno
      - Como dizem: A diferença entre o remédio e o veneno é a dose
      - O desafio é calibrar ambos até o momento em que "se deve parar de otimizar", ou seja, BUSCAR O MEIO TERMO entre viés e variância
      - Quando devemos parar de otimizar?
        - Gerar N modelos(cada modelo com seu respectivo ajuste/parametrização)
        - Executar de forma iterada cada modelo para prever sobre os dados de treinamento e de teste
        - Para cada iteração, calcular o RMSE e plotar em um gráfico de linhas a lista de resultado sobre os dados de treinamento e de teste
        - Conforme vamos otimizando o modelo o erro vai diminuindo tanto para sobre os dados de treinamento, quanto para os dados de teste
        - A partir do momento em que o modelo começa a errar para os dados de teste e continua acertar para os dados de treinamento, devemos parar! Nesse momento temos o início do overfitting.
	- Gráfico abaixo, vemos que conforme aumentamos a complexidade(ajustes, parametrização e etc...)
![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/tradeoff_bias_variance_graphic.jpg)
	- Conforme figura anterior, devemos usar o modelo parâmetrizado no momento ANTES de começar a errar sobre os dados de teste
        
 ## Técnicas
 
 ## Referências
https://www.dadosaleatorios.com.br/post/overfitting/<br>
https://lamfo-unb.github.io/2017/04/29/Um-Olhar-Descontraido-Sobre-o-Dilema-Vies-Variancia/<br>
https://datascience.eu/pt/matematica-e-estatistica/vies-vs-variancia/<br>
http://regisely.com/blog/bias-variance/<br>
