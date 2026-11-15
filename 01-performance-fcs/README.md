# Sistema de Performance — Operação FCs

Sistema completo de acompanhamento individual de performance para os colaboradores operacionais dos quatro FCs da Shopper.

Antes deste sistema, o acompanhamento era inteiramente manual, sem rastreabilidade individual e sem canal direto para o colaborador. Hoje cada pessoa acessa sua própria performance diariamente pelo totem — com mensagens geradas por IA que explicam exatamente o que aconteceu na semana e o que precisa mudar.

---

## Componentes

| Tipo | Componente | Descrição |
|---|---|---|
| Sistema | [Pipeline Dataform](./pipeline-dataform.md) | 13 jobs SQL que processam todas as atividades e geram o ranking semanal |
| Sistema | [Totem de Feedback](./totem.md) | Aplicação touchscreen com visão diária e semanal, feedback por IA |
| Agente | [Assiduidade](./agente-assiduidade.md) | Verifica direito à bonificação via API Ahgora, bloqueia pagamento se houver divergência |
| Agente | [Alertas de Performance](./agente-alertas.md) | Identifica colaboradores em risco e direciona para coordenador |
| Agente | [Mensagens por Setor](./agente-mensagens-setor.md) | Gera mensagens de bonificação por setor com base nos KPIs da semana |
| Agente | [Feedback Individual por IA](./agente-feedback-ia.md) | Gera feedback personalizado por colaborador via Gemini 2.5 Flash |
| Automação | [Scripts de Carteira e Ranking](./automacoes.md) | Exporta rankings, preenche planilha de pagamento, gera PDFs |

---

## Impacto

| Métrica | Antes | Depois |
|---|---|---|
| Rastreabilidade individual | Manual / inexistente | 74 mil feedbacks processados |
| Picking (itens/hora) | 29 | 89 (+203%) |
| Packing (itens/hora) | 25 | 79 (+217%) |
| Fracionamento (itens/hora) | 6 | 24 (+284%) |
| Recebimento (itens/hora) | 247 | 454 (+84%) |
| Colaboradores com bonificação rastreável | 0 | 23.277 registros |
| Canal de consulta para o colaborador | Nenhum | Totem diário + semanal |
| Mensagens de feedback | Manuais / inexistentes | Geradas por IA por colaborador |

---

## Repositórios

| Componente | Repositório |
|---|---|
| Pipeline e agentes | `performance-dataform` (privado) |
| Totem (backend + frontend) | `performance-totem-feedback` (privado) |
