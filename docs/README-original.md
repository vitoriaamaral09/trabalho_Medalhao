# README Original

# Projeto: Pipeline de Dados com Databricks e Delta Lake. Arquitetura Medalhão.

Este repositório apresenta o desenvolvimento de um **Pipeline de Dados** utilizando o **Databricks** e o **Delta Lake**, aplicando a **Arquitetura Medalhão (Medallion Architecture)**, com as camadas **Landing**, **Bronze**, **Silver** e **Gold**.

O trabalho foi desenvolvido como parte da disciplina de **Engenharia de Dados**, com foco em demonstrar o funcionamento completo de um ambiente de processamento de dados moderno e escalável.

---

## Objetivo do Projeto

O principal objetivo foi **implementar um pipeline orquestrado e funcional**, capaz de mover e transformar dados brutos em dados refinados, passando por todas as camadas da Arquitetura Medalhão.  
Além disso, foram avaliados critérios como:
- Organização do repositório no GitHub  
- Estrutura e clareza dos **notebooks Databricks**
- Funcionamento da **Job & Pipeline**
- Criação de **documentação com MkDocs**
- Criação do **README**

---

## Arquitetura Medalhão

É uma abordagem de camadas para a engenharia de dados, utilizada em ambientes como o **Databricks**.  
Cada camada tem uma função específica:

| Camada | Descrição | Tipo de dado |
|--------|------------|--------------|
| **Landing** | Área de recepção dos dados brutos, exatamente como recebidos das fontes. | CSV / JSON |
| **Bronze** | Dados brutos convertidos em formato Delta, com tipagem e schema definidos. | Raw Delta |
| **Silver** | Dados limpos e tratados, com joins e filtros aplicados. | Curated Delta |
| **Gold** | Dados agregados e prontos para consumo analítico. | Aggregated Delta |

---


## Funcionalidades e Entregáveis

-  5 tabelas (mínimo) em formato **CSV ou JSON**
-  1 notebook para **cada camada** (Landing → Bronze → Silver → Gold)
-   **Job & Pipeline** funcional e orquestrado no Databricks
-  Integração com **GitHub**
-  **Documentação** criada com **MkDocs**
-  Repositório organizado e padronizado

---

## Execução do Pipeline

1. **Upload dos arquivos brutos** para a camada *Landing*.
2. **Execução do notebook `landing_to_bronze.ipynb`**, que converte e move os dados para a camada *Bronze*.
3. **Execução do notebook `bronze_to_silver.ipynb`**, responsável pelo tratamento e padronização.
4. **Execução do notebook `silver_to_gold.ipynb`**, que realiza agregações e gera dados analíticos.
5. **Job & Pipeline** orquestra a execução dos três notebooks na sequência.

---

## Como rodar localmente (documentação)

Para visualizar a documentação com **MkDocs**:

1. Crie um ambiente virtual:
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Mac/Linux
   venv\Scripts\activate     # Windows

   pip install mkdocs mkdocs-material # instala as dependências
   mkdocs serve # inicia o servidor local
   # Acesse o navegador:
    http://127.0.0.1:8000


## Alunas: Eunice de Borba, Maria Laura Jeronimo e Vitória Viana
