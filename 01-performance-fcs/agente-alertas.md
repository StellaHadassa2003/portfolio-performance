# Agente de Alertas de Performance

Identifica semanalmente colaboradores em risco e direciona para o coordenador responsável com recomendação de ação, gerando rastreabilidade completa das intervenções.

---

> Evolução: este agente é a base do [Performance Wave](../03-performance-wave/README.md), que detalha as sete dimensões de detecção, os textos por IA com travas, o retorno do supervisor e a pesquisa com o colaborador.

---

## Critérios de alerta

- Queda de performance consecutiva por dois ou mais períodos
- Absenteísmo acima do limiar definido por setor
- Padrão recorrente de detratoras operacionais
- Reincidência nos 20% piores do setor

---

## Fluxo

1. Pipeline semanal identifica colaboradores que atendem a um ou mais critérios
2. Alerta é gerado com contexto: histórico de pontuação, motivos, comparativo com a equipe
3. Coordenador responsável recebe o alerta via Slack com recomendação de ação
4. Coordenador registra o retorno pelo totem (intervenção realizada, justificativa)
5. Rastreabilidade completa fica registrada no BigQuery

---

## Stack

Python · BigQuery · Slack API
