# Arquitetura Medalhão

A **Arquitetura Medalhão** é uma abordagem amplamente usada em engenharia de dados moderna,
com o objetivo de organizar e refinar os dados progressivamente em camadas.

---

##  Camadas do Pipeline

| Camada | Descrição | Tipo de Dados |
|--------|------------|----------------|
| **Landing** | Área de recepção dos dados brutos, como foram recebidos da fonte. | CSV / JSON |
| **Bronze** | Conversão dos dados para formato Delta, com estrutura definida. | Raw Delta |
| **Silver** | Dados tratados, limpos e enriquecidos. | Curated Delta |
| **Gold** | Dados analíticos, prontos para dashboards e relatórios. | Aggregated Delta |

---

##  Fluxo do Pipeline

1. **Landing → Bronze:** ingestão e conversão para formato Delta.  
2. **Bronze → Silver:** tratamento, limpeza e padronização.  
3. **Silver → Gold:** agregações e estruturação final para análise.

---

##  Benefícios da Arquitetura Medalhão

- Padronização e controle das etapas de transformação.
- Reprocessamento facilitado.
- Escalabilidade e reusabilidade de dados.
- Integração direta com ferramentas de BI e Analytics.
