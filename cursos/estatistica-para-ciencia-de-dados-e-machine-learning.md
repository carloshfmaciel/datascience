# Resumo Curso Estatística para Ciência de Dados e Machine Learning - Udemy

[Link Curso](https://www.udemy.com/course/estatistica-para-ciencia-de-dados-machine-learning)

- Entender o contexto do problema e o que representam os dados
- Extração dos dados
- Limpeza dos dados
- Mesclar os dados
- Gerar novas informações(feature engineering)
- Interagir e visualizar
- Criar modelos de machine learning

1. Entendimento da base
2. Verificando se os datasets possuem valores nulos(Analisar se deverão ser excluidos ou preenchidos com média por exemplo)
3. Verificar se todos os registros do dataset possuem relação entre eles
4. Verificar outliers através do boxplot(analisar o que fazer com eles(excluir ou substituir))
    - Pesquisar técnicas de tratar outliers
5. Buscar por dados duplicados
6. Excluir colunas desnecessárias para a analise(id por exemplo nao faz diferença no machine learning)
7. Normalizar os dados(manter valores na mesma escala decimal)

Feature Engineering
- Baseado em novas perguntas de negócio, criamos novas colunas com um dado que permite responder essas perguntas diretamente

Gráficos
- Barras - Usado para categoria ou tempo contra dado numérico. Bom para mostrar comportamentos de anomalias. Eixo Horizontal temos um dado categórico e no eixo vertical um dado numérico.
- Linhas - Usado para tempo contra dado numérico ou análise de 2 dados numéricos. Bom para mostrar tendência e ruídos. Dados numéricos nos dois eixos.
- Dispersão - Normalmente usado para análise de 2 dados numéricos(ou tempo em um eixo). Bom para mostrar correlação entre os dados.
- Pizza - Usado para comparar porcentagen/proporção entre categorias. Somente usar com porcentagem.
- Boxplot - Usado para categoria contra dado numérico. Mostra a variação dos dados e outliers. Bom para buscar outliers e avaliar se uma variável impacta no comportamento da outra. Ele exibe quartis e mediana.
- Histograma e Curva de Distribuição Normal - Normalmente usado para análise de 2 dados numéricos. Eixo vertical temos a frequência, ou seja, o quanto uma coisa está ocorrendo e no eixo horizontal teremos um categoria, uma linha do tempo ou até mesmo um dado numérico.
- Bolhas - Similar ao gráfico de dispersão, exibe uma terceira dimensão que seria um volume de um determinado ponto. Eixo vertical, horizontal e o tamanho da bolha(volume).
- Pareto - Usado para exibir categorias mais representativas do dataset. Exibe colunas de frequência em ordem decrescente e uma linha que mostrará o percetual acumulado dessas categorias.
- Dendograma - Mostra a frequência em que eventos ocorrem em diversas categorias.
- Diagrama de Sankey - Mostra o relacionamento entre duas variáveis.
- Mapa de calor - Mostra o comportamento de uma variável, comparada as outras. Seria como o mapa de bolhas, mas ao invés de dar um tamanho, dariamos uma cor distinta para aquela bolha. Mostrar o impacto visual onde está o problema.

Machine Learning

- Quando trabalhamos com ML precisamos definir um alvo
  - Alvo é a propriedade do dataset que contém o valor esperado para o conjunto de dados no registro
- Após a definição do alvo, normalizar os dados
  - Fazer com que os dados estejam dentro da mesma grandeza ou dimensão
  - Uma técnica de normalização é converter o valor entre 0 e 1
- Converter dados categóricos
- Regressão 
  - Linear: Quando se quer prever um número baseado em outro número
  - Logística: Quando se quer prever um valor booleano/binário, ou seja, SIM e NÃO, 0 e 1
