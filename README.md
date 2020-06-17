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
- Preparação dos dados
  - Remover colunas que não são pertinentes para a analise
  - Substituir dados que devem ser substituidos por NaN(ex: inf de infinito)
  - Remover linhas onde o target for NaN
  - Preencher valores nulos com o valor mais frequente para a respectiva coluna(Categoricos)
  - Preencher valores nulos com a mediana da respectiva coluna(Numéricos)
  - Normalizar variáveis numéricas
  - Fazer Label Enconding das variáveis categóricas(isso otimiza o treinamento do modelo)
  - Aplicar o balanceamento no dataset
 Construção do Modelo
- Executar o Modelo
- Calcular acurácia e acerto sobre os dados de teste(Matriz de Confusão)
