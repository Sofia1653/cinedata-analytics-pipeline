# CineData Analytics | Pipeline de Dados End-to-End
 
Projeto da atividade de **Engenharia de Dados** do **Visagio Rocket Lab 2026**.
 
Pipeline de ETL sobre um catálogo de filmes, construído no **Databricks** com **PySpark** e **SQL**, seguindo a **Arquitetura Medalhão** (Bronze, Silver e Gold). O resultado alimenta duas frentes: Data Marts e modelagem dimensional para BI, e uma tabela de contexto para um assistente de IA baseado em LLM (RAG).
 
---
 
| Camada | Papel | Escrita |
|---|---|---|
| **Bronze** | Cópia fiel dos dados de origem, tudo como texto, com a coluna `ingestion_datetime` | Delta, `append` |
| **Silver** | Colunas em português, tipos corretos, limpeza, deduplicação e regras de negócio | Delta, `overwrite` |
| **Gold** | Modelagem dimensional (fato, dimensões, pontes), tabela de contexto para IA e respostas de negócio | Delta, `overwrite` |
 
## Estrutura do repositório
 
```
├── notebooks/
│   ├── Landing_to_Bronze.ipynb
│   ├── Bronze_to_Silver.ipynb
│   └── Silver_to_Gold.ipynb
├── job/
│   └── job.yaml
├── docs/
│   └── execucao_job.png
└── README.md
```
 
## Tecnologias
 
Databricks, PySpark, Spark SQL, Delta Lake, Databricks Workflows (Jobs) e a API PTAX do Banco Central.
 
---
 
## Como executar
 
1. Subir os 5 CSVs para um **Volume** do Databricks (`workspace.default.landing`).
2. Importar os 3 notebooks para o Workspace.
3. Executar em ordem: `Landing_to_Bronze` → `Bronze_to_Silver` → `Silver_to_Gold`, ou rodar o Job `cinedata_pipeline`, que faz isso automaticamente.
---
