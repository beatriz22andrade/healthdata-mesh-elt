 # **HealthData Mesh: Pipeline ELT Distribuído em Nuvem**

## 📌 Objetivo do Projeto

Este projeto demonstra a construção de um pipeline de Engenharia de Dados (ELT) baseado em conceitos de Data Mesh, orquestrando o processamento distribuído de dados de saúde simulados na nuvem. O objetivo foi ingerir, limpar e cruzar dados de dois domínios hospitalares distintos (Triagem e Diagnóstico) e extrair KPIs de risco cardíaco.

## 🛠️ Arquitetura e Tecnologias

Gestão Ágil: Kanban via Notion para organização das tarefas (épicos de Ingestão, Transformação e Qualidade).

Data Lake (Cloud): Amazon S3 (AWS) estruturado em camadas físicas (/raw e /trusted).

Processamento Distribuído: Apache Spark (PySpark) executado no ambiente Databricks Serverless.

Qualidade e Validação: SQL Avançado (CTEs, Window Functions, Agregações) para geração de resumos executivos.

## ⚙️ Fluxo de Dados (Pipeline)

Geração e Ingestão (Simulada): Criação de dados sintéticos via Python representando pacientes, sinais vitais (com injeção intencional de falhas/nulos) e histórico de risco.

Transformação (Silver Layer): Utilização do PySpark para tratamento de nulos, desmembramento de colunas complexas (pressão arterial dividida em sistólica e diastólica) e inner join entre os domínios.

Refinamento e KPIs (Gold Layer): Aplicação de consultas SQL direto na view temporária do Spark para gerar métricas de risco, média de batimentos e rankeamento de gravidade.

Armazenamento (S3): Exportação dos dados processados (formato tabular) para a camada /trusted no Amazon S3.

## 📊 Resultados e Demonstração

### 1. DataBricks e a tabela com dados simulados 

<img width="1396" height="757" alt="TabelaPySpark" src="https://github.com/user-attachments/assets/7c14c6ff-57ca-4acf-ac05-d670b15eb996" />


### 2. Consulta em SQl para gerar métricas e realizar um ranking

<img width="1386" height="755" alt="Consulta-SQL" src="https://github.com/user-attachments/assets/062a354c-0906-4af4-a124-15dc12b16930" />


### 3. Exportação de dados no AWS 

<img width="1910" height="602" alt="bucket-AWS" src="https://github.com/user-attachments/assets/b7affb74-7b6e-4cb5-9bf2-0f4f199d583c" />


### 4. Organização do projeto no Notion (Método ágil Kanban)
<img width="1562" height="772" alt="Kanban-AnaliseCardiaca" src="https://github.com/user-attachments/assets/c46febea-3f8c-4d3c-81e6-6e581e1fb067" />


O pipeline processou 1.500 registros médicos distribuídos em 2 domínios de dados em menos de 3 segundos. A transformação resultou na extração de 5 KPIs estratégicos de saúde (incluindo médias vitais e ranking de gravidade), permitindo uma visão analítica rápida e confiável para a tomada de decisão.
