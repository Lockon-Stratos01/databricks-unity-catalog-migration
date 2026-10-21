# 🚀 Databricks Unity Catalog Migration & Governance

Este repositório contém uma solução completa de **Migração de Metadados do Hive Metastore para o Databricks Unity Catalog**, englobando governança de dados, mascaramento conforme a **LGPD** e rastreabilidade através de **linhagem e auditoria**.

---

## 📌 Arquitetura & Fluxo do Projeto

O projeto está estruturado em uma sequência modular de notebooks na pasta `notebooks/`:

1. **`01_migracao_hive_para_unity_catalog.ipynb`**
   - Mapeamento e inventário de tabelas legadas do Hive Metastore.
   - Automação de comandos DDL / SYNC para migração no Unity Catalog.
   - Organização da estrutura de 3 níveis (`catalog.schema.table`).

2. **`02_mascaramento_dados_lgpd.ipynb`**
   - Aplicação de **Column Masking** e **Row-Level Security (RLS)** em dados sensíveis (PII).
   - Conformidade com a Lei Geral de Proteção de Dados (LGPD).
   - Controle de acesso baseado em funções e grupos (RBAC).

3. **`03_linhagem_e_auditoria.ipynb`**
   - Rastreamento e visualização de **Data Lineage** nativo do Unity Catalog.
   - Análise de impacto de alterações entre camadas de dados (Bronze, Silver, Gold).
   - Consulta e monitoramento de logs de auditoria no `system.access.audit`.

---

## 📸 Evidências Visuais & Resultados

### 1. Mascaramento de Dados Sensíveis (LGPD)
Proteção de dados PII (ex: CPF mascarado) aplicada diretamente nas colunas do Unity Catalog.  
![Mascaramento LGPD](docs/lgpd-column-masking.png)

### 2. Linhagem de Dados - Origem / Legado
Rastreabilidade inicial mapeando a ingestão das tabelas legadas.  
![Data Lineage](docs/data-lineage.png)

### 3. Linhagem de Dados - Camada Silver
Visualização do fluxo e transformação estruturada dos dados na camada intermediária.  
![Linhagem Silver](docs/data-lineage-silver.png)

### 4. Linhagem de Dados - Camada Gold (Consolidação)
Análise de dependências e impacto na tabela final de resumo e crédito de clientes.  
![Linhagem Gold](docs/data-lineage-gold.png)

---

## 📁 Estrutura do Repositório

```text
.
├── docs/                 # Evidências visuais e documentação
│   ├── lgpd-column-masking.png
│   ├── data-lineage.png
│   ├── data-lineage-silver.png
│   └── data-lineage-gold.png
├── notebooks/            # Notebooks PySpark e SQL do Databricks
│   ├── 01_migracao_hive_para_unity_catalog.ipynb
│   ├── 02_mascaramento_dados_lgpd.ipynb
│   └── 03_linhagem_e_auditoria.ipynb
├── sql/                  # Scripts SQL complementares
├── terraform/            # Automação de infraestrutura como código (IaC)
└── README.md             # Documentação principal
