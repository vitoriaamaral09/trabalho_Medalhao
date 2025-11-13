
---

##  **docs/resultados.md**

```markdown
# Resultados

Após a execução completa do pipeline, o projeto gera dados organizados e prontos para análise nas camadas *Bronze*, *Silver* e *Gold*.

---

## 🔍 Camada Bronze
Contém os dados brutos padronizados, convertidos para formato Delta e com metadados de origem e timestamp de ingestão.

**Exemplo de schema:**
```text
bronze_customers
├── customer_id
├── name
├── email
├── source_file
└── ingestion_timestamp
