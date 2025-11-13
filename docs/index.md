
# Projeto: Pipeline de Dados com Databricks e Delta Lake

Este projeto tem como objetivo demonstrar a implementação de um **pipeline de dados completo**
utilizando o **Databricks** e o **Delta Lake**, aplicando a **Arquitetura Medalhão (Medallion Architecture)**.

A arquitetura foi organizada em quatro camadas: **Landing**, **Bronze**, **Silver** e **Gold**,
garantindo uma estrutura modular e escalável para ingestão, transformação e consumo de dados.

---

##  Objetivo
Demonstrar a criação e execução de um pipeline completo de dados, desde a leitura de arquivos CSV até a geração de tabelas analíticas em formato Delta.

---

##  Estrutura Geral do Projeto
```bash
trabalho_medalhao/
├── notebooks/
│ ├── 01_Landing_to_Bronze.ipynb
│ ├── 02_Bronze_to_Silver.ipynb
│ ├── 03_Silver_to_Gold.ipynb
│ └── 004_Atividade_Pratica_Lakehouse.ipynb
├── docs/
│ ├── arquitetura.md
│ ├── dataset.md
│ ├── notebooks.md
│ └── referencias.md
└── mkdocs.yml
```

# Etapa 1: Preparação do Ambiente

Antes de iniciar a execução, o ambiente Databricks foi configurado com um cluster compatível com PySpark e acesso ao Unity Catalog.
Foram definidos parâmetros básicos para padronizar os caminhos e nomes das tabelas, incluindo:

CATALOG_NAME: workspace

SCHEMA_NAME: projeto_medalhao

LANDING_PATH: /Volumes/workspace/projeto_medalhao/landing_zone/

Os arquivos CSV simulando dados de um e-commerce (clientes, pedidos, produtos e avaliações) foram armazenados na Landing Zone. O ambiente local também foi preparado com Python 3.8+ e instalação dos pacotes mkdocs e mkdocs-material para documentação.

---

# Etapa 2: Estrutura do Dataset

O conjunto de dados utilizado representa informações de e-commerce, composto por:

Arquivo	Descrição	Volume aproximado
customers.csv	Dados de clientes	10 MB
orders.csv	Pedidos realizados	25 MB
order_items.csv	Itens de cada pedido	15 MB
products.csv	Cadastro de produtos	5 MB
reviews.csv	Avaliações de produtos	3 MB

Esses arquivos foram a base da camada Landing, a primeira da arquitetura Medalhão.

# Etapa 3: Criação da Camada Bronze

O primeiro notebook executado foi o 01_Landing_to_Bronze.ipynb, responsável por realizar a leitura dos arquivos CSV brutos da Landing Zone.
Nesta etapa, os dados foram padronizados e gravados no formato Delta Lake, originando as tabelas da camada Bronze, que armazena os dados quase brutos, mas já com estrutura organizada.

Exemplo de estrutura gerada:
```bash
Bronze/
 ├── bronze_customers.delta
 ├── bronze_orders.delta
 ├── bronze_products.delta
 └── bronze_reviews.delta
```
 Essa camada tem como objetivo preservar a integridade dos dados originais e permitir reprocessamentos futuros.

 # Etapa 4: Transformação para a Camada Silver

No notebook 02_Bronze_to_Silver.ipynb, iniciou-se o processo de limpeza, enriquecimento e normalização das tabelas Bronze.
Foram tratados valores nulos, ajustados tipos de dados e removidas inconsistências. Além disso, as tabelas foram cruzadas para gerar visões analíticas intermediárias, já prontas para consultas de negócio.

Estrutura gerada:
```bash
Silver/
 ├── silver_orders_enriched.delta
 ├── silver_customers_enriched.delta
 └── silver_products_enriched.delta
```

O objetivo dessa camada é fornecer dados limpos, consistentes e integrados, facilitando análises e agregações futuras.

# Etapa 5: Criação da Camada Gold

Por fim, o notebook 03_Silver_to_Gold.ipynb consolidou os dados da camada Silver em tabelas analíticas otimizadas para consumo.
Foram aplicadas transformações finais, cálculos agregados e métricas de negócio — como resumos de vendas e análises de comportamento de clientes.

As tabelas resultantes foram:
```bash
Gold/
 ├── gold_sales_summary.delta
 └── gold_customer_rfm.delta
```
 Essa camada é voltada diretamente para relatórios e dashboards, sendo a base de visualizações no Power BI e análises de indicadores de desempenho.

# Etapa 6: Documentação e Publicação

A documentação do projeto foi criada utilizando o MkDocs com tema Material, permitindo gerar um site estático de fácil navegação.
O arquivo mkdocs.yml definiu o nome, descrição, autores e estrutura das páginas (Início, Arquitetura, Dataset e Referências), além do link direto para o repositório no GitHub.

O conteúdo técnico foi dividido em arquivos Markdown (.md) localizados na pasta docs/, e o site pôde ser executado localmente com o comando:

```bash
mkdocs serve
```

# Conclusão

Com a execução das três camadas — Landing → Bronze → Silver → Gold — o projeto demonstrou o fluxo completo de tratamento de dados em ambiente Lakehouse, integrando o Databricks e o Delta Lake.
O resultado é uma arquitetura moderna, escalável e confiável para análise de dados, pronta para integração com ferramentas de BI e geração de insights estratégicos.

