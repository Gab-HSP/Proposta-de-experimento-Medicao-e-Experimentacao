# Plano de Experimento - Scoping e Planejamento

## 1. Identificação Básica

### 1.1 Título do Experimento
Impacto da presença de ruído nos dados sobre a precisão de algoritmos de classificação supervisionada

### 1.2 Código / ID
`EXP-TCC-2025-RUIDO-DADOS-CLASSIFICACAO`

### 1.3 Versão do Documento
- **Versão Atual:** v1.0
- **Histórico de Revisão:**
  - v1.0 (23/11/2025): Versão inicial do plano de experimento

### 1.4 Datas
**Data de criação:** 20/11/2025  
**Última atualização:** 26/11/2025

### 1.5 Autores
- **Autor:** Gabriel Henrique Silva Pereira  
  - **Curso / Área:** Engenharia de Software  
  - **Instituição:** PUC Minas  
  - **E-mail:** gabriel.pereira.676690@sga.pucminas.br  

### 1.6 Responsável Principal
- **Responsável Principal (PI):** Gabriel Henrique Silva Pereira

### 1.7 Projeto / Produto / Iniciativa Relacionada
Este plano de experimento integra o Trabalho de Conclusão de Curso (TCC) na área de Engenharia de Dados, Qualidade de Dados e Aprendizado de Máquina.

## 2. Contexto e Problema

### 2.1 Descrição do Problema / Oportunidade
Modelos de aprendizado de máquina são amplamente utilizados em aplicações reais, mas sua performance depende fortemente da qualidade dos dados de entrada. Em muitos cenários, conjuntos de dados podem conter erros de medição, inconsistências, rótulos incorretos, ruído aleatório, registros duplicados, faltantes ou contraditórios. Esse tipo de ruído pode degradar a precisão dos modelos, afetar a capacidade de generalização, aumentar o overfitting e causar interpretações incorretas.

### 2.2 Contexto Organizacional e Técnico
- **Ambiente:** Acadêmico (disciplina de experimentação)
- **Domínio:** Conjuntos de dados tabulares clássicos de classificação
- **Técnicas:** Machine Learning supervisionado
- **Ferramentas:** Python, scikit-learn, Pandas, NumPy

### 2.3 Trabalhos e Evidências Prévias
Estudos mostram que classificadores são sensíveis à qualidade dos dados, mas o grau de sensibilidade varia conforme o algoritmo. Há falta de experimentos que avaliem níveis específicos de ruído e comparações diretas entre classificadores simples.

### 2.4 Referencial Teórico e Empírico Essencial
Baseia-se em três pilares: Qualidade de Dados, Aprendizado de Máquina Supervisionado e Engenharia de Software Empírica.

## 3. Objetivos e Questões (GQM)

### 3.1 Objetivo Geral
**Analisar** o impacto de diferentes níveis de ruído em conjuntos de dados  
**com o propósito de** avaliar a degradação de desempenho em algoritmos de classificação  
**sob a perspectiva** de cientistas de dados e engenheiros de machine learning  
**no contexto** de modelos supervisionados aplicados a dados tabulares.

### 3.2 Objetivos Específicos
**O1.** Avaliar o impacto do ruído na acurácia dos classificadores  
**O2.** Comparar a robustez de diferentes algoritmos frente ao ruído  
**O3.** Analisar o efeito do ruído nas demais métricas de classificação  
**O4.** Determinar se o aumento progressivo de ruído causa degradação linear ou exponencial

### 3.3 Questões de Pesquisa / de Negócio
**Q1.1:** Como a acurácia varia conforme aumenta o ruído?  
**Q1.2:** Existe um nível crítico de ruído em que o modelo perde utilidade?  
**Q1.3:** A queda de performance é consistente entre diferentes datasets?  

**Q2.1:** Qual algoritmo mantém melhor desempenho com 10%–30% de ruído?  
**Q2.2:** Algoritmos de árvore são mais robustos que SVM e regressão?  
**Q2.3:** Há diferença na robustez entre classificadores lineares e não-lineares?  

