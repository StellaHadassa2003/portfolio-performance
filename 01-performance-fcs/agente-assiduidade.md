# Agente de Assiduidade

Verifica semanalmente se cada colaborador tem direito à bonificação de assiduidade, consultando a API Ahgora e cruzando com a planilha de controle.

---

## Fluxo

1. Lê matrículas e período da planilha de controle da semana
2. Consulta a API Ahgora (SOAP) para cada matrícula
3. Compara o resultado com a coluna de direito à premiação
4. Salva os resultados no BigQuery
5. Gera JSON com divergências encontradas
6. **Bloqueia o pagamento automaticamente** se houver inconsistências — aguarda validação humana antes de liberar

---

## Destaques

**Parada obrigatória** — o agente nunca avança para o pagamento sem confirmação explícita. Se há divergência, envia resumo via Slack e aguarda resposta antes de prosseguir.

**Ajuste manual via BQ** — se a liderança identificar um erro de registro (ex: falta que deveria ser abono), o agente aplica o ajuste diretamente na tabela do BigQuery via UPDATE e confirma antes de liberar.

**Verificação de duplicidade** — antes de rodar, consulta o BQ para verificar se já existe resultado para o período atual, evitando reprocessamento acidental.

---

## Stack

Python · Ahgora SOAP API · BigQuery · Google Sheets API · Slack API
