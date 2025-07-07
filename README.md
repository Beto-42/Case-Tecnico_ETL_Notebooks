# Documentação de Rotinas de ETL e Análise de Dados

## 📖 Visão Geral do Projeto

Este repositório documenta um projeto completo de pipeline de dados, demonstrando um fluxo de trabalho de ponta a ponta: desde a geração de dados brutos e a execução de testes de qualidade, passando por um processo de ETL com múltiplas etapas de tratamento e aplicação de regras de negócio, até a visualização final em um dashboard interativo no Power BI.

O objetivo é apresentar uma solução robusta para o tratamento de dados, garantindo que as informações que chegam para a análise final sejam íntegras, consistentes e precisas.

---

## ✨ Principais Funcionalidades

* **Simulação de Ambiente Real:** Geração de um dataset inicial com problemas comuns de qualidade de dados (nulos, duplicatas, valores negativos, etc.).
* **Testes de Qualidade de Dados:** Aplicação de rotinas para verificação de **Integridade**, **Consistência** e **Precisão** dos dados.
* **Pipeline de ETL Sequencial:** Utilização de Jobs (Notebooks Python) para transformar e enriquecer os dados passo a passo.
* **Armazenamento e Verificação:** Conexão com um banco de dados **SQLite** para armazenar e validar os dados processados.
* **Visualização de Dados:** Desenvolvimento de um relatório no **Power BI** com KPIs e dashboards para análise e suporte à tomada de decisão.

---

## 📂 Estrutura do Projeto e Arquivos

O fluxo de trabalho é dividido nos seguintes componentes principais:

### 1. Processos ETL e Criação de Jobs (Notebooks Python)

> O coração do projeto, onde os dados são gerados, testados, limpos e enriquecidos através de uma série de rotinas sequenciais.

* `ETL1.ipynb`
    * **Descrição:** Ponto de partida do pipeline. Este notebook gera um arquivo `.csv` simulando dados brutos com diversos problemas (campos nulos, valores negativos, produtos duplicados, etc.).
    * **Destaque:** Ao final, executa e apresenta relatórios dos **Testes de Integridade, Consistência e Precisão**, fornecendo um diagnóstico completo da qualidade dos dados iniciais.

* `job_v1.ipynb`
    * **Descrição:** Inicia o pipeline de tratamento. Este job estabelece uma conexão com um banco de dados **SQLite**, cria a estrutura de tabelas e armazena as informações do arquivo CSV gerado pelo `ETL1.ipynb` para verificação e processamento inicial.

* `job_v2.ipynb`
    * **Descrição:** Aplica a primeira regra de negócio, que consiste em carregar para a próxima etapa apenas os registros que possuem uma **quantidade produzida superior a 10**.

* `job_v3.ipynb`
    * **Descrição:** Aplica uma regra de limpeza de dados, removendo o caractere de **ponto final** (`.`) em colunas numéricas para evitar erros de truncamento.

* `job_v4.ipynb`
    * **Descrição:** Executa uma etapa de **enriquecimento de dados**, onde novas colunas calculadas (como margem de lucro, por exemplo) são adicionadas ao dataset para agregar valor à análise.

* `job_v5.1.ipynb`
    * **Descrição:** Realiza um ciclo final de limpeza e tratamento nos dados já enriquecidos, garantindo a máxima qualidade e consistência do dataset antes de ser disponibilizado para a camada de visualização.

### 2. Relatório em Power BI

* **Arquivo:** `Relatorio_Producao.pbix` (exemplo de nome)
    * **Descrição:** Arquivo do Power BI contendo o relatório final. Nele, foram desenvolvidas fórmulas em **DAX (Data Analysis Expressions)** para criar KPIs, métricas e cálculos complexos que servem de base para os visuais.
    * **Destaque:** O resultado é um dashboard interativo, projetado para atender às necessidades da audiência final e facilitar a tomada de decisão baseada em dados.

### 3. Documentação Adicional

* **Pasta:** `/Documentacao_SQL`
    * **Descrição:** Contém documentos e prints (`.png` ou `.jpg`) dos scripts SQL utilizados para interagir com o banco de dados, incluindo a criação de tabelas e outras consultas relevantes, servindo como um anexo técnico do projeto.

---

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python
* **Bibliotecas:** Pandas, NumPy, Matplotlib, Seaborn, SQLite3
* **Banco de Dados:** SQLite
* **BI e Visualização:** Microsoft Power BI
* **Linguagens de Análise:** DAX, SQL