**Q3.1:** O F1-score é mais sensível ao ruído do que a acurácia?  
**Q3.2:** Ruído afeta mais precisão ou recall?  
**Q3.3:** Como o ruído impacta a curva ROC-AUC?  

**Q4.1:** A queda de desempenho é linear conforme o ruído aumenta?  
**Q4.2:** Há aumento de variabilidade nos resultados com mais ruído?  
**Q4.3:** Existe um ponto de inflexão onde a degradação se acelera?

### 3.4 Métricas Associadas (GQM)

| Objetivo | Pergunta | Métrica | Descrição | Unidade |
|----------|----------|---------|-----------|---------|
| O1 | Q1.1 | M1 – Acurácia | Percentual de classificações corretas | % |
| O1 | Q1.1 | M2 – Acurácia Balanceada | Média das acurácias por classe | % |
| O1 | Q1.2 | M3 – Queda Percentual | Diferença entre acurácia original e com ruído | % |
| O1 | Q1.3 | M4 – Consistência entre Datasets | Variação da queda entre diferentes bases | Coeficiente |
| O2 | Q2.1 | M5 – Robustez Relativa | Acurácia média por algoritmo em todos níveis | Índice |
| O2 | Q2.2 | M6 – Diferença de Robustez | Comparação entre tipos de algoritmos | % |
| O2 | Q2.3 | M7 – Sensibilidade ao Ruído | Taxa de mudança por tipo de algoritmo | %/nível |
| O3 | Q3.1 | M8 – F1-Score | Média harmônica entre precisão e recall | % |
| O3 | Q3.1 | M9 – Diferença F1-Acurácia | Comparação entre métricas | Pontos % |
| O3 | Q3.2 | M10 – Precisão | Verdadeiros positivos ÷ positivos previstos | % |
| O3 | Q3.2 | M11 – Recall | Verdadeiros positivos ÷ positivos reais | % |
| O3 | Q3.3 | M12 – ROC-AUC | Área sob a curva ROC | Escala 0-1 |
| O4 | Q4.1 | M13 – Taxa de Degradação | Acurácia perdida / percentual de ruído | %/nível |
| O4 | Q4.2 | M14 – Variância | Dispersão das métricas entre execuções | Unidade estatística |
| O4 | Q4.3 | M15 – Ponto de Inflexão | Nível onde degradação muda de padrão | % ruído |

### Tabela de Métricas Detalhadas

| Métrica | Descrição | Unidade |
|---------|-----------|---------|
| M1 – Acurácia | Percentual de classificações corretas no total | % |
| M2 – Acurácia Balanceada | Média das acurácias por classe, considerando desbalanceamento | % |
| M3 – Queda Percentual | Diferença percentual entre acurácia original e com ruído | % |
| M4 – Consistência entre Datasets | Coeficiente de variação da queda entre diferentes bases | Coeficiente |
| M5 – Robustez Relativa | Índice comparativo de manutenção de performance | Índice 0-1 |
| M6 – Diferença de Robustez | Comparação percentual entre tipos de algoritmos | % |
| M7 – Sensibilidade ao Ruído | Taxa de mudança de performance por nível de ruído | %/nível |
| M8 – F1-Score | Média harmônica entre precisão e recall | % |
| M9 – Diferença F1-Acurácia | Diferença em pontos percentuais entre F1 e acurácia | Pontos % |
| M10 – Precisão | Proporção de verdadeiros positivos entre preditos positivos | % |
| M11 – Recall | Proporção de verdadeiros positivos entre reais positivos | % |
| M12 – ROC-AUC | Área sob a curva Característica de Operação do Receptor | Escala 0-1 |
| M13 – Taxa de Degradação | Razão entre perda de acurácia e nível de ruído | %/nível |
| M14 – Variância | Medida de dispersão dos resultados entre execuções | Unidade estatística |
| M15 – Ponto de Inflexão | Nível de ruído onde padrão de degradação muda | % ruído |

