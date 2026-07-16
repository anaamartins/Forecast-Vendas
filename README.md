# Forecast-Vendas
Projeto de Forecast de Vendas, integrando processos ETL, Data Warehouse, modelo tabular em SSAS, Power BI e modelos preditivos de Machine Learning. A análise exploratória dos dados foi realizada em Python.

### Visão Geral
Este projeto foi desenvolvido com o objetivo de apoiar o processo de Forecast de Vendas.

O projeto contempla a exportação, transformação e carregamento dos dados (ETL), a construção de um Data Warehouse, o desenvolvimento de um modelo tabular em SSAS, a criação de modelos preditivos de Machine Learning e a disponibilização da informação através de report, dashboard e aplicação em Power BI.

<p align="center">
  <img src="docs/images/powerbi-executive-summary.png" alt="Power BI — Sumário Executivo" width="95%">
</p>


## Problema de negócio

O processo de análise e previsão de vendas dependia da consolidação manual de dados provenientes de diferentes fontes.

Esta abordagem aumentava:

- o tempo necessário para preparar a informação;
- o risco de erros e inconsistências;
- a dificuldade em atualizar as análises regularmente;
- a dependência de tarefas manuais;
- a dificuldade em incorporar indicadores externos no processo de forecast.

O projeto foi desenvolvido para automatizar este processo, criar uma fonte única de informação e apoiar o planeamento comercial e a tomada de decisão.



## Projeto

O projeto integra diferentes componentes numa única plataforma analítica:

- pipelines ETL desenvolvidos no Azure Data Factory;
- Data Lake organizado nas camadas `Source`, `RAW` e `Processed`;
- Data Warehouse com modelo dimensional;
- modelo semântico tabular em SQL Server Analysis Services;
- report, dashboard, aplicação e versão mobile em Power BI;
- análise exploratória dos dados em Python;
- desenvolvimento, treino, otimização e avaliação dos modelos no Azure Machine Learning;



## Principais resultados

A análise dos dados entre 2022 e 2024 permitiu identificar:

- vendas anuais entre aproximadamente **40 M€ e 42,6 M€**;
- crescimento das vendas de aproximadamente **6,6% em 2024**;
- margens brutas estáveis entre **66% e 68%**;
- elevada concentração das vendas no mercado angolano;
- dependência de um número reduzido de clientes e mercados;
- maior volume de vendas no mês de abril, associado à renovação de contratos de manutenção;
- indícios de associação entre as vendas em Angola, o preço do petróleo e a taxa de câmbio.

A componente preditiva obteve um coeficiente de determinação aproximado de **R² = 0,379**.

Este resultado é apresentado como um **baseline inicial**, não como um modelo pronto para produção.



## Arquitetura

<p align="center">
  <img src="docs/images/architecture.png" alt="Arquitetura da solução" width="100%">
</p>

O Pipeline Master do Azure Data Factory coordena a ingestão, transformação e carregamento dos dados.

Os ficheiros são armazenados no Azure Data Lake Storage, processados por camadas e carregados no Data Warehouse SQL, criadas e geridas através do Azure Data Studio..

O modelo tabular em SQL Server Analysis Services consome os dados do Data Warehouse e é utilizado pelo Power BI através de uma ligação live.

A componente de Machine Learning utiliza um dataset preparado no Azure Data Factory e posteriormente processado em Python e Azure Machine Learning.

### Fluxo simplificado

```text
ERP SAP + Base de Dados + Indicadores Macroeconómicos
                         ↓
                Azure Data Factory
                         ↓
              Azure Data Lake Storage
              Source → RAW → Processed
                         ↓
              ┌──────────┴───────────┐
              ↓                      ↓
     SQL Data Warehouse       Dataset de Machine Learning
              ↓               preparado no Azure Data Factory
         SSAS Tabular                 ↓
              ↓                Python — Análise Exploratória
          Power BI                    ↓
                              Azure Machine Learning
                         Treino · Otimização · Avaliação
```



## Power BI

O report permite analisar o desempenho comercial e financeiro entre 2022 e 2024.

As principais áreas de análise são:

- sumário executivo;
- clientes;
- mercados e países;
- empresas e linhas de negócio;
- vendas, custos e margens;
- concentração de receita;
- contexto macroeconómico;
- evolução mensal e anual;
- forecast e avaliação das previsões.

### Sumário executivo

<p align="center">
  <img src="docs/images/powerbi-executive-summary.png" alt="Power BI — Sumário Executivo" width="95%">
</p>

### Análise de vendas

<p align="center">
  <img src="docs/images/powerbi-sales-analysis.png" alt="Power BI — Análise de Vendas" width="95%">
</p>

### Contexto macroeconómico

<p align="center">
  <img src="docs/images/powerbi-macro-context.png" alt="Power BI — Contexto Macroeconómico" width="95%">
</p>



## Machine Learning

A componente de Machine Learning foi desenvolvida para complementar a análise histórica com uma estimativa do valor das vendas.

O processo incluiu:

- análise exploratória dos dados;
- tratamento de valores em falta;
- análise de distribuições e correlações;
- seleção e transformação das variáveis;
- transformação logarítmica da variável-alvo;
- divisão dos dados em treino e teste;
- treino e otimização dos modelos;
- validação cruzada;
- avaliação das previsões.

