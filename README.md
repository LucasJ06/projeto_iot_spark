# 🚀 Pipeline de Telemetria IoT com Apache Spark e Arquitetura Medallion
Este projeto demonstra a construção de um pipeline de dados escalável utilizando Apache Spark no Databricks, processando mais de 1 milhão de registros de telemetria de sensores industriais. O objetivo é transformar dados brutos de sensores em insights de negócio sobre falhas críticas, utilizando as melhores práticas de Engenharia de Dados.

### 🏗️ Arquitetura do Projeto
O projeto segue a Arquitetura Medallion, garantindo a qualidade e a linhagem dos dados em cada etapa:

Camada Bronze (Ingestão): Geração e armazenamento de mais de 1 milhão de registros brutos de sensores (ID, Temperatura, Timestamp e Status).

Camada Silver (Transformação): Limpeza de dados, remoção de duplicatas e filtragem de estados críticos.

Camada Gold (Business): Agregação de dados para criação de um ranking dos sensores com maior índice de falhas.

### 🛠️ Tecnologias Utilizadas
Apache Spark (PySpark): Processamento distribuído de grandes volumes de dados.

Delta Lake: Armazenamento com suporte a transações ACID e controle de versão.

Databricks: Plataforma unificada de análise de dados.

Python/SQL: Linguagens utilizadas para manipulação e consulta dos dados.

### 🛡️ Destaques Técnicos
1. Segurança ACID e Governança
Utilizei o Delta Lake para garantir a integridade dos dados através de transações ACID. Isso permite:

  Time Travel: Capacidade de consultar versões anteriores da tabela e auditar mudanças através do comando DESCRIBE HISTORY.

  Rollback: Proteção contra deleções acidentais ou falhas no pipeline.

2. Performance em Big Data
  Particionamento: A Camada Bronze foi particionada pela coluna status, otimizando as consultas na Camada Silver.

  Escalabilidade: O pipeline foi desenhado para processar 100 milhões de linhas em menos de 2 segundos.

3. Lógica de Negócio (Camada Gold)
  A agregação final identifica os sensores mais problemáticos, filtrando registros onde a temperatura excede 45° em estado de erro.
