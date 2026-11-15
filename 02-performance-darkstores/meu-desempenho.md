# Meu Desempenho

Funcionalidade do dashboard que permite ao operador de darkstore consultar sua própria performance, sem precisar de acesso administrativo ao sistema.

---

## O que o operador vê

- **Total de pedidos** processados no período consultado
- **Taxa de SLA** — % de pedidos entregues dentro do prazo
- **Tempo médio de ciclo** em minutos por pedido
- **Pedidos com ruptura** — pedidos em que algum item ficou sem estoque

---

## Como funciona

1. Operador acessa o dashboard e digita o próprio nome
2. Backend busca na view `darkstore.pedidos_lojinhas` usando `UPPER(TRIM(operador)) = UPPER(@nome)` para tolerar variações de digitação
3. Resultado retorna agregado por período: total_pedidos, taxa_sla, avg_cycle_min, pedidos_com_ruptura

---

## Destaques

**Sem login individual** — o operador não precisa de conta própria. A busca por nome é simples e acessível de qualquer terminal da loja.

**Histórico disponível** — o operador pode consultar desempenho de períodos anteriores, não apenas do turno atual.

---

## Stack

Vue.js · Node.js · BigQuery · Cloud Run
