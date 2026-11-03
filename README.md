# Tech Challenge Fase 1 — Case E-commerce Olist

**Pós Tech Data Analytics — FIAP**
**Aluno:** Caio Henrique F. de J. Sousa

Relatório executivo sobre o desempenho comercial, a logística e a satisfação dos clientes da Olist, feito a partir do [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce).

## Entregáveis

| Entregável | Onde está |
|---|---|
| Notebook com toda a análise (Python) | [`notebooks/tech_challenge_olist.ipynb`](notebooks/tech_challenge_olist.ipynb) |
| Slides da apresentação executiva | [`Olist — Tech Challenge Fase 1.pptx`](Olist%20%E2%80%94%20Tech%20Challenge%20Fase%201.pptx) |
| Vídeo da apresentação (até 5 min) | [`TechChallengeFase1-Caio Henrique.mp4`](TechChallengeFase1-Caio%20Henrique.mp4) |
| Dados utilizados | pasta [`data/externos/`](data/externos/) |

## Estrutura da pasta

```
tech-challeng/
├── data/externos/        # CSVs da Olist usados (Kaggle) + população por UF 2018 (IBGE)
├── notebooks/            # notebook com a análise completa
├── Olist — Tech Challenge Fase 1.pptx
├── TechChallengeFase1-Caio Henrique.mp4
└── README.md
```

## Principais resultados

- **Crescimento:** de jan a ago, as vendas foram de R$ 3,0 mi (2017) para R$ 7,2 mi (2018), +141%. O crescimento veio do número de pedidos; o ticket médio ficou parado em cerca de R$ 137. Em 2018 as vendas estabilizaram perto de R$ 0,9 mi por mês.
- **Oportunidade:** o Nordeste tem 27% da população, mas só 9% dos pedidos (16 pedidos por 100 mil habitantes, contra 75 no Sudeste).
- **Entrega:** o pedido leva 12 dias em média e a Olist promete 23. Mesmo assim, 6,8% atrasam, com picos de 12% na Black Friday 2017 e 19% em março de 2018. No Nordeste o atraso é de 12,8%.
- **Satisfação:** pedido no prazo recebe nota média 4,3; pedido atrasado, 2,3.
- **Recompra:** só 3% dos clientes compraram mais de uma vez.
- **Projeção:** cerca de R$ 4,2 mi de set a dez/2018, com novembro perto de R$ 1,4 mi (erro médio de 7% no teste).

## Recomendações

1. Reforçar a logística antes da Black Friday.
2. Prazo máximo de postagem para vendedores e ranking de pontualidade.
3. Melhorar a entrega no Nordeste antes de investir em marketing na região.
4. Campanha de segunda compra, com cupom enviado após a entrega.

## Dados e decisões de tratamento

- **Base completa:** 99.441 pedidos (set/2016 a out/2018).
- **Base analisada:** 96.211 pedidos entregues entre jan/2017 e ago/2018.
  - Pedidos cancelados ou não entregues ficaram de fora (cerca de 3%), porque não geram receita nem têm data de entrega.
  - 2016 e set–out/2018 ficaram de fora porque têm pouquíssimos pedidos (o dataset foi cortado nessas pontas).
- **Receita** = soma do preço dos produtos, sem frete (valor vendido na plataforma).
- Itens somados por pedido antes dos joins, para não duplicar a receita; uma avaliação por pedido (a mais recente); cliente identificado pelo `customer_unique_id`.
- **Dado externo:** estimativa de população por UF de 2018 (IBGE), usada para medir a penetração por região.
- O arquivo `olist_geolocation_dataset.csv` não foi incluído no repositório por ser grande (61 MB) e não ser usado na análise.

Todas as decisões estão explicadas e testadas passo a passo nas seções 3 e 4 do notebook.

## Como rodar

1. Instale as bibliotecas:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy jupyter
   ```
2. Abra o notebook a partir da pasta `notebooks`:
   ```bash
   jupyter notebook notebooks/tech_challenge_olist.ipynb
   ```
3. Rode todas as células em ordem (**Kernel → Restart & Run All**).

## Fontes

- [Brazilian E-Commerce Public Dataset by Olist (Kaggle)](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- IBGE — estimativa de população por UF, 2018
