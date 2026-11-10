# 📊 Análise Exploratória e Limpeza de Dados de E-commerce (Online Retail)

Este repositório contém um projeto completo de **Análise Exploratória de Dados (EDA)**, **Limpeza e Tratamento de Dados (Data Cleaning)** e **Visualização de Negócios** aplicado a um conjunto de dados real de transações de um grande e-commerce multinacional sediado no Reino Unido.

---

## 🎯 Objetivos do Projeto

1. **Diagnóstico da Base Bruta:** Identificar problemas estruturais, valores ausentes, duplicatas e inconsistências.
2. **Investigação de Anomalias (EDA):**
   - Entender o comportamento de cancelamentos e estornos (prefixo `C`).
   - Investigar transações com quantidades negativas sem cancelamento (descobertas como baixas operacionais de estoque com preço zero).
   - Analisar inconsistências de catálogo (produtos com múltiplas descrições e divergências de digitação).
3. **Pipeline de Limpeza e Preparação:** Construir regras justificadas de negócio para filtrar sujeiras sem descartar receita legítima.
4. **Análise de Performance e Negócios:** Calcular faturamento real, ticket médio, sazonalidade temporal, produtos líderes de vendas e distribuição geográfica.

---

## 📁 Estrutura do Repositório

```text
analise-ecommerce/
│
├── data/
│   └── online-retail.xlsx          # Dataset original (541.909 transações)
│
├── notebooks/
│   └── analise_vendas.ipynb        # Notebook principal estruturado e executado
│
├── .gitignore                      # Arquivos e diretórios ignorados pelo Git
└── README.md                       # Documentação completa do projeto
```

---

## 🔍 Principais Descobertas e Decisões de Limpeza

| Problema Identificado | Volume Encontrado | Decisão e Justificativa |
|---|:---:|---|
| **Duplicatas Exatas** | 5.268 linhas | Removidas para evitar contagem dupla de itens e receita. |
| **Descrições Ausentes (`NaN`)** | 1.454 linhas | 100% tinham preço zero (`UnitPrice == 0.0`) e nenhuma identificação de cliente. Eram ajustes de estoque e foram excluídas do conjunto de vendas. |
| **Cancelamentos (`InvoiceNo` com 'C')** | 9.288 linhas | Separados em um DataFrame dedicado (`df_cancelamentos`), representando estornos de £ 896.812,49. |
| **Quantidades ou Preços Negativos/Zero** | 1.336 linhas | Descartadas por se tratarem de baixas operacionais (avarias, perdas, amostras), mantendo apenas transações válidas (`Quantity > 0` e `UnitPrice > 0`). |

> **Resultado do Pipeline:** A base foi limpa de 541.909 para **392.732 transações comerciais legítimas**, preservando 100% das vendas reais com faturamento comprovado.

---

## 📈 Métricas de Negócio Encontradas

* **Faturamento Total Líquido:** **£ 8.911.407,90**
* **Total de Pedidos Comerciais Únicos:** **19.960 pedidos**
* **Total de Produtos Distintos Vendidos:** **3.877 itens**
* **Ticket Médio por Pedido:** **£ 446,46**

### Insights Comerciais:
1. **Sazonalidade e Black Friday:** O faturamento cresceu intensamente no segundo semestre de 2011, atingindo o pico histórico em **novembro de 2011 (£ 1,51 milhão)** impulsionado pelas vendas natalinas e Black Friday.
2. **Concentração no Reino Unido:** O Reino Unido responde por mais de 80% da receita total, seguido por mercados internacionais relevantes como **Holanda**, **Irlanda (EIRE)**, **Alemanha** e **França**.
3. **Mix de Produtos:** Artigos utilitários, presentes e papelaria com ticket acessível dominam o topo de vendas em quantidade física (como sacolas decoradas e canecas).

---

## 🛠️ Tecnologias Utilizadas

* **Python 3**
* **Pandas** (Tratamento, agregação e manipulação de DataFrames)
* **Matplotlib** & **Seaborn** (Visualização de dados e gráficos executivos)
* **Jupyter Notebook** (Documentação interativa e narrativa analítica)

---

## 🚀 Como Executar o Projeto

1. Clone o repositório ou baixe os arquivos:
   ```bash
   git clone https://github.com/SEU_USUARIO/analise-ecommerce.git
   cd analise-ecommerce
   ```
2. Crie e ative um ambiente virtual:
   ```bash
   python -m venv .venv
   # No Windows:
   .venv\Scripts\activate
   # No Linux/Mac:
   source .venv/bin/activate
   ```
3. Instale as dependências:
   ```bash
   pip install pandas openpyxl matplotlib seaborn notebook
   ```
4. Abra o notebook no Jupyter:
   ```bash
   jupyter notebook notebooks/analise_vendas.ipynb
   ```

---

*Desenvolvido por **Vitor Emanuel** como projeto de Análise Exploratória e Qualidade de Dados.*
