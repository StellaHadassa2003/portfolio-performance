# Agente de Feedback Individual por IA

Cada colaborador recebe uma mensagem personalizada gerada por LLM ao consultar seu resultado no totem. A IA recebe contexto estruturado (pontuação, atividades, erros, histórico, posição no ranking) e gera um feedback em texto natural.

**Modelo:** Gemini 2.5 Flash · **Formato de saída:** JSON com dois campos

---

## Campos gerados

**Resumo** (máx. 2 frases) — situação geral: gap para a meta em pontos e itens, motivo de desqualificação, ou celebração se top 1.

**Detalhe** (máx. 3 frases) — atividades realizadas, impacto dos erros em pontos e reais, o que fazer para melhorar ou manter.

---

## Perfis com prompts distintos

| Perfil | Tom e foco |
|---|---|
| Top 1 do FC | Celebração máxima, desafio de manter o recorde |
| Bonificado acima de 1.4M | Parabenizar, apontar gap para o top 1 em itens concretos |
| Bonificado padrão (≥1M) | Parabenizar, próxima meta é 1.5M |
| Elegível próximo (≥700k) | Urgência positiva — faltam X itens específicos, está perto |
| Elegível distante (<700k) | Honesto sobre a distância, exige esforço consistente |
| Desqualificado | Firme sobre o motivo; analisa se a bonificação estava ao alcance mesmo sem a desqualificação |
| Fiscal | Foco no resultado da equipe: % bonificados, classificação EXCELENTE / PODE MELHORAR / PRECISA DE ATENÇÃO / PREOCUPANTE |
| Supervisor | Split entre ausências e erros operacionais nos desqualificados, ações recomendadas por tipo |
| Intraday | Foco no que falta no ciclo atual em andamento, não no histórico |

---

## Destaques técnicos

**Gap em itens concretos** — o agente não diz "faltam 150.000 pontos". Calcula quantos itens da atividade principal do colaborador equivalem a esse gap e diz "faltam ~42 pedidos mapeados".

**Impacto financeiro dos erros** — para colaboradores elegíveis que perderam pontos por erros, o agente calcula a diferença em reais de bonificação e inclui no detalhe: "erros custaram R$ 23,00 em bonificação".

**Análise do gap pós-desqualificação** — para desqualificados, o agente verifica se a bonificação estava ao alcance mesmo sem o erro: "mesmo sem a desqualificação, faltariam mais 38 pedidos para atingir 1 Milhão — bonificação não estava garantida."

**Classificação da equipe** — para fiscais, o % de bonificados da equipe determina o tom da mensagem automaticamente, com vocabulário padronizado por faixa.

---

## Regras absolutas do prompt

- Nunca inventar ou alterar números — usar apenas os dados fornecidos no contexto
- Nunca inventar sobrenome — apenas o primeiro nome
- Zero emojis
- Português do Brasil, tom direto e humano, sem corporativês
- Se a pontuação média da equipe estiver abaixo de 600K, o alerta aparece obrigatoriamente no detalhe

---

## Stack

Node.js · Gemini 2.5 Flash API · BigQuery
