# Pipeline de Dados — Dataform + BigQuery

Pipeline semanal com 13 jobs em SQL que processa todas as fontes de dados operacionais dos FCs e calcula a pontuação individual de cada colaborador.

---

## Atividades cobertas

Picking · Packing · Recebimento Fresh e Mercearia · Reposição · Expedição · Pré-Expedição · Fracionamento · Gestão de Estoque · Assiduidade · Fiscais · Supervisores

---

## Fluxo dos jobs

```
Fontes brutas (Sheets, APIs externas, BigQuery nativo)
    ↓ Job 00 — KPIs operacionais da semana por setor
    ↓ Job 01 — Extração de pontos individuais (metric codes por atividade)
    ↓ Job 02 — Score consolidado com multiplicadores e penalidades
    ↓ Job 03 — Ranking semanal com posição, status e valor de bonificação
    ↓ Job 04 — Performance de liderança (fiscais e supervisores)
    ↓ Job 05 — Performance de não-mensuráveis
    ↓ Jobs 06–13 — Feedbacks operacionais, comparativos, ocorrências
    → performance_detalhada (tabela final de consumo)
```

---

## Destaques técnicos

**Metric codes** — cada atividade tem um código de métrica que define como os pontos são calculados: por item processado, por lote, por pedido, com pesos e multiplicadores distintos por setor e turno.

**Multiplicadores de bonificação** — a pontuação final aplica multiplicadores por desempenho relativo (posição no ranking do setor) e penalidades por erros operacionais, zeramento por ocorrências disciplinares e descontos de equipe.

**Ambientes QA e Prod separados** — todos os jobs existem em versões `qa/` e `prod/`, com tabelas e regras de negócio específicas por ambiente. GitHub Actions valida QA antes de qualquer promoção para produção.

**Organograma histórico** — o pipeline consome o organograma semanal com histórico de admissão, desligamento e absenteísmo de cada colaborador, garantindo que a pontuação reflita apenas os dias efetivamente trabalhados.

---

## CI/CD

GitHub Actions executa o pipeline automaticamente toda semana:
1. Roda os jobs de QA
2. Valida os resultados contra checks automáticos
3. Promove para produção se aprovado

---

## Stack

BigQuery · Dataform · SQL · GitHub Actions