### Principais limitações do modelo

- período histórico limitado a 2022–2024;
- ausência de informação completa sobre contratos anteriores a 2022;
- reduzida capacidade explicativa de algumas variáveis;
- existência de fatores comerciais não representados nos dados;
- comportamento distinto entre mercados e segmentos.



## Recomendações para o negócio

Com base nos resultados, foram identificadas as seguintes recomendações:

- monitorizar a concentração de vendas por cliente e mercado;
- simular o impacto de uma redução das vendas no mercado angolano;
- incorporar informação contratual e dados do pipeline comercial;
- desenvolver previsões separadas para mercados com comportamentos distintos;
- acompanhar o efeito da taxa de câmbio e do preço do petróleo;
- integrar as previsões e os respetivos erros no Power BI.



## Próximos passos

As prioridades para evolução do projeto são:

- comparar o modelo com baselines temporais;
- adicionar métricas como MAE, RMSE e WAPE;
- incorporar dados contratuais e pipeline comercial;
- criar previsões por mercado e linha de negócio;
- integrar os resultados preditivos no modelo semântico.



## Ferramentas

| Área | Tecnologia |
|---|---|
| Integração e orquestração | Azure Data Factory |
| Armazenamento | Azure Data Lake Storage |
| Transformação | Azure Data Factory Data Flows |
| Data Warehouse | SQL Server / Azure SQL Database |
| Desenvolvimento e consultas SQL | Azure Data Studio |
| Modelo semântico | SQL Server Analysis Services |
| Business Intelligence | Power BI |
| Machine Learning | Python e Azure Machine Learning |



## Contributo

O projeto incluiu:

- definição do problema de negócio e das necessidades de análise;
- análise das fontes de dados disponíveis;
- identificação dos processos de negócio abrangidos pelo projeto;
- definição do granularidade das tabelas dimensão e facto;
- desenho da arquitetura do projeto;
- desenho do modelo dimensional, incluindo tabelas facto, dimensão, medidas e relações;
- criação das tabelas de dimensões e factos no Data Warehouse SQL;
- desenvolvimento dos pipelines e Data Flows no Azure Data Factory;
- implementação dos processos de carregamento e atualização das tabelas;
- desenvolvimento do modelo tabular em SQL Server Analysis Services;
- criação de medidas, hierarquias, roles e partições;
- desenvolvimento do report, dashboard, aplicação e versão mobile em Power BI;
- análise exploratória dos dados em Python;
- desenvolvimento, treino, otimização e avaliação dos modelos no Azure Machine Learning;
- interpretação dos resultados e elaboração de recomendações.



<details>
<summary><strong>Detalhes do processo ETL</strong></summary>

<br>

O processo ETL é coordenado por um Pipeline Master no Azure Data Factory.

As principais etapas são:

1. carregamento dos ficheiros originais na camada `Source`;
2. conversão dos ficheiros para Parquet;
3. armazenamento dos dados na camada `RAW`;
4. transformação das tabelas dimensão e facto;
5. armazenamento dos dados tratados na camada `Processed`;
6. carregamento no Data Warehouse SQL;
7. atualização automática da `DimCalendario`;
8. preparação do dataset utilizado em Machine Learning.

</details>

<details>
<summary><strong>Detalhes do modelo dimensional</strong></summary>

<br>

O Data Warehouse utiliza um modelo dimensional composto pelas seguintes tabelas.

### Dimensões

- `DimCliente`
- `DimEmpresa`
- `DimPais`
- `DimProduto`
- `DimProjeto`
- `DimTipoVenda`
- `DimCalendario`

### Tabelas de factos

- `FactVendas`
- `FactMacros`

Foram utilizadas surrogate keys nas dimensões sem identificadores numéricos adequados.

O carregamento das dimensões utiliza operações de `upsert`, preservando as chaves e a integridade das relações com as tabelas de factos.

<p align="center">
  <img src="docs/images/dimensional-model.png" alt="Modelo dimensional" width="95%">
</p>

</details>

<details>
<summary><strong>Detalhes do modelo semântico</strong></summary>

<br>

O modelo tabular em SQL Server Analysis Services centraliza:

- relações entre tabelas dimensão e facto;
- medidas de vendas, custos e margens;
- indicadores macroeconómicos;
- hierarquias temporais e de produtos;
- perspetivas de análise;
- partições anuais;
- roles e regras de segurança;
- traduções para inglês.

O Power BI utiliza uma ligação live ao modelo tabular.

</details>

<details>
<summary><strong>Fontes de dados</strong></summary>

<br>

O projeto integra dados relativos ao período de 2022 a 2024.

As fontes utilizadas incluem:

- ERP SAP;
- base de dados interna;
- taxas de câmbio;
- inflação;
- desemprego;
- Produto Interno Bruto;
- preço do petróleo.

</details>



## Documentação

- [Processo ETL](docs/processo_etl.md)
- [Modelo dimensional](docs/modelo_dimensional.md)
- [Machine Learning](docs/machine_learning.md)