## 4. Escopo e Contexto do Experimento

### 4.1 Escopo Funcional / de Processo
**Incluído:**
- Conjuntos de dados tabulares clássicos (Iris, Wine, Breast Cancer)
- Algoritmos: Regressão Logística, Decision Tree, SVM
- Níveis de ruído: 0%, 10%, 20%, 30%
- Adição de ruído em features numéricas
- Métricas de avaliação de classificação

**Excluído:**
- Algoritmos de deep learning
- Dados de séries temporais ou imagens
- Correção automática de ruído
- Pipelines completos de MLops

### 4.2 Contexto do Estudo
- **Tipo de organização:** Acadêmica
- **Projeto:** TCC em Engenharia de Software
- **Experiência:** Nível intermediário em machine learning

### 4.3 Premissas
- É possível gerar ruído artificial de forma controlada
- Bibliotecas disponíveis permitem executar todos os algoritmos
- Datasets selecionados permitem classificação supervisionada

### 4.4 Restrições
- Tempo limitado da disciplina para planejamento
- Recursos computacionais básicos
- Não envolvimento de grandes bases reais

### 4.5 Limitações Previstas
- Resultados podem não generalizar para deep learning
- Ruído sintético pode não refletir perfeitamente ruído real
- Apenas três algoritmos considerados

## 5. Stakeholders e Impacto Esperado

### 5.1 Stakeholders Principais
- Pesquisador (PI)
- Professor orientador
- Cientistas de dados
- Engenheiros de machine learning

### 5.2 Interesses e Expectativas dos Stakeholders
- **PI:** Realizar experimento claro e replicável
- **Professor:** Coerência metodológica e validade
- **Cientistas de dados:** Entender robustez dos algoritmos
- **Eng. ML:** Ajustar modelos em cenários com ruído

### 5.3 Impactos Potenciais no Processo / Produto
- Melhor compreensão da relação qualidade de dados vs performance
- Orientação sobre algoritmos mais robustos
- Apoio à tomada de decisão em pipelines de dados

## 6. Riscos de Alto Nível, Premissas e Critérios de Sucesso

### 6.1 Riscos de Alto Nível
- Escolha inadequada do dataset ou algoritmos
- Níveis de ruído insuficientes para diferença estatística
- Alta variabilidade nos resultados

### 6.2 Critérios de Sucesso Globais
- Planejamento claro e consistente
- Métricas adequadas e alinhadas às questões
- Desenho experimental replicável

### 6.3 Critérios de Parada Antecipada
- Falta de acesso aos datasets planejados
- Dificuldade de implementação dos algoritmos
- Mudança de escopo do TCC

## 7. Modelo Conceitual e Hipóteses

### 7.1 Modelo Conceitual do Experimento
O experimento propõe que o aumento progressivo de ruído nos dados de treinamento causa degradação não-linear no desempenho dos classificadores, com algoritmos baseados em árvore demonstrando maior robustez comparada a modelos lineares.

### 7.2 Hipóteses Formais
**H₀:** Não há diferença significativa no desempenho dos classificadores entre diferentes níveis de ruído nos dados  
**H₁:** Existe diferença significativa no desempenho dos classificadores conforme aumenta o nível de ruído nos dados

### 7.3 Nível de Significância e Considerações de Poder
- **Nível de significância (α):** 0,05
- **Poder estatístico (1-β):** 80%
- **Tamanho de efeito considerado:** moderado (d = 0,5)

## 8. Variáveis, Fatores, Tratamentos e Objetos de Estudo

### 8.1 Objetos de Estudo
- Módulos de código de classificação
- Conjuntos de dados de benchmark
- Métricas de avaliação de modelos

### 8.2 Sujeitos / Participantes (Visão Geral)
Estudantes de pós-graduação com conhecimento em machine learning (simulação computacional)

