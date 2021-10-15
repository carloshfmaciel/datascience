## Correlação

Mede o quanto uma variável influencia a outra, ou seja, se correlaciona.

## Regressão
Previsão de valores futuros
	
### Como saber se posso aplicar regressão(linear ou múltipla) para estimar valores de um determinado cenário?
- Verificar se existe forte correlação entre a(s) variável(is) X e y
  - Como calcular a correlação?
    - Através do coeficiente de correlação
    - Podemos também exibindo um gráfico de linhas
      - Caso tenhamos uma linha reta na diagonal(ascendente ou descendente) e boa parte dos dados estiverem concentrados nela			

 ## Covariância
	  - Mede utilizando a própria escala das variáveis a correlação entre as variáveis, ou seja, quanto uma variável influencia a outra
		- Ponto negativo é que trabalha com as variáveis em escalas diferentes, dificultando a análise
		- Seu cálculo é a base para o cálculo do coeficiente de correlação
    - Printar o calculo e a tabela com o calculo(Link https://www.udemy.com/course/estatistica-para-ciencia-de-dados-machine-learning/learn/lecture/22533840#overview)
    - Resumo
      - Quando > 0 temos uma correção positiva(conforme uma var aumenta a outra também aumenta)
      - Quando < 0 temos correlação negativa(conforme uma var aumenta a outra diminui)
      - Quando = 0, as variáveis são independentes, uma variável não está relacionada com outra

## Coeficiente de Correlação
    - A faixa de valores do resultado é sempre entre -1 e 1
      - Quando > 0 temos uma correção positiva(conforme uma var aumenta a outra também aumenta)
      - Quando < 0 temos correlação negativa(conforme uma var aumenta a outra diminui)
      - Quando = 0, as variáveis são independentes, uma variável não está relacionada com outra
    - Printar o cálculo(Link https://www.udemy.com/course/estatistica-para-ciencia-de-dados-machine-learning/learn/lecture/22533840#overview)			
    - Quanto mais próximo de 1 ou -1, mais forte é a correlação entre as variáveis
		- Printar exemplos e códigos (Link: https://www.udemy.com/course/estatistica-para-ciencia-de-dados-machine-learning/learn/lecture/22533844#overview)
			- Mostrar em python o calculo de alguma que possua forte correlação positiva
			- Mostrar em python o calculo de alguma que possua forte correlação negativa
			- Mostrar em python o calculo de não possua correlação positiva
			- Exibir gráfico de correlação usando o YellowBrik
		- Printa tabela de correlação e interpretação
## Coeficiente de Determinação
	  - Conhecido também como R2 ou R Score
		- Ele é um número entre 0 e 1
		- É a proporção do erro do modelo de regressão em relação ao erro do modelo de média	
	  - O resultado é o percentual que a variável dependente(y) consegue ser explicada pela(s) variáveil(eis) independente(s), ou seja, x
		- Ele diz quanto por cento o modelo de regressão é melhor do que o modelo mais simples(modelo de média)
		- Quanto maior o valor, melhor é o modelo de regressão em relação ao modelo de média
		- Fórmula
		  - (1-(Soma dos erros do modelo de regressão SOBRE Soma dos erros do modelo de média))
			- Link(https://www.youtube.com/watch?v=xeGBoa--xzY)
    - Printar o cálculo(Link https://www.udemy.com/course/estatistica-para-ciencia-de-dados-machine-learning/learn/lecture/22533840#overview)	
  - Observação
	  - Correlação nem sempre significa causa
		- Printar gráfico de coisas que possuem correlação, mas que são casualidades, como o caso dos filmes do Nicolas Cage
