# TripleTen-3-Projeto_Carros


## O que vende um carro?

A atividade trata-se de uma análise de uma dataframe com as informações de propagandas de carros. O dataframe representaria um site, chamado Lista de Eixo de Manivela. Centenas de propagandas gratuitas de veículos são publicadas no site todos os dias. Estudarei os dados coletados nos últimos anos e determinarei quais fatores influenciaram o preço de um veículo.

Em primeiro lugar, será feito o pré-processamento dos dados. O dataframe será analisado, procurando-se por valores ausentes, duplicados ou com formatação incorreta, e serão tratados. Encontrado valores ausentes, será investigado se existe alguma razão, então decidirei se serão substituídos. Em seguida, investigariei a necessidade de modelagem e criação de novas colunas do dataframe, para melhorar a análise.

Sendo assim, a análise do dataframe será feita estudando os parâmetros como preço, idade do veículo, quando a propaganda foi colocada, etc. Para cada parâmetro será construido histogramas e outros gráficos, investigando a distribuição dos parâmetros e a existencia de valores atípicos.

Em seguida, será estudado quantos dias as propagandas foram exibidas. Descrevendo o tempo de vida útil comum de uma propaganda. Determinarei quando as propagandas foram removidas rapidamente, e quando elas foram listadas por um tempo anormalmente longo. Analisarei o número de propagandas e o preço médio para cada tipo de veículo. Para demonstrar a relação, construirei um gráfico mostrando a dependência do número de propagandas em relação ao tipo de veículo.

Por fim, será visto quais fatores mais influenciam o preço. Serão pegos os tipos populares detectados e será visto se os seus preços dependem da idade, quilometragem, condição, tipo de transmissão, etc. As categorias de variáveis categóricas analisadas precisam ter pelo menos 50 propagandas, de outro modo, seus parâmetros não serão válidos para análise.


## Conclusão geral

Pré-Processamento dos Dados

A primeira fase da análise consistiu em fazer uma primeira visualização dos dados para procurar problemas. Foram encontrados valores ausentes, colunas com tipos de dados incorretos e duplicatas implícitas. Os valores ausentes foram os primeiros a serem tratados.

As colunas model_year, cylinders, odometer, paint_color e is_4wd possuíam valores ausentes. Cada uma delas foi tratada de uma forma diferente:

is_4wd: é uma variável booleana, sendo 1 representando sim e 0 representando não. Os valores 0 estavam como nan. Foram substituídos os nan por 0.

paint_color: foi substituído usando a moda da cor do carro em relação ao modelo. Foi feito desta forma, pois intuitivamente, a cor do carro deve possuir relação com o modelo. Não foi encontrada uma causa para a existência dos valores ausentes.

cylinders: foi substituído usando a moda em relação ao modelo. Existe relação entre a quantidade de cilindros e o modelo de carro. Não foi encontrada uma causa para a existência dos valores ausentes.

odometer: foi substituído usando a mediana em relação à condição do carro. Não foi encontrada uma causa para a existência dos valores ausentes.

model_year: foi substituído usando a mediana em relação ao modelo. Não foi encontrada uma causa para a existência dos valores ausentes.

Depois de resolvidos os valores ausentes, foram tratadas as duplicatas implícitas da coluna model. A correção do tipo de dados foi feita para as colunas is_4wd, model_year e cylinders, que foram transformadas em int64, e para a coluna date_posted, que foi transformada em datetime.

Foram adicionadas quatro colunas para enriquecer a análise. Foi adicionada uma coluna para o dia em que a propaganda foi postada, uma para a idade do veículo, uma para a quilometragem por ano e uma para representar a coluna de condição por meio de números.

Análise de Dados

Os primeiros parâmetros estudados para entender o que afeta o preço foram a idade do veículo, quilometragem, número de cilindros, condição do veículo e o próprio preço. Os valores atípicos afetaram a visualização, foi criado um novo dataframe sem os valores atípicos.

Análises Univariadas:

O preço varia em até 35.000 dólares, com a maioria dos dados entre 5.000 e 15.000 dólares.
A quilometragem começa entre 0 e 250.000. Carros com 0 quilômetros têm idade igual a zero.
A idade está entre 0 e 23 anos, a maioria entre 5 e 10 anos.
Os cilindros mais comuns são de 8, 6 e 4.
As condições mais comuns são "excelente" e "bom".

Análises Multivariadas:

Os tipos mais comuns de carro são "SUV", "truck" e "sedan". "SUV" tem um preço mediano de 8980 dolares, "truck" de 14995 dolares e "sedan" de 5999 dolares.

Os gráficos demonstram que a partir de 10 anos os preços tendem a diminuir, com apartir 20 anos não a preços acima de 15000. A partir de 150000 quilometros o preço médio tende a cair, em 250000 quilometros o preço não está acima de 10000 dolares. Carros em baixa condição tendem a não serem vendidos por um alto preço dolares, mas apartir da condição boa, se torna irrelevante. Em relação a quantidade de cilindros , os de "3" "12" não possuem um número suficiente para a analise. A quantidade de cilindros parece não afetar o preço. O tipo de transmissão possue um preço mediano parecido entre transmissão manual e automatica, mas o tipo "other" tende a possuir uma mediana maior mas com alta variancia. A cor do para possui uma mediana parecida entre as corre, não demonstra afetar o preço. Concluo que, a partir da minha análise, a idade e quilometragem do carro são as variáveis que mais afetam o preço