### 8.3 Variáveis Independentes (Fatores) e Seus Níveis
- **Fator A:** Tipo de algoritmo (Regressão Logística, Decision Tree, SVM)
- **Fator B:** Nível de ruído (0%, 10%, 20%, 30%)

### 8.4 Tratamentos (Condições Experimentais)
12 condições experimentais (3 algoritmos × 4 níveis de ruído)

### 8.5 Variáveis Dependentes (Respostas)
- Acurácia, F1-Score, Precisão, Recall, ROC-AUC
- Taxa de degradação, Robustez relativa

### 8.6 Variáveis de Controle / Bloqueio
- Dataset utilizado
- Divisão treino/teste
- Hiperparâmetros dos algoritmos

### 8.7 Possíveis Variáveis de Confusão Conhecidas
- Características intrínsecas dos datasets
- Complexidade do problema de classificação
- Número de features e instâncias

## 9. Desenho Experimental

### 9.1 Tipo de Desenho
Fatorial completamente randomizado com medidas repetidas

### 9.2 Randomização e Alocação
Ordem de execução dos tratamentos randomizada para controlar efeitos de aprendizado

### 9.3 Balanceamento e Contrabalanço
Cada algoritmo testado em todos os níveis de ruído com mesma quantidade de repetições

### 9.4 Número de Grupos e Sessões
12 grupos experimentais (3 algoritmos × 4 níveis de ruído) com 30 repetições cada

## 10. População, Sujeitos e Amostragem

### 10.1 População-Alvo
Estudantes e profissionais com conhecimento em machine learning e classificação supervisionada

### 10.2 Critérios de Inclusão de Sujeitos
- Conhecimento básico em Python
- Experiência com scikit-learn
- Disponibilidade para participar do experimento

### 10.3 Critérios de Exclusão de Sujeitos
- Conflitos de interesse com ferramentas
- Falta de conhecimento técnico mínimo
- Restrições de tempo

### 10.4 Tamanho da Amostra Planejado
30 participantes por grupo (total: 360 observações)

### 10.5 Método de Seleção / Recrutamento
Amostra de conveniência entre estudantes de pós-graduação

### 10.6 Treinamento e Preparação dos Sujeitos
Sessão de treinamento sobre protocolo experimental e ferramentas

## 11. Instrumentação e Protocolo Operacional

### 11.1 Instrumentos de Coleta
- Questionários online (Google Forms)
- Scripts Python para coleta automática
- Planilhas para registro manual

### 11.2 Materiais de Suporte
- Instruções detalhadas do experimento
- Guia de uso das ferramentas
- Template para registro de resultados

### 11.3 Procedimento Experimental
1. Recrutamento e treinamento
2. Alocação randomizada
3. Execução dos tratamentos
4. Coleta de métricas
5. Análise estatística

### 11.4 Plano de Piloto
Piloto com 5 participantes para validar instrumentos e procedimentos

## 12. Plano de Análise de Dados (Pré-Execução)

### 12.1 Estratégia Geral de Análise
ANOVA two-way para testar efeitos principais e interações

### 12.2 Métodos Estatísticos Planejados
- Teste de normalidade (Shapiro-Wilk)
- ANOVA fatorial
- Testes post-hoc (Tukey HSD)
- Análise de regressão

### 12.3 Tratamento de Dados Faltantes e Outliers
Exclusão de outliers extremos (> 3 DP) e imputação para dados faltantes

### 12.4 Plano de Análise para Dados Qualitativos
Análise de conteúdo para comentários e observações

## 13. Avaliação de Validade (Ameaças e Mitigação)

### 13.1 Validade de Conclusão
**Ameaça:** Baixo poder estatístico  
**Mitigação:** Cálculo amostral prévio e repetições adequadas

### 13.2 Validade Interna
**Ameaça:** Efeitos de aprendizagem  
**Mitigação:** Contrabalanço e randomização

### 13.3 Validade de Constructo
**Ameaça:** Operacionalização inadequada das métricas  
**Mitigação:** Uso de métricas consagradas na literatura

