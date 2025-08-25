# Desafio_Python
## Desafio proposto da Trilha de Engenharia de Dados.

Este projeto implementa um pipeline de ingestão e tratamento de dados usando PySpark e Databricks.
Ele consome dados de duas APIs públicas:

- **PokéAPI**
 – informações sobre Pokémons

- **SpaceX API**
 – lançamentos e foguetes da SpaceX

Os dados são processados em três camadas:

- **Bronze** → dados crus extraídos das APIs

- **Silver** → dados tratados, padronizados e deduplicados

- **Gold** → dados enriquecidos, prontos para consumo analítico

Além disso, é gerado um relatório de qualidade de dados que avalia:

Fonte dos dados **(FONTE_DADOS)**

Quantidade de linhas **(QTD_ROWS)**

Proporção média de valores nulos **(NULL_RATIO_MEDIA)**

.
── **notebooks/**

├── 01_bronze_ingestao.ipynb
│   
├── 02_silver_tratamento.ipynb
│   
├── 03_gold_enriquecimento.ipynb
│   
├── 04_data_quality_report.ipynb
│

├── **tables/**
│   
├── workspace.bronze.*
│   
├── workspace.silver.*
│   
├── workspace.gold.*
│   
├── workspace.quality.data_quality_report
│

├── **README.md**

## Tecnologias Usadas

- PySpark / Databricks
- Delta Lake
- APIs REST (PokéAPI & SpaceX)
- Python (requests, datetime, json)

## Fluxo do Pipeline

###  1- Ingestão (Bronze)

- Coleta os dados brutos das APIs

- Converte listas e dicionários em JSON string

- Armazena em tabelas Delta na camada bronze

### 2- Transformação (Silver)

- Seleção de colunas relevantes

- Deduplicação (última ingestão vence)

- Padronização de nomes de colunas

- Tratamento de nulos

### 3- Enriquecimento (Gold)

- Junção entre lançamentos da SpaceX e dados de foguetes

- Preparação de dados de Pokémons com atributos chave

- Tabelas prontas para dashboards

# Qualidade de Dados (Quality Layer)

- Cálculo de número de linhas

- Percentual médio de valores nulos
 
- Checks de ranges definidos por coluna
 
- Geração de relatório consolidado

# Como Executar no Databricks

####1- Clone o repositório no Databricks Repo

####2- Configure o cluster com:

- Runtime: 7.3+ com Delta Lake

- Linguagem: Python 3

#### 3- Execute os notebooks na ordem:

- **01_bronze_ingestao

- 02_silver_tratamento

- 03_gold_enriquecimento

- 04_data_quality_report**

# Visualize os resultados:
SELECT * FROM workspace.gold.spacex_launches;
SELECT * FROM workspace.quality.data_quality_report;
