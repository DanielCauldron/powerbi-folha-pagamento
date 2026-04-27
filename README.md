# 📊 Resumo da Folha de Pagamento — Power BI

<img width="1913" height="802" alt="pagamento" src="https://github.com/user-attachments/assets/75c72136-d87e-43b8-8799-9f8f843ec9e8" />


Dashboard desenvolvido para análise e acompanhamento de folha de pagamento, com foco em indicadores de RH e gestão de custos por centro de custo e cargo.

---

## 🎯 Objetivo

Centralizar as principais métricas de folha de pagamento em um painel interativo, permitindo a visualização de salários, bônus, comissões e descontos de forma clara e segmentada por área e cargo.

---

## 📌 Indicadores (KPIs)

| Métrica | Descrição |
|---|---|
| Head Count | Total de funcionários ativos |
| Salário Bruto | Soma de salário base + bônus + comissão |
| Valor de Bônus | Calculado sobre % de bônus por funcionário |
| Valor de Comissão | Calculado sobre % de comissão por funcionário |
| Salário Líquido | Salário bruto deduzido dos descontos |
| Valor de Desconto | Total de descontos aplicados |

---

## 🗂️ Modelagem de Dados

Modelo no formato **Star Schema** com 3 tabelas:

- **FOLHA_PGTO** — tabela fato com dados de salário, bônus, comissão e descontos
- **CARGO** — dimensão com código e nome do cargo
- **CENTRO_CUSTO** — dimensão com código e nome do centro de custo

---

## ⚙️ Medidas DAX

```dax
VALOR BONUS =
  SUMX(FOLHA_PGTO, FOLHA_PGTO[SALARIO] * (FOLHA_PGTO[PCT BONUS] / 100))

VALOR COMISSAO =
  SUMX(FOLHA_PGTO, FOLHA_PGTO[SALARIO] * (FOLHA_PGTO[PCT COMISSAO] / 100))

SALARIO BRUTO =
  SUM(FOLHA_PGTO[SALARIO]) + [VALOR BONUS] + [VALOR COMISSAO]

SALARIO LIQUIDO =
  [SALARIO BRUTO] - SUM(FOLHA_PGTO[DESCONTOS])
```

---

## 🛠️ Ferramentas

- Power BI Desktop
- Power Query (ETL e tratamento de nulos)
- DAX (medidas calculadas)
- Excel (fonte de dados)

---

## 📁 Arquivos

| Arquivo | Descrição |
|---|---|
| `Dax_exercicio_01.pbix` | Arquivo Power BI com o dashboard completo |
| `003_FOLHA.xlsx` | Base de dados utilizada no projeto |

---

## 👤 Autor

Desenvolvido por **Daniel Caldeirão**

🔗 [LinkedIn](https://www.linkedin.com/in/daniel-caldeirao) · 📧 [dfcaldeirao@gmail.com](mailto:dfcaldeirao@gmail.com)
