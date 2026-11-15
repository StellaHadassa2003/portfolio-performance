# Sistema de Performance — Darkstores

Sistema de acompanhamento de performance para as darkstores da Shopper, cobrindo mais de 25 lojas em São Paulo, Campinas, Curitiba, Brasília e Goiânia.

Antes deste sistema, as darks não tinham nenhum canal estruturado de acompanhamento individual de performance. Hoje lideranças acompanham produtividade em tempo real e colaboradores consultam seu próprio desempenho por nome.

---

## Componentes

| Tipo | Componente | Descrição |
|---|---|---|
| Sistema | [Pipeline Dataform](./pipeline-dataform.md) | Processa pedidos, calcula métricas individuais e gera rankings semanais |
| Sistema | [Dashboard Intraday](./dashboard-intraday.md) | Painel em tempo real de produtividade por colaborador para lideranças |
| Sistema | [Meu Desempenho](./meu-desempenho.md) | Visão individual do colaborador: SLA, ciclo médio, erros por pedido |
| Automação | [Scripts de Relatório e Publicação](./automacoes.md) | Gera PDFs, exporta CSVs, publica no Drive, processa carteira |

---

## Impacto

- Mais de 25 darks cobertas em 5 estados
- Lideranças com visibilidade em tempo real de produtividade individual — antes inexistente
- Colaboradores com acesso ao próprio histórico de erros por pedido
- Relatórios semanais automatizados — eliminaram compilação manual de dados

---

## Repositórios

| Componente | Repositório |
|---|---|
| Pipeline e scripts | `performance-dataform` (privado) |
| Dashboard (backend + frontend) | `performance-darkstore-dashboard` (privado) |
