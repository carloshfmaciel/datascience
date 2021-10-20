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

Abaixo temos a definição de quando existe correlação. Ou seja, comparamos o resultado da covariância ou do coeficiente de correlação no critério abaixo:
- Quando o resultado do coeficiente de correlação for > 0 temos uma correlação positiva(conforme X aumenta o y também aumenta)
- Quando o resultado do coeficiente de correlação for < 0 temos uma correlação negativa(conforme X aumenta o y diminui)
- Quando o resultado do coeficiente de correlação for = 0, as variáveis são independentes, não possuem correlação, uma variável não está relacionada com a outra

## Covariância
Mede utilizando a própria escala das variáveis a correlação entre as variáveis, ou seja, quanto uma variável influencia a outra
- Ponto negativo é que trabalha com as variáveis em escalas diferentes, dificultando a análise
- Seu cálculo é a base para o cálculo do coeficiente de correlação

No exemplo abaixo, temos uma amostra de 4 registros que representam 4 imóveis, onde temos o tamanho em metro quadrado e o preço.

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/tabela_covariancia.jpg)

Abaixo temos a fórmula do cálculo da covariância

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/calc_form_variancia.jpg)

E abaixo temos a fórmula com os respectivos valores

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/calc_form_variancia_com_valores.jpg)

Temos portanto uma variância de 178.500 que é maior que 0. Portanto temos uma correlação positiva(conforme X aumenta, y também aumenta). 

Porém será que essa correlação é forte ou fraca? Perceba que não temos idéia dos limites dessa correlação, portanto fica difícil mensurar a força da mesma.

Visando facilitar essa interpretação, temos a seguir o cálculo do coeficiente de correlação, que utilizando o resultado da covariância calcula a força da correlação.

### Calculando Covariância em Python

```python
# importações
import numpy as np
import pandas as pd
import seaborn as sns
import math

# montando base de dados
tamanho = np.array([30, 39, 49, 60])
preco = np.array([57000, 69000, 77000, 90000])

dataset = pd.DataFrame({'tamanho': tamanho, 'preco': preco})
dataset
```

||**tamanho**	|**preco**|
|-|---------|-----|
|0|	30	   |57000|
|1|	39	   |69000|
|2|	49	   |77000|
|3|	60	   |90000|

## Coeficiente de Correlação
- A faixa de valores do resultado é sempre entre -1 e 1
  - Quando > 0 temos uma correlação positiva(conforme X aumenta, y também aumenta)
  - Quando < 0 temos correlação negativa(conforme X aumenta, y diminui)
  - Quando = 0, as variáveis são independentes, uma variável não está relacionada com outra

Abaixo temos a fórmula do cálculo do coeficiente de correlação

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/calc_form_coef_corr.jpg)

E abaixo temos a fórmula com os respectivos valores

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/calc_form_coef_corr_com_valores.jpg)

Temos portanto o valor de 0,99 que está bem próximo de 1. Ou seja, temos aqui uma correlação forte que significa que conforme X(o tamanho do imóvel) aumenta, o valor de y(preço do imóvel) também aumenta.
			
- Quanto mais próximo de 1 ou -1, mais forte é a correlação entre as variáveis
  - Printar exemplos e códigos (Link: https://www.udemy.com/course/estatistica-para-ciencia-de-dados-machine-learning/learn/lecture/22533844#overview)
    - Mostrar em python o calculo de alguma que possua forte correlação positiva
    - Mostrar em python o calculo de alguma que possua forte correlação negativa
    - Mostrar em python o calculo de não possua correlação positiva
    - Exibir gráfico de correlação usando o YellowBrik
- Printar tabela de correlação e interpretação

## Coeficiente de Determinação
- Conhecido também como R2 ou R Score
- Ele é um número entre 0 e 1
- É a proporção do erro do modelo de regressão em relação ao erro do modelo de média	
- O resultado é o percentual que a variável dependente(y) consegue ser explicada pela(s) variáveil(eis) independente(s), ou seja, x
- Ele diz quanto por cento o modelo de regressão é melhor do que o modelo mais simples(modelo de média)
- Quanto maior o valor, melhor é o modelo de regressão em relação ao modelo de média

Abaixo temos a fórmula do cálculo do coeficiente de determinação

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/calc_form_coef_det.jpg)

Onde:
- R² = Coeficiente de Determinação
- RSS = Erro entre os modelos(Soma dos residuais quadrados)
- TSS = Erro do modelo de média(Soma Total dos quadrados) 

Também podemos calcular a partir do resultado do coeficiente de correlação, onde a fómula e valores ficariam conforme abaixo:

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/calc_form_coef_det_com_valores.jpg)

Conforme resultado acima, interpretamos que 98% da variável dependente(y, ou seja, no caso o preço) é explicada pela variável independente(X, no caso o tamanho do imóvel).	

## Observação
- Correlação nem sempre significa causa
- Printar gráfico de coisas que possuem correlação, mas que são casualidades, como o caso dos filmes do Nicolas Cage
