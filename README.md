# Engenharia de Dados - Pipeline E-commerce Olist

Este projeto apresenta uma solução completa de engenharia de dados desenvolvida no Databricks utilizando PySpark. O objetivo é processar e transformar dados brutos do ecossistema Olist em informações analíticas prontas para o consumo de negócio, seguindo as melhores práticas da arquitetura Medallion.

## Estrutura do Projeto

A solução foi dividida em três notebooks principais, garantindo a modularização e a escalabilidade do processo de ETL:

### Camada Bronze: Ingestão e Landing
O processo inicia-se com a leitura de arquivos CSV originais e a conversão para tabelas Delta. Nesta etapa, realizamos o consumo de uma API externa do Banco Central para obter as cotações históricas do Dólar, fundamentais para a normalização financeira do projeto.

### Camada Silver: Limpeza e Enriquecimento
Nesta camada, os dados são refinados. Aplicamos técnicas de deduplicação por Window Functions para garantir a unicidade de registros de clientes e produtos. Também realizamos traduções de status, cálculos de prazos logísticos e a integração dos valores de câmbio para gerar métricas financeiras em USD.

### Camada Gold: Analytics e Data Marts
A etapa final consolida as tabelas de fato e dimensão em visões agregadas. Focamos na performance comercial por categoria e na qualidade da experiência do cliente. Utilizamos lógicas de ranking com tratamento de empates para identificar com precisão os melhores e piores desempenhos de produtos e vendedores.

## Tecnologias e Metodologias

* **Processamento:** PySpark (Spark SQL e DataFrames)
* **Storage:** Delta Lake (Formato Delta)
* **Infraestrutura:** Databricks Community Edition
* **Orquestração:** Databricks Jobs (Workflows)
* **Otimização:** Particionamento e ZORDER

## Orquestração

O fluxo de dados é automatizado através de um Workflow que coordena a execução sequencial dos notebooks. O sistema está configurado para uma execução diária agendada para as 13:00 (Fuso America/Recife), garantindo que os dados analíticos estejam sempre atualizados para a tomada de decisão.

<img width="1255" height="685" alt="Captura de Tela 2026-04-07 às 13 30 51" src="https://github.com/user-attachments/assets/2263d45a-14a8-4c50-90c3-e8261d6f22a4" />


<img width="767" height="300" alt="Captura de Tela 2026-04-07 às 13 30 33" src="https://github.com/user-attachments/assets/8db355e3-6c50-48bc-aa7e-57b6e5a1648f" />
