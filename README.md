# Proposta-de-experimento-Medicao-e-Experimentacao# Plano de Experimento - Scoping e Planejamento  
## Qualidade de Dados e Impacto de Ruído em Modelos de Classificação

---

# 1. Identificação Básica

## 1.1 Título do Experimento
Impacto da presença de ruído nos dados sobre a precisão de algoritmos de classificação supervisionada

## 1.2 Código / Id
`EXP-TCC-2025-RUIDO-DADOS-CLASSIFICACAO`

## 1.3 Versão do Documento
- **Versão Atual:** v1.0

## 1.4 Datas
**Data de criação:** 20/11/2025  
**Última atualização:** 23/11/2025

## 1.5 Autores
- **Autor:** Gabriel Henrique Silva Pereira  
  - **Curso / Área:** Engenharia de Software  
  - **Instituição:** PUC Minas  
  - **E-mail:** gabriel.pereira.676690@sga.pucminas.br  

## 1.6 Responsável Principal
- **Responsável Principal (PI):** Gabriel Henrique Silva Pereira

## 1.7 Projeto / Produto
Este plano de experimento integra o Trabalho de Conclusão de Curso (TCC) na área de **Engenharia de Dados**, **Qualidade de Dados** e **Aprendizado de Máquina**, com foco em:

- Avaliar o impacto de **ruído em conjuntos de dados** sobre a performance de **classificadores supervisionados**;
- Comparar diferentes **níveis de ruído** e seus efeitos sobre métricas de desempenho;
- Explorar questões relacionadas à **robustez de modelos** frente a dados alterados artificialmente.

---

# 2. Contexto do Problema

## 2.1 Descrição do Problema / Oportunidade
Modelos de aprendizado de máquina são amplamente utilizados em aplicações reais, mas sua performance depende fortemente da **qualidade dos dados de entrada**. Em muitos cenários, conjuntos de dados podem conter:

- erros de medição,  
- inconsistências,  
- rótulos incorretos,  
- ruído aleatório,  
- registros duplicados, faltantes ou contraditórios.

Esse tipo de ruído pode:

- degradar a precisão dos modelos,  
- afetar a capacidade de generalização,  
- aumentar o overfitting,  
- causar interpretações incorretas.  

Entretanto, a literatura ainda apresenta lacunas sobre:

- até que ponto diferentes níveis de ruído impactam classificadores comuns;  
- se certos algoritmos são mais robustos a ruído do que outros;  
- qual tipo de métrica mais sofre impacto;  
- como ruídos nos rótulos afetam mais do que ruído nas features.

O problema central é:

> **Problema:** Não está claro, de forma empírica, qual é o impacto de diferentes níveis de ruído nos dados sobre o desempenho de algoritmos de classificação supervisionada.

## 2.2 Contexto Organizacional e Técnico
O experimento será planejado considerando:

- **Ambiente acadêmico** (disciplina de experimentação);
- **Domínio:** conjuntos de dados tabulares clássicos de classificação;
- **Técnicas de machine learning:** Regressão Logística, Decision Tree e SVM;
- **Níveis de ruído:** 0%, 10%, 20% e 30%;
- **Ambiente técnico:**
  - Python e bibliotecas como scikit-learn;
  - Ferramentas para manipulação de dados como Pandas e NumPy;
  - Scripts para geração artificial de ruído em dados.

## 2.3 Trabalhos e Evidências Prévias
Evidências que motivam o estudo incluem:

- Trabalhos que mostram que **classificadores são sensíveis à qualidade dos dados**, mas o grau de sensibilidade varia conforme o algoritmo.  
- Estudos sobre **robustez em modelos supervisionados**, que sugerem variação significativa no desempenho à medida que se introduz ruído nos rótulos.  
- Práticas de engenharia de dados demonstram que ruído é comum em pipelines reais.  
- Falta de experimentos que avaliem **níveis específicos de ruído** e **comparações diretas entre classificadores simples**.

## 2.4 Referencial Teórico e Empírico Essencial
O experimento se apoia em três bases:

### 1. **Qualidade de Dados**
- Conceitos de acurácia, consistência, confiabilidade;
- Impactos do ruído (aleatório ou sistemático);
- Técnicas de detecção e mitigação de ruído.

### 2. **Aprendizado de Máquina Supervisionado**
- Funcionamento de classificadores simples:  
  - Regressão Logística  
  - Decision Tree  
  - Support Vector Machine  
- Métricas de avaliação: Acurácia, Precisão, Recall, F1-score.

### 3. **Engenharia de Software Empírica**
- Variáveis independentes: níveis de ruído;
- Variáveis dependentes: métricas de desempenho;
- Hipóteses estatísticas;
- Ameaças à validade e desenho experimental.

---

# 3. Objetivos e Questões (GQM)

## 3.1 Objetivo Geral
**Analisar** o impacto de diferentes níveis de ruído em conjuntos de dados  
**com o propósito de** avaliar a degradação de desempenho em algoritmos de classificação  
**sob a perspectiva** de cientistas de dados e engenheiros de machine learning  
**no contexto** de modelos supervisionados aplicados a dados tabulares.

---

## 3.2 Objetivos Específicos
**O1.** Avaliar o impacto do ruído na acurácia dos classificadores.  
**O2.** Comparar a robustez de diferentes algoritmos frente ao ruído.  
**O3.** Analisar o efeito do ruído nas demais métricas (precisão, recall, F1).  
**O4.** Determinar se o aumento progressivo de ruído causa degradação linear ou exponencial.

---

## 3.3 Questões de Pesquisa (por objetivo)

