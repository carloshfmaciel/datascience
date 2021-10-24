# Como fazer deploy do Modelo em Produção?

Após o modelo estiver pronto para ir para Produção, uma das formas mais simples de usar o mesmo em produção é através de uma API.

Para tanto precisamos empacotar o mesmo, o que pode ser feito através da lib python "pickle" e através de um framework web python, como por exemplo o Flask,
podemos chamar o MODELO passando para o mesmo os dados recebidos na API.

Porém, devemos passar para o modelo, os dados que recebermos na API, no mesmo formato, com a mesma estrutura, com as mesmas transformações que foram realizadas sobre os dados de treinamento.

Ou seja, as mesmas transformações realizadas sobre os dados que foram usados no treinamento do modelo, devem ser realizadas sobre os dados sobre os quais ocorrerá a predição em Produção. Ex: Encoding, Normalization etc...

## Arquitetura do Modelo em Produção

![](https://github.com/carloshfmaciel/datascience/blob/master/conceitos/images/arquit_mod_prod.JPG)

- Step Request Modelo em Produção
  - API transforma os dados recebidos(JSON) em um dataframe
  - API chama classe ou método responsável pela transformação dos dados
    - Classe ou método obtém os recursos de transformação através do pickle
  - API chama classe ou método responsável pela chamada do modelo
    - Classe ou método obtém o modelo através do pickle
  - Modelo retorna a predição para a API
  - API retorna a predição para o requisitante
	
## Referências
https://www.youtube.com/watch?v=-s2B3Hsi1eM
