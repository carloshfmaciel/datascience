# Conceitos
- Tradeoff entre viés(bias) e variância(variance)

# Resumo Cursos Datascience

- [Estatística para Ciência de Dados e Machine Learning - Udemy](https://github.com/carloshfmaciel/datascience/blob/master/cursos/estatistica-para-ciencia-de-dados-e-machine-learning.md)
- [Séries Temporais com Python/Pandas/Statsmodels - Youtube](https://github.com/carloshfmaciel/datascience/blob/master/cursos/series-temporais-com-python-pandas-statsmodels.md)
- [Inteligência Artificial: Sistemas de Recomendação em Python - Udemy](https://github.com/carloshfmaciel/datascience/blob/master/cursos/inteligencia-artificial-sistemas-de-recomendacao-em-python.ipynb)

# Resumo Livros Datascience
- [Learn Amazon SageMaker](https://github.com/carloshfmaciel/datascience/tree/master/livros/learn_amazon_sageMaker)

# Meu Portfólio Análise de dados

[Sistema de recomendação utilizando SVD  - Livro Make Your Own Recommender System](Sistema_de_Recomendação_SVD_Livro_Machine_Learning_Make_Your_Own_Recommender_System.ipynb)

### Steps da Análise de Dados
- Introdução
- Contextualização do Problema
- Import dos dados
- Análise Exploratória dos dados
  - Dimensoes DataFrame
  - Dicionário dos dados
  - Visualização das primeiras entradas
  - Primeiras conclusões sobre os dados
  - Tipos de Variáveis
  - Descrição estatística do dataframe
  - Verificar quantidade de dados nulos por coluna
  - Verificar valores únicos por coluna
  - Verificar proporção do target do modelo(ideal é que seja 50/50 ou próximo disso), ou seja, se está balanceado(Gráfico de Barras)
  - Feature Engineering - Análisar quais outras propriedades RELEVANTES podem ser criadas a partir das existentes
- Preparação dos dados
  - Remover colunas que não são pertinentes para a analise
  - Substituir dados que devem ser substituidos por NaN(ex: inf de infinito)
  - Remover linhas onde o target for NaN
  - Preencher valores nulos com o valor mais frequente para a respectiva coluna(Categoricos) ou com np.Nan
  - Preencher valores nulos com a mediana da respectiva coluna(Numéricos) ou com np.Nan
  - Normalizar variáveis numéricas
  - Fazer Label Enconding das variáveis categóricas(isso otimiza o treinamento do modelo)
  - Aplicar o balanceamento no dataset
  - Feature Engineering - Adição de propriedades RELEVANTES a partir das já existentes
- Pré Processamento
  - Testar vários modelos 
    - Fazendo otimização de parâmetros
	- Fazendo validação cruzada com cálculo de RMSE(Root Mean Square Error) - Quanto menor o valor, melhor
 Construção do Modelo
- Executar o Modelo
- Calcular acurácia e acerto sobre os dados de teste(Matriz de Confusão)


## Como escolher um modelo de Machine Learning

Precisamos definir qual resposta queremos dar ao negócio, ou seja, se é uma Decisão, Estimativa ou Rankeamento.

- **Decisão** - Sim ou Não, 1 ou 0
<br>Ex: O paciente vai faltar ou não na consulta. O cliente vai pagar ou não o empréstimo

- **Estimativa** - Calcula uma probabilidade
<br>Ex: Quero enviar sms para os clientes que tem mais de 70% por cento de comprar o produto X. Aqui não existe a premissa de restrição/limite na quantidade de SMS que eu posso enviar. Então não importa se são 10 ou se são 1000 cliente que tem mais de 70% de probabilidade de comprar. Irei enviar para todos.

- **Rankeamento** - Ordenar do item que possui maior probabilidade para o item de menor probabilidade
<br>Ex: Quero enviar sms para os clientes que tem mais de 70% por cento de comprar o produto X. Porém o negócio tem restrição/limite na quantidade de SMS que eu posso enviar, devido ao budget. Então o negócio diz até quantos cliente posso enviar SMS. Por esta razão ordenamos e obtemos os primeiros até atingir a quantidade que o negócio pode enviar SMS. 