### **O1 – Acurácia**
- **Q1.1:** Como a acurácia varia conforme aumenta o ruído?  
- **Q1.2:** Existe um nível crítico de ruído em que o modelo perde utilidade?

### **O2 – Robustez do Algoritmo**
- **Q2.1:** Qual algoritmo mantém melhor desempenho com 10%–30% de ruído?  
- **Q2.2:** Algoritmos de árvore são mais robustos que SVM e regressão?

### **O3 – Outras Métricas**
- **Q3.1:** O F1-score é mais sensível ao ruído do que a acurácia?  
- **Q3.2:** Ruído afeta mais precisão ou recall?

### **O4 – Intensidade do Impacto**
- **Q4.1:** A queda de desempenho é linear conforme o ruído aumenta?  
- **Q4.2:** Há aumento de variabilidade nos resultados com mais ruído?

---

## 3.4 Métricas Associadas

| Objetivo | Pergunta | Métrica | Descrição |
|----------|----------|---------|-----------|
| O1 | Q1.1 | M1 – Acurácia | Percentual de classificações corretas |
| O1 | Q1.2 | M2 – Queda percentual da acurácia | Diferença entre acurácia original e com ruído |
| O2 | Q2.1 | M3 – Robustez relativa | Acurácia média por algoritmo em todos níveis |
| O3 | Q3.1 | M4 – F1-score | Média harmônica entre precisão e recall |
| O3 | Q3.2 | M5 – Precisão | Verdadeiros positivos ÷ positivos previstos |
| O3 | Q3.2 | M6 – Recall | Verdadeiros positivos ÷ positivos reais |
| O4 | Q4.1 | M7 – Taxa de degradação | Acurácia perdida / percentual de ruído |
| O4 | Q4.2 | M8 – Variância da performance | Dispersão das métricas entre execuções |

---

## 3.5 Tabela Geral das Métricas

| Métrica | Descrição | Unidade |
|---------|-----------|---------|
| M1 | Acurácia | % |
| M2 | Queda percentual da acurácia | % |
| M3 | Robustez relativa | índice |
| M4 | F1-score | % |
| M5 | Precisão | % |
| M6 | Recall | % |
| M7 | Taxa de degradação | % por nível de ruído |
| M8 | Variância da performance | unidade estatística |

---

# 4. Escopo e Contexto do Experimento

## 4.1 Escopo Incluído
- Conjuntos de dados tabulares clássicos (ex: Iris, Wine, Breast Cancer, ou dataset sintético);
- Algoritmos: Regressão Logística, Decision Tree e SVM;
- Níveis de ruído artificial: 0%, 10%, 20%, 30%;
- Adição de ruído em features e/ou labels;
- Avaliação por métricas de classificação;
- Comparação direta entre níveis e algoritmos.

## 4.2 Escopo Excluído
- Algoritmos de deep learning;
- Dados de séries temporais ou imagens;
- Correção automática de ruído;
- Execução de pipelines completos de MLops.

---

## 4.3 Premissas
- É possível gerar ruído artificial de forma controlada.  
- As bibliotecas disponíveis permitem executar todos os algoritmos.  
- O dataset selecionado permite classificação binária ou multiclasse.  
- As métricas serão calculáveis em todos os cenários.

---

## 4.4 Restrições
- Tempo limitado da disciplina para planejamento.  
- Recursos computacionais básicos (notebook pessoal).  
- Não envolvimento de grandes bases de dados reais.  
- Não haverá execução real do experimento neste momento.

---

## 4.5 Limitações Previstas
- Resultados futuros podem não generalizar para deep learning.  
- Ruído sintético pode não refletir perfeitamente ruído real.  
- Apenas três algoritmos serão considerados.  
- Conjuntos de dados pequenos podem limitar análise.  

---

# 5. Stakeholders e Impacto Esperado

## 5.1 Stakeholders Principais
- Pesquisador (PI)  
- Professor orientador  
- Cientistas de dados  
- Engenheiros de machine learning  
- Comunidade acadêmica  
- Profissionais de Engenharia de Dados

---

## 5.2 Interesses e Expectativas

| Stakeholder | Interesse / Expectativa |
|-------------|-------------------------|
| PI | Realizar experimento claro e replicável |
| Professor | Coerência metodológica e validade |
| Cientistas de dados | Entender robustez dos algoritmos |
| Eng. ML | Ajustar modelos em cenários com ruído |
| Eng. Dados | Compreender impacto da qualidade de dados |
| Academia | Evidências empíricas sobre ruído |

---

## 5.3 Impactos Potenciais
- Melhor compreensão da relação entre qualidade de dados e performance.  
- Orientação sobre quais algoritmos são mais robustos.  
- Apoio à tomada de decisão em pipelines de dados.  
- Reflexões para estratégias de limpeza ou detecção de ruído.

---

# 6. Riscos, Critérios de Sucesso e Parada

## 6.1 Riscos de Alto Nível
- Escolha inadequada do dataset ou algoritmos.  
- Níveis de ruído insuficientes para gerar diferença estatística.  
- Alta variabilidade nos resultados, dificultando conclusão.  
- Inadequação das métricas escolhidas.

---

## 6.2 Critérios de Sucesso Globais
- Planejamento claro e consistente.  
- Métricas adequadas e alinhadas às questões.  
- Desenho experimental replicável.  
- Base sólida para execução futura no TCC.

---

## 6.3 Critérios de Parada Antecipada
- Falta de acesso aos datasets planejados.  
- Dificuldade de implementação futura dos algoritmos.  
- Mudança de escopo do TCC.  
- Problemas técnicos impeditivos no ambiente experimental.

---
