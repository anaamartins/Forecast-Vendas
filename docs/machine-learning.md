# Machine Learning

## Objetivo

A componente de Machine Learning foi desenvolvida para complementar a análise histórica com uma estimativa do valor das vendas.

## Preparação dos dados

O processo de preparação incluiu:

- tratamento de valores em falta;
- análise de distribuições e correlações;
- seleção e transformação das variáveis;
- transformação logarítmica da variável-alvo.

## Treino e avaliação

Os dados foram divididos em conjuntos de treino e teste. Os modelos foram treinados, otimizados e avaliados no Azure Machine Learning.

Foi também utilizada validação cruzada durante o processo de avaliação.

## Resultado

O modelo obteve um coeficiente de determinação de aproximadamente **R² = 0,379**.

Este resultado representa um baseline inicial e não um modelo pronto para produção.

## Limitações

- período histórico limitado a 2022–2024;
- ausência de informação contratual completa;
- fatores comerciais não representados nos dados;
- comportamentos distintos entre mercados e segmentos.

## Próximos passos

- comparar o modelo com baselines temporais;
- adicionar métricas como MAE, RMSE e WAPE;
- incorporar dados contratuais e informação do pipeline comercial;
- criar previsões por mercado e linha de negócio;
- integrar os resultados no modelo semântico e no Power BI.