### 13.4 Validade Externa
**Ameaça:** Contexto específico acadêmico  
**Mitigação:** Uso de datasets e algoritmos padrão

### 13.5 Resumo das Principais Ameaças e Estratégias de Mitigação
| Ameaça | Estratégia de Mitigação |
|--------|-------------------------|
| Baixo poder estatístico | Cálculo amostral adequado |
| Vieses de seleção | Randomização e critérios claros |
| Instrumentação inadequada | Validação por piloto |

## 14. Ética, Privacidade e Conformidade

### 14.1 Questões Éticas
Participação voluntária com direito a desistência a qualquer momento

### 14.2 Consentimento Informado
Termo de consentimento explicando objetivos, riscos e benefícios

### 14.3 Privacidade e Proteção de Dados
Dados anonimizados e armazenados por 5 anos

### 14.4 Aprovações Necessárias
Comitê de ética institucional e orientador do TCC

## 15. Recursos, Infraestrutura e Orçamento

### 15.1 Recursos Humanos e Papéis
- **PI:** Planejamento e execução
- **Orientador:** Supervisão metodológica

### 15.2 Infraestrutura Técnica Necessária
- Computadores pessoais
- Ambiente Python com bibliotecas ML
- Ferramentas de análise estatística

### 15.3 Materiais e Insumos
- Licenças de software (open-source)
- Serviços de cloud para processamento

### 15.4 Orçamento e Custos Estimados
Custos mínimos (ferramentas open-source e recursos próprios)

## 16. Cronograma, Marcos e Riscos Operacionais

### 16.1 Macrocronograma
- **Semana 1-2:** Planejamento e validação
- **Semana 3-4:** Recrutamento e piloto
- **Semana 5-8:** Execução do experimento
- **Semana 9-10:** Análise e relatório

### 16.2 Dependências entre Atividades
Validação ética → Recrutamento → Execução → Análise

### 16.3 Riscos Operacionais e Plano de Contingência
**Risco:** Baixa adesão no recrutamento  
**Contingência:** Estender período ou ampliar critérios

## 17. Governança do Experimento

### 17.1 Papéis e Responsabilidades Formais
- **PI:** Execução e análise
- **Orientador:** Validação metodológica
- **Participantes:** Execução das tarefas

### 17.2 Ritos de Acompanhamento Pré-Execução
Reuniões semanais com orientador durante planejamento

### 17.3 Processo de Controle de Mudanças no Plano
Mudanças aprovadas por PI e orientador, documentadas no histórico

## 18. Plano de Documentação e Reprodutibilidade

### 18.1 Repositórios e Convenções de Nomeação
Repositório Git com estrutura padronizada de pastas e nomenclatura

### 18.2 Templates e Artefatos Padrão
- Template de consentimento
- Scripts de análise padronizados
- Formulários de coleta

### 18.3 Plano de Empacotamento para Replicação Futura
Documentação completa com Dockerfile e requirements.txt

## 19. Plano de Comunicação

### 19.1 Públicos e Mensagens-Chave Pré-Execução
- **Participantes:** Objetivos e procedimentos
- **Orientador:** Progresso e desafios
- **Comunidade:** Resultados e insights

### 19.2 Canais e Frequência de Comunicação
- E-mail para comunicação formal
- Reuniões semanais com orientador
- Plataforma online para participantes

### 19.3 Pontos de Comunicação Obrigatórios
- Aprovação do plano
- Início e término do recrutamento
- Resultados finais

## 20. Critérios de Prontidão para Execução (Definition of Ready)

### 20.1 Checklist de Prontidão
- [ ] Plano aprovado pelo orientador
- [ ] Aprovação ética obtida
- [ ] Instrumentos validados no piloto
- [ ] Recrutamento concluído
- [ ] Infraestrutura preparada

### 20.2 Aprovações Finais para Iniciar a Operação
Orientador e comitê de ética devem autorizar início da execução
