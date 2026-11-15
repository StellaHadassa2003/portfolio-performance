# Dashboard Intraday

Dashboard web em tempo real acessado pelos coordenadores das darkstores durante o turno. Mostra o andamento dos pedidos, SLA, produtividade e rupturas da operação em curso — sem esperar o fechamento do dia.

---

## O que exibe

- **Pedidos em andamento** — pedidos abertos por loja e status (picking, packing, expedição)
- **SLA em tempo real** — % de pedidos dentro do SLA e tempo médio de ciclo por loja
- **Produtividade por turno** — itens processados por hora, comparativo com o objetivo do turno
- **Rupturas** — SKUs com ruptura identificados no ciclo atual, agrupados por loja
- **Ranking de operadores** — posição dos operadores no turno atual por produtividade

---

## Arquitetura

```
BigQuery (dados operacionais)
    ↓ consulta a cada N minutos
    ↓ Node.js backend (Cloud Run)
    ↓ Vue.js frontend (Firebase Hosting)
    → dashboard no navegador do coordenador
```

O backend mapeia store_codes para fulfillment_center_ids e consulta as fontes brutas diretamente — os dados do dashboard intraday são ao vivo, não passam pelo pipeline semanal.

---

## Acesso

Autenticação via Google OAuth2 — apenas usuários com e-mail corporativo Shopper acessam o dashboard.

---

## Stack

Vue.js · Node.js · BigQuery · Google OAuth2 · Firebase Hosting · Cloud Run
