# Processo ETL

## Objetivo

O processo ETL foi desenvolvido para extrair, transformar e carregar os dados utilizados na análise e previsão de vendas.

## Fontes de dados

- ERP SAP;
- bases de dados internas;
- indicadores macroeconómicos.

## Orquestração

O Pipeline Master do Azure Data Factory coordena a execução dos diferentes processos de ingestão, transformação e carregamento.

## Camadas do Data Lake

### Source

Área de receção dos dados provenientes das diferentes fontes.

### RAW

Área destinada ao armazenamento dos dados no seu formato original.

### Processed

Área onde são disponibilizados os dados após os processos de limpeza e transformação.

## Transformações

As transformações foram desenvolvidas através de pipelines e Data Flows no Azure Data Factory.

## Carregamento

Após o processamento, os dados são carregados nas tabelas de factos e dimensões do Data Warehouse.
