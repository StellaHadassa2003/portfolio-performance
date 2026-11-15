# Pipeline de Dados — Dataform + BigQuery

Pipeline SQL que processa as fontes de dados operacionais das darkstores e calcula métricas de produtividade por operador, loja e turno.

---

## Atividades cobertas

Picking · Packing · Expedição · Gestão de Estoque · SLA de pedidos · Rupturas

---

## Fluxo dos jobs

```
Fontes brutas (pedidos, rotas, operadores, lojinhas)
    ↓ Extração de pedidos por operador com SLA e tempo de ciclo
    ↓ Consolidação de produtividade por setor, turno e semana
    ↓ Cálculo de rupturas e taxa de acerto
    → darkstore.pedidos_lojinhas (view de consumo)
    → produtividade_setor_historico (histórico consolidado)
```

---

## Destaques técnicos

**Mapeamento loja → fulfillment center** — cada store_code é mapeado para um fulfillment_center_id (pamplona, moema, pinheiros, higienópolis, vila olímpia, entre outras) e para o formato LJ usado na API de fotos.

**Produtividade consolidada** — a métrica `prod_consolidada` é calculada como `total_itens / horas_trabalhadas`, segmentada por setor, turno e semana.

**SLA e tempo de ciclo** — pedidos com tempo fora do SLA são identificados e vinculados ao operador responsável, gerando `taxa_sla` e `avg_cycle_min` por operador.

**Nome do operador normalizado** — o join entre pedido e operador usa `UPPER(TRIM(operador))` para contornar inconsistências de digitação no cadastro.

---

## Stack

BigQuery · Dataform · SQL · GitHub Actions
