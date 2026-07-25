# Avaliação do Programa Farmácia Popular: uma aplicação de inferência causal com os microdados da PNS 2019

Este repositório contém o notebook desenvolvido para a disciplina **Avaliação de Políticas Públicas com Dados**, do **Mestrado Profissional em Ciência de Dados e Inteligência Artificial** do Instituto Brasileiro de Ensino, Desenvolvimento e Pesquisa (IDP).

O trabalho aplica conceitos de inferência causal ao **Programa Farmácia Popular**, utilizando os microdados da **Pesquisa Nacional de Saúde (PNS 2019)**.

---

## Objetivo

O objetivo deste trabalho é aplicar os principais conceitos de inferência causal em um cenário distinto daquele utilizado em sala de aula (Bolsa Família), conforme proposto na atividade da disciplina.

Para isso, foi analisado o Programa Farmácia Popular, buscando responder à seguinte questão de pesquisa:

> **Qual é o efeito da obtenção de medicamentos pelo Programa Farmácia Popular sobre a adesão medicamentosa entre indivíduos com hipertensão arterial?**

---

## Conteúdo do notebook

O notebook contempla as seguintes etapas:

- leitura automatizada dos microdados da PNS 2019;
- interpretação automática do layout SAS da pesquisa;
- construção da base analítica;
- recodificação das variáveis;
- estatísticas descritivas;
- definição da população de estudo;
- formulação dos resultados potenciais;
- definição do estimando causal (ATT);
- construção da história causal;
- elaboração do Directed Acyclic Graph (DAG);
- aplicação do critério de backdoor.

---

## Estrutura do projeto

```
Avaliação do Programa Farmácia Popular/
│
├── Tarefa_1_Políticas_Públicas_com_Dados.ipynb
├── dicionario_PNS_microdados_2019.xls
├── input_PNS_2019.sas
├── input_PNS_2019.txt
└── README.md
```

---

## Dados necessários

Este trabalho utiliza os microdados públicos da **Pesquisa Nacional de Saúde (PNS 2019)**, disponibilizados pelo **Instituto Brasileiro de Geografia e Estatística (IBGE)**.

Os microdados **não acompanham este repositório**, pois o arquivo possui aproximadamente **445 MB**, ultrapassando o limite de tamanho permitido para arquivos individuais no GitHub.

### Como obter os dados

Na data de elaboração deste trabalho (julho de 2026), os microdados estavam disponíveis em:

https://ftp.ibge.gov.br/PNS/2019/Microdados/

A documentação da pesquisa estava disponível em:

https://ftp.ibge.gov.br/PNS/2019/Microdados/Documentacao/

Como endereços eletrônicos podem ser alterados ao longo do tempo, caso os links acima não estejam disponíveis recomenda-se acessar o portal oficial do IBGE e pesquisar por:

> **Microdados PNS 2019**

Após o download:

1. extraia o arquivo compactado;
2. copie o arquivo `PNS_2019.txt` para a mesma pasta do notebook;
3. mantenha também os arquivos `input_PNS_2019.txt` e `input_PNS_2019.sas`;
4. execute normalmente o notebook.

O notebook realiza automaticamente a verificação da existência dos microdados e informa ao usuário caso o arquivo não seja encontrado.

---

## Variáveis utilizadas

As principais variáveis empregadas na análise foram:

| Variável | Código PNS |
|----------|------------|
| Unidade da Federação | V0001 |
| Estrato amostral | V0024 |
| Unidade Primária de Amostragem | UPA_PNS |
| Número do domicílio | V0006_PNS |
| Sexo | C006 |
| Idade | C008 |
| Cor ou raça | C009 |
| Diagnóstico de hipertensão | Q00201 |
| Prescrição de medicamento | Q00503 |
| Uso do medicamento | Q00601 |
| Obtenção pelo Farmácia Popular | Q00801 |
| Última consulta médica | Q01101 |
| Peso amostral | V00291 |
| Escolaridade | VDD004A |
| Renda domiciliar per capita | VDF003 |

---

## Tecnologias utilizadas

- Python 3
- Google Colab
- pandas
- NumPy
- matplotlib
- NetworkX

---

## Reprodutibilidade

O notebook foi desenvolvido buscando garantir a reprodutibilidade da análise.

Para isso:

- as posições das variáveis são obtidas automaticamente a partir do layout oficial da PNS;
- não há posições codificadas manualmente;
- o notebook verifica automaticamente a existência dos microdados antes da leitura;
- todas as etapas da construção da base de dados são documentadas.

---

## Limitações

A análise apresentada possui caráter didático e foi desenvolvida para fins acadêmicos.

Embora utilize microdados oficiais da PNS 2019, algumas variáveis conceituais necessárias ao modelo causal (como gravidade prévia da doença e acesso geográfico ao Programa Farmácia Popular) não estão diretamente observadas na pesquisa, sendo representadas de forma conceitual no Directed Acyclic Graph (DAG).

---

## Autor

**Rafael Carvalho**

Mestrado Profissional em Ciência de Dados e Inteligência Artificial

Instituto Brasileiro de Ensino, Desenvolvimento e Pesquisa (IDP)

Brasília – DF

2026