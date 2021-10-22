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

### Força da Correlação

De acordo com o resultado do coeficiente de correlação, temos:

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/tab_coef_corr.jpg)

Para termos um bom resultado o ideal é que a correlação seja moderada ou forte.

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

### Calculando o Coeficiente de Correlação em Python

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

```python
# calculando o coeficiente de correlação entre tamanho e preço
np.corrcoef(tamanho, preco)
```
```
# Perceba que a correlação entre tamanho e preço é de 0.99
array([[1.        , 0.99620063],
       [0.99620063, 1.        ]])
```

## Coeficiente de Determinação / R²
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


## Analisando o coeficiente de correlação de forma gráfica

Podemos utilizar algumas formas gráficas/visuais para analisar a força da correlação(coeficiente de correlação) entre todas as propriedades de um dataset.

Abaixo temos um dataset de imóveis, onde temos as propriedades do imóvel e o seu preço.

```python
dataset.head()
```

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/dataset_houses.jpg)

### Mapa de Calor

```python
import matplotlib.pyplot as plt
fig, ax = plt.subplots(figsize=(15,15))
ax = sns.heatmap(dataset.corr(), annot=True)
```
Perceba que as propriedades que possuem maior correlação com preço são: bathrooms(0.53), sqft_living(0.7), grade(0.67), sqft_above(0.61) e sqft_living15(0.59).

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/heatmap_houses.png)

### Gráfico de Barras

```python
!pip install yellowbrick --upgrade
from yellowbrick.target import FeatureCorrelation
columns = dataset.columns[1:]
grafico = FeatureCorrelation(labels = columns)
grafico.fit(dataset.iloc[:, 1:16].values, dataset.iloc[:, 0].values)
grafico.show();
```

Aqui podemos ver a força da correlação(coeficiente de correlação) através de barras.
<br>Perceba que as propriedades que possuem maior correlação com preço são: bathrooms(0.53), sqft_living(0.7), grade(0.67), sqft_above(0.61) e sqft_living15(0.59).

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/bargraph_houses.png)

## Observação
- Correlação nem sempre significa causa
- Printar gráfico de coisas que possuem correlação, mas que são casualidades, como o caso dos filmes do Nicolas Cage
