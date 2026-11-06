# Perfil Exportador do Brasil (1995–hoje)

>  **Projeto em andamento.** Este README é atualizado a cada etapa concluída.

O Brasil deixou de ser um exportador de produtos industriais para se tornar um exportador de commodities? Este projeto investiga, com dados públicos de comércio exterior, como a pauta exportadora brasileira mudou desde 1995. Todo o processo é feito com SQL Server, Python e Power BI.

---

##  Perguntas de pesquisa

1. Como evoluiu a participação de **produtos básicos (commodities)** e de **produtos industrializados** no total exportado pelo Brasil?
2. Em que período a mudança se intensificou?
3. A diferença na composição da pauta entre o início e o fim da série é **estatisticamente significativa**?
4. Quais fatores se associam ao aumento do peso das commodities, como câmbio, preços internacionais e demanda de grandes parceiros comerciais?
5. Como a concentração em **produtos** e em **destinos** (por exemplo, a China) mudou ao longo do tempo?

---

##  Status das etapas

| # | Etapa | Ferramentas | Status |
|---|-------|-------------|--------|
| 1 | Repositório e banco de dados `perfil` | Git, SQL Server | ✅ Concluída |
| 2 | Coleta dos dados de exportação | Python | ⏳ Em andamento |
| 3 | Limpeza e padronização (classificações, valores, períodos) | Python (pandas) | ◻ A fazer |
| 4 | Modelagem e carga no banco | SQL Server | ◻ A fazer |
| 5 | Consultas analíticas (participação por categoria, ranking de produtos e destinos) | SQL | ◻ A fazer |
| 6 | Análise exploratória (EDA) | Python (pandas, matplotlib/seaborn) | ◻ A fazer |
| 7 | Testes de hipótese | Python (scipy/statsmodels) | ◻ A fazer |
| 8 | Modelo de regressão | Python (statsmodels) | ◻ A fazer |
| 9 | Dashboard | Power BI, DAX | ◻ A fazer |
| 10 | Conclusões e documentação final | — | ◻ A fazer |

---

##  Fontes de dados (previstas)

| Fonte | Conteúdo | Uso no projeto |
|-------|----------|----------------|
| Comex Stat (MDIC) | Exportações brasileiras por produto, país de destino e ano | Base principal |
| Ipeadata / Banco Central | Taxa de câmbio e índices de preços | Variáveis explicativas da regressão |
| *[a definir]* | Preços internacionais de commodities | Variável explicativa da regressão |

>  **Ponto de atenção metodológico:** classificações de produtos mudam ao longo do tempo, e a série detalhada pode não cobrir o período inteiro com a mesma nomenclatura. A compatibilização entre classificações e a definição de "commodity" usada no projeto serão documentadas na etapa 3.

---

##  Arquitetura

```
Fontes públicas (Comex Stat, Ipeadata)
        │
        ▼
Python: coleta e limpeza (pandas)
        │
        ▼
SQL Server: banco "perfil" (tabelas tratadas + views analíticas)
        │
        ├──► Python: EDA, testes de hipótese e regressão
        │
        └──► Power BI: dashboard (DAX)
```

---

##  Estrutura do repositório (planejada)

```
perfil-exportador-brasil/
├── data/
│   ├── raw/            # dados brutos (não versionados se forem grandes)
│   └── processed/      # dados tratados
├── notebooks/          # EDA, testes de hipótese e regressão
├── src/                # scripts de coleta e limpeza
├── sql/                # criação de tabelas, views e consultas
├── powerbi/            # arquivo .pbix e prints do dashboard
├── docs/               # decisões metodológicas e dicionário de dados
└── README.md
```

---

##  Plano de análise estatística

- **EDA:** evolução da participação de cada categoria, distribuição dos valores, concentração de produtos e destinos (índice de Herfindahl-Hirschman).
- **Testes de hipótese:** comparar a participação das commodities entre períodos (por exemplo, antes e depois de meados dos anos 2000) e verificar se a diferença é significativa.
- **Regressão:** relacionar a participação das commodities com câmbio, preços internacionais e demanda externa, com atenção aos cuidados próprios de séries temporais (tendência e autocorrelação).

---

##  Tecnologias

`SQL Server` · `Python` · `pandas` · `scipy` · `statsmodels` · `matplotlib` · `Power BI` · `DAX` · `Git`

---

##  Sobre o projeto

Este é o terceiro projeto do meu portfólio de dados e também meu laboratório de estudos: cada etapa aplica um tema que estou aprofundando (SQL, pandas, estatística e DAX). A pergunta vem da minha formação em Ciências Sociais, e o objetivo é respondê-la com dados, e não com impressões.

**Outros projetos:**
- [Despesas Públicas Federais](https://github.com/cainaq): pipeline em SQL Server e dashboard em Power BI
- [Monitor de Indicadores Econômicos](https://github.com/cainaq): coleta automatizada via API, SQL Server, Power BI e Power Automate

---

**Cainã Queiroz Silva** · [LinkedIn](https://www.linkedin.com/in/cainaqueiroz) · [GitHub](https://github.com/cainaq)
