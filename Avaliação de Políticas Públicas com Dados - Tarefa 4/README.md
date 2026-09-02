# Avaliação de Políticas Públicas com Dados — Tarefa 4

## Mestrado em Ciência de Dados e Inteligência Artificial no Setor Público

Este repositório contém a resolução da **Tarefa 4** da disciplina **Avaliação de Políticas Públicas com Dados**, desenvolvida no contexto do Mestrado Profissional em Ciência de Dados e Inteligência Artificial aplicado ao Setor Público.

A atividade tem como foco a aplicação do método de **Diferenças em Diferenças (Difference-in-Differences — DiD)** para avaliação de impacto de políticas públicas.

---

## Objetivo

O objetivo da tarefa é aplicar e interpretar o estimador de Diferenças em Diferenças utilizando dados em dois períodos, 2005 e 2009, considerando diferentes grupos de comparação e análises de robustez.

A atividade contempla quatro etapas:

1. Estimação manual do DiD canônico entre **T1 e C1** para três desfechos;
2. Confirmação das estimativas por meio de regressão;
3. Realização de teste placebo entre **C1 e C2**;
4. Reestimação do DiD utilizando apenas domicílios com **painel completo**, presentes em 2005 e 2009.

---

## Arquivos

- `aula04_painel.csv`  
  Base de dados utilizada na análise.

- `Avaliação_de_Políticas_Públicas_Tarefa_4.ipynb`  
  Notebook contendo preparação dos dados, cálculos, regressões e interpretações.

---

## Desfechos analisados

Foram utilizados três indicadores de resultado:

- `attend_med`: indicador médio de frequência escolar;
- `dropout_med`: indicador médio de abandono escolar;
- `grade_now_med`: série/ano escolar médio observado.

Os grupos utilizados foram:

- **T1**: grupo tratado;
- **C1**: grupo de controle principal;
- **C2**: grupo de comparação utilizado no teste placebo.

---

## 1. DiD canônico — T1 vs C1

O estimador de Diferenças em Diferenças foi calculado por:

\[
\widehat{\delta}_{DiD}
=
(\bar{Y}_{T1,2009} - \bar{Y}_{T1,2005})
-
(\bar{Y}_{C1,2009} - \bar{Y}_{C1,2005})
\]

Os resultados obtidos foram:

| Desfecho | DiD |
|---|---:|
| `attend_med` | 0,0089 |
| `dropout_med` | -0,0080 |
| `grade_now_med` | 0,1527 |

---

## 2. Confirmação por regressão

O DiD também foi estimado por meio da especificação:

\[
Y_{it}
=
\beta_0
+
\beta_1 Tratado_i
+
\beta_2 Pós_t
+
\beta_3(Tratado_i \times Pós_t)
+
\varepsilon_{it}
\]

O coeficiente da interação `tratado:pos` reproduziu exatamente os valores obtidos pelo cálculo manual.

Os erros-padrão foram clusterizados por domicílio (`cod_dtm`), considerando a dependência entre observações de uma mesma unidade ao longo do tempo.

| Desfecho | Coeficiente DiD | Erro-padrão | p-valor |
|---|---:|---:|---:|
| `attend_med` | 0,0089 | 0,0107 | 0,4067 |
| `dropout_med` | -0,0080 | 0,0094 | 0,3933 |
| `grade_now_med` | 0,1527 | 0,1038 | 0,1413 |

Nenhum dos três coeficientes apresentou significância estatística ao nível de 5%.

---

## 3. Teste placebo — C1 vs C2

Como verificação adicional, foi estimado um DiD placebo entre dois grupos não tratados, considerando **C1 como pseudo-tratado** e **C2 como controle**.

| Desfecho | DiD placebo | Erro-padrão | p-valor |
|---|---:|---:|---:|
| `attend_med` | -0,0010 | 0,0103 | 0,9238 |
| `dropout_med` | 0,0086 | 0,0090 | 0,3414 |
| `grade_now_med` | 0,0219 | 0,0992 | 0,8255 |

Os coeficientes foram pequenos e estatisticamente indistinguíveis de zero, não indicando resultado placebo especialmente suspeito.

---

## 4. Painel completo

A análise foi repetida utilizando somente os domicílios observados tanto em 2005 quanto em 2009.

Foram identificados:

- **6.831 domicílios** com painel completo;
- **13.662 observações**.

Os resultados foram:

| Desfecho | DiD original | DiD painel completo | Diferença |
|---|---:|---:|---:|
| `attend_med` | 0,0089 | 0,0062 | -0,0027 |
| `dropout_med` | -0,0080 | -0,0060 | 0,0020 |
| `grade_now_med` | 0,1527 | -0,1741 | -0,3268 |

Os resultados de `attend_med` e `dropout_med` permaneceram próximos aos encontrados na amostra original.

Por outro lado, `grade_now_med` apresentou alteração substancial, inclusive com inversão do sinal do coeficiente, indicando maior sensibilidade desse desfecho à composição da amostra.

---

## Principais conclusões

A atividade evidenciou três aspectos importantes da aplicação do método de Diferenças em Diferenças:

- o cálculo manual do DiD é equivalente ao coeficiente de interação obtido pela regressão;
- o teste placebo não indicou diferenças temporais relevantes entre C1 e C2 para os desfechos analisados;
- a análise com painel completo mostrou que os resultados de `attend_med` e `dropout_med` são relativamente estáveis, enquanto `grade_now_med` é mais sensível à composição da amostra.

A análise com painel completo deve ser entendida como uma verificação de robustez, e não necessariamente como uma especificação superior, pois a permanência dos domicílios nas duas ondas também pode estar associada a características específicas das unidades observadas.

---

## Tecnologias utilizadas

- Python
- pandas
- NumPy
- statsmodels
- Google Colab / Jupyter Notebook