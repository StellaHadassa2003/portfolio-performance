# Agente de Mensagens de Performance por Setor

Lê os KPIs dos dashboards de cada FC, interpreta a direção de cada indicador e gera automaticamente as mensagens de bonificação enviadas por setor aos colaboradores via totem.

---

## O que faz

1. Lê as abas de Resumo FC (KPIs da semana: semana anterior, semana atual, delta, meta) e a side table de configuração (setores, descontos, ideia central) de cada FC
2. Identifica quais KPIs se aplicam a cada setor
3. Determina a direção de cada indicador: melhorou / piorou / distante da meta
4. Incorpora a ideia central da semana (contexto operacional fornecido pela liderança) como fio condutor da mensagem
5. Gera a mensagem em até 3 frases, sem mencionar números ou percentuais — apenas direção qualitativa
6. Escreve na aba Mensagens da planilha e gera PDF para distribuição

---

## Casos especiais tratados

**Fiscais de picking** — colaboradores com desconto individual por vistoria têm mensagem gerada a partir da aba "Fiscais de Picking", com o texto já pronto da coluna Mensagem e multiplicador aplicado à bonificação.

**Gestão de Estoque** — colaboradores com justificativa de inventário preenchida recebem mensagem reformulada pelo agente: não atingiu mínimo de posições, não atingiu acurácia, ou recebeu detratora por baixo desempenho.

**Zeramento por erro de processo** — quando um setor inteiro tem bonificação zerada por erro operacional (ex: caixa enviada vazia por falha de processo), o agente gera mensagem explicativa com o motivo, sem atribuir culpa individual.

---

## Regras da mensagem

- Máximo 3 frases, sem saudação e sem assinatura
- Primeira frase sempre indica o desconto: `-25% na Bonificação.` ou `VALOR DA BONIFICAÇÃO ZERADO.`
- Nunca mencionar números, percentuais ou valores — só direção
- Tom direto e factual, sem frases motivacionais genéricas

---

## Stack

Python · BigQuery · Google Sheets API · LLM (Claude)
