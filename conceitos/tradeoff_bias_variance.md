## Viés(Bias) x Variância(Variance)
- O que são?
  - Viés e Variância são dois erros de previsão que ocorrem principalmente durante o processo de aprendizagem de máquina

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
  - É a diferença que ocorre entre a quantidade de erros/acertos sobre os dados de treinamento, versus o montante de erros/acertos sobre os dados de teste
  - Quando falamos de variância
  - Tipos de Variância
    - Alta Variância/High Variance
      - Quando o modelo erra muito sobre os dados de teste
    - Baixa Variância/Low Variance
      - Quando o modelo erra pouco sobre os dados de teste			

## O que faz o modelo ter viés alto(errar muito sobre os dados de treinamento) e/ou variância alta?
  - Seleção de um modelo não apropriado
  - Baixa qualidade dos dados(inclusão de dados que são inúteis para a previsão - ruído)
  - Adição de complexidade
			
# Overfitting e Underfitting
Dependendo da qualidade dos dados de treinamento e dos ajustes que realizamos no modelo, o modelo pode se ajustar demais ou menos do que deveria.<br>
Quando o modelo não se ajusta, ou seja, não consegue capturar os padrões dos dados de treinamento, ele também é incapaz de prever com acerto sobre novos dados.	<br>		
Quando o modelo se ajusta de mais sobre os dados significa que ele decorou os dados e o mesmo será incapaz de prever com acerto sobre novos dados.<br>
- Overfitting
  - Quando o modelo se ajusta muito bem aos dados do treinamento(Overfitting), mas não sobre os dados de teste, ou seja, ele não aprende, ele decora
  - Viés Baixo
  - Variância Alta
- Underfitting
  - Modelo que se ajusta mal aos dados do passado
  - Viés Alto
  - Variância Alta
      			
# Desafio
  - Para que um modelo seja bom, ele precisa passar por otimização que significa adição de complexidade
    - O que é otimização/complexidade do modelo?
      - Quando fazemos ajustes para melhorar a acurácia do modelo, estamos adicionando complexidade 
      - Esses ajustes podem ser
        - Adição de neurônios ou camadas(Redes Neurais)
        - Adição de mais nós(Árvores de Decisão)
        - Adição de mais features
        - HyperParameters
  - Temos aqui um cobertor curto, pois conforme o viés é reduzido, temos o aumento da variância e vice-versa
  - O desafio aqui é calibrar ambos até o momento que se deve parar a otimização do modelo)
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
        - Gráfico abaixo
        - Conforme figura anterior, devemos usar o modelo parametrizado no momento ANTES do modelo começar a errar para os dados de teste 
        
 ## Técnicas   
