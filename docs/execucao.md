# Execução do Pipeline

Nesta seção é descrito o processo de execução do pipeline do projeto **Medalhão**, composto pelas camadas *Landing*, *Bronze*, *Silver* e *Gold*.

---

##  Passo a passo de execução

### 1. Preparação do ambiente
Antes de rodar os notebooks, certifique-se de que o ambiente Databricks está configurado corretamente com:
- Cluster ativo e compatível com PySpark;
- Acesso ao **Unity Catalog** (caso esteja habilitado);
- Arquivos CSV disponíveis na *Landing Zone*.

### 2. Execução dos notebooks

O pipeline segue a sequência abaixo:

| Etapa | Notebook | Descrição |
|-------|-----------|-----------|
| 1️⃣ | `01_Landing_to_Bronze.ipynb` | Leitura dos arquivos CSV brutos da *Landing Zone*, padronização e escrita no formato Delta na camada Bronze. |
| 2️⃣ | `02_Bronze_to_Silver.ipynb` | Limpeza, enriquecimento e normalização dos dados. Geração das tabelas analíticas intermediárias na camada Silver. |
| 3️⃣ | `03_Silver_to_Gold.ipynb` | Agregação e transformação final dos dados para uso em relatórios, dashboards e insights de negócio. |

---

##  Parâmetros principais

- **CATALOG_NAME:** `workspace`
- **SCHEMA_NAME:** `projeto_medalhao`
- **LANDING_PATH:** Caminho de origem dos arquivos CSV.
- **BRONZE_PATH / SILVER_PATH / GOLD_PATH:** Caminhos das tabelas Delta geradas em cada camada.

---

##  Estrutura das camadas

```text
Landing Zone/
 ├── customers.csv
 ├── orders.csv
 ├── order_items.csv
 ├── products.csv
 └── reviews.csv

Bronze/
 ├── bronze_customers.delta
 ├── bronze_orders.delta
 ├── bronze_products.delta
 └── bronze_reviews.delta

Silver/
 ├── silver_orders_enriched.delta
 ├── silver_customers_enriched.delta
 └── silver_products_enriched.delta

Gold/
 ├── gold_sales_summary.delta
 └── gold_customer_rfm.delta
