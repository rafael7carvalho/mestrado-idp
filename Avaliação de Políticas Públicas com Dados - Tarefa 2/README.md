# Avaliação de Políticas Públicas com Dados — Tarefa 2

Este diretório contém a resolução de exercício desenvolvido na disciplina **Avaliação de Políticas Públicas com Dados**, do **Mestrado Profissional em Ciência de Dados e Inteligência Artificial** do Instituto Brasileiro de Ensino, Desenvolvimento e Pesquisa (IDP).

O exercício utiliza a base `progresa_completo.csv` para analisar o efeito do **PROGRESA** sobre uma variável de resultado educacional e realizar uma análise de poder estatístico.

---

## Objetivo

O exercício possui três objetivos principais:

1. estimar o efeito do PROGRESA sobre uma variável de resultado diferente da utilizada originalmente em aula;
2. avaliar o balanceamento entre os grupos de tratamento e controle no novo recorte da amostra;
3. calcular o tamanho amostral necessário para detectar um efeito padronizado de **0,10σ**, com **poder estatístico de 90%**.

Como variável de resultado, foi utilizada a **série escolar (`grc`)**.

---

## Estrutura da análise

O notebook foi organizado nas seguintes etapas:

1. **Importação das bibliotecas**
2. **Leitura e inspeção da base**
3. **Exploração das variáveis de interesse**
4. **Definição do tratamento e da elegibilidade**
5. **Construção da amostra de linha de base**
6. **Tabela de balanceamento**
7. **Estimação do efeito do PROGRESA sobre a série escolar (`grc`)**
8. **Cálculo do tamanho amostral para poder estatístico de 90%**
9. **Análise de poder considerando a proporção observada entre tratamento e controle**

---

## Dados

A análise utiliza o arquivo:

`progresa_completo.csv`

A base contém informações relacionadas à avaliação do programa PROGRESA e é utilizada no notebook para construir os grupos de tratamento e controle, definir a amostra analítica e estimar o efeito sobre a variável educacional selecionada.

---

## Principais resultados

### Balanceamento

A tabela de balanceamento compara características observáveis dos grupos de tratamento e controle na linha de base de 1997.

Foram analisadas características como idade, sexo, condição indígena, escolaridade e idade do chefe do domicílio, rendimento mensal do chefe do domicílio e índice de bem-estar.

Algumas dessas características apresentaram diferenças estatisticamente significativas entre os grupos, indicando que a interpretação de comparações simples de médias requer cautela.

### Efeito sobre a série escolar

Para a variável de resultado `grc`, a diferença estimada entre os grupos em 1998 foi de aproximadamente:

- **Efeito estimado:** 0,0106
- **Erro-padrão:** 0,0290
- **p-valor:** 0,7159
- **IC 95%:** [-0,0463; 0,0674]

Nesta especificação, não foi encontrada evidência estatística de diferença entre os grupos de tratamento e controle para a série escolar.

### Análise de poder

Utilizando `statsmodels`, foi calculado o tamanho amostral necessário para detectar um efeito padronizado de **0,10σ**, considerando nível de significância de **5%** e poder estatístico de **90%**.

Sob uma alocação equilibrada entre tratamento e controle, seriam necessárias aproximadamente:

- **2.103 observações por grupo**
- **4.206 observações no total**

Considerando a proporção efetivamente observada na amostra, de aproximadamente **1,63 tratado para cada controle**, seriam necessárias aproximadamente:

- **1.696 observações no grupo de controle**
- **2.769 observações no grupo de tratamento**
- **4.465 observações no total**

A amostra utilizada na análise contém **27.432 observações**, número superior ao tamanho amostral calculado para detectar um efeito padronizado de 0,10σ nas condições estabelecidas.

---

## Tecnologias utilizadas

A análise foi desenvolvida em **Python**, utilizando principalmente:

- `pandas` — manipulação e análise dos dados;
- `numpy` — operações numéricas;
- `scipy` — testes estatísticos;
- `statsmodels` — análise de poder e cálculo do tamanho amostral.

O notebook foi desenvolvido e executado em ambiente **Jupyter/Google Colab**.

---

## Arquivos

```text
Avaliação de Políticas Públicas com Dados - Tarefa 2/
│
├── Análise_de_Políticas_Públicas_com_Dados_Tarefa_2.ipynb
├── progresa_completo.csv
└── README.md
```

- **`Análise_de_Políticas_Públicas_com_Dados_Tarefa_2.ipynb`**: notebook contendo os códigos, resultados e interpretações da análise.
- **`progresa_completo.csv`**: base de dados utilizada no exercício.
- **`README.md`**: documentação do projeto.

---

## Reprodutibilidade

Para reproduzir a análise, mantenha o arquivo `progresa_completo.csv` no mesmo diretório do notebook e execute as células sequencialmente.

As principais dependências são:

```python
import numpy as np
import pandas as pd

from scipy import stats
from statsmodels.stats.power import TTestIndPower
```

---

## Observação metodológica

Os resultados devem ser interpretados no contexto específico do recorte e da estratégia analítica utilizados no exercício. Em particular, a ausência de significância estatística na estimativa para `grc` não equivale à demonstração de ausência de efeito do programa.

Da mesma forma, o cálculo de poder apresentado refere-se especificamente à capacidade de detectar um efeito padronizado de **0,10σ**, considerando nível de significância de 5% e poder de 90%.

---

## Autor

**Rafael Carvalho**  
Mestrado Profissional em Ciência de Dados e Inteligência Artificial  
Instituto Brasileiro de Ensino, Desenvolvimento e Pesquisa (IDP)