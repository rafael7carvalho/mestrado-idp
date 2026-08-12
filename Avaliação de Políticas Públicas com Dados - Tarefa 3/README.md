# Avaliação de Políticas Públicas com Dados — Tarefa 3

Atividade desenvolvida na disciplina **Avaliação de Políticas Públicas com Dados**, no âmbito do mestrado do IDP.

## Objetivo

A atividade aplica métodos de *propensity score* para avaliar o efeito do Programa Bolsa Família sobre frequência escolar, explorando diferentes estratégias de estimação e balanceamento entre os grupos de tratamento e controle.

## Análises realizadas

O notebook está organizado em três etapas principais:

1. **Comparação de propensity scores**
   - comparação entre duas definições oficiais de *propensity score* disponibilizadas pelo IFPRI;
   - comparação dos escores oficiais com o *propensity score* estimado a partir da especificação utilizada em aula;
   - análise das correlações e dos gráficos de dispersão.

2. **IPW com Gradient Boosting**
   - estimação do *propensity score* com `GradientBoostingClassifier`;
   - estimação com e sem calibração das probabilidades;
   - cálculo do efeito médio do tratamento por *Inverse Probability Weighting* (IPW);
   - diagnóstico da influência de probabilidades extremas sobre os pesos.

3. **Balanceamento das covariáveis**
   - pareamento 1:1 pelo *propensity score*;
   - cálculo das diferenças médias padronizadas (SMD);
   - construção de *Love Plot*;
   - comparação do balanceamento obtido por pareamento e IPW.

## Arquivos

- `Avaliação de Políticas Públicas com Dados - Tarefa 3.ipynb` — notebook com a resolução da atividade;
- `aula03_completo.csv` — base de dados utilizada na análise;
- `pscores_completo.csv` — base contendo os *propensity scores* oficiais utilizados para comparação.

## Principais bibliotecas

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

## Observação

O notebook foi desenvolvido em Python no Google Colab e contém os códigos, resultados, gráficos e interpretações utilizados na resolução da atividade.