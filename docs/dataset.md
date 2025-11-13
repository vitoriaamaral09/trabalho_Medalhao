#  Dataset

O projeto utiliza um conjunto de dados simulado que representa informações de **e-commerce** — clientes, pedidos, produtos e avaliações.

---

##  Estrutura dos Arquivos

| Arquivo | Descrição | Volume aproximado |
|----------|------------|-------------------|
| customers.csv | Dados de clientes | 10 MB |
| orders.csv | Pedidos realizados | 25 MB |
| order_items.csv | Itens de cada pedido | 15 MB |
| products.csv | Cadastro de produtos | 5 MB |
| reviews.csv | Avaliações de produtos | 3 MB |

---

##  Localização
Os arquivos são armazenados na **Landing Zone**, e o caminho base é definido em código como:

```python
CATALOG_NAME = "workspace"
SCHEMA_NAME = "projeto_medalhao"
LANDING_PATH = f"/Volumes/{CATALOG_NAME}/{SCHEMA_NAME}/landing_zone/"
```