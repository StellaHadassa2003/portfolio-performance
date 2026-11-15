# Performance Wave

Camada de **acompanhamento ativo** construída sobre o sistema de performance dos FCs. O ranking e o totem mostram o que aconteceu; o Wave decide **quem precisa de atenção, o que a liderança deve fazer e se a ação aconteceu**, e devolve essa informação ao sistema.

> Este material descreve **metodologia e decisões de desenho**. Não contém dados de colaboradores, resultados individuais, credenciais nem identificadores internos.

---

## O problema

Com o ranking semanal existia rastreabilidade individual, mas não havia um mecanismo que transformasse a informação em ação:

- sinais de risco de saída (queda de produção, faltas, advertências) ficavam espalhados em fontes diferentes;
- o supervisor recebia números, não uma leitura do caso nem uma sugestão de conduta;
- não havia registro do que a liderança decidiu fazer, então não dava para avaliar se a ação funcionou;
- o colaborador em risco nunca era ouvido.

## A ideia

Um ciclo semanal fechado, em que cada etapa alimenta a seguinte:

```
Detectar → Explicar → Direcionar → Registrar → Medir
```

| Etapa | O que faz | Documento |
|---|---|---|
| Detectar | Cruza produção, presença e disciplina em sete dimensões e classifica o caso | [Detecção de alertas](./deteccao-alertas.md) |
| Explicar | Texto de análise e ação, escrito por IA sob regras e travas determinísticas | [Textos por IA](./textos-ia.md) |
| Direcionar | Define quem recebe o caso e qual conduta é indicada | [Encaminhamento e ação](./encaminhamento-e-acao.md) |
| Registrar | O supervisor responde sobre cada caso antes de abrir os feedbacks semanais | [Retorno do supervisor](./retorno-supervisor.md) |
| Ouvir | Pesquisa privada com o colaborador, por perfil | [Pesquisa com o colaborador](./pesquisa-colaborador.md) |
| Medir | Acompanhamento das ações e dos desfechos | [Acompanhamento](./acompanhamento.md) |

Estudos de apoio:

- [Novatos e rampa](./novatos-e-rampa.md): a régua de referência de quem está nos primeiros 90 dias.
- [Expansão para novos setores](./expansao-novos-setores.md): como o mesmo método foi adaptado a Expedição e Reposição.
- [Modelo de retenção x reposição](./modelo-retencao-reposicao.md): direção de um modelo determinístico de apoio à decisão.
- [Princípios e salvaguardas](./principios-e-salvaguardas.md): o que o sistema se recusa a fazer.

---

## Decisões de desenho que se repetem

1. **Regra determinística decide, IA escreve.** Quem entra em alerta, o nível e o destinatário saem de SQL e regras. A IA só redige o texto, e nunca altera o nível.
2. **A IA é vigiada por código.** Limite de frases, de números, coerência da série e proibição de afirmar o que não existe são checados depois da resposta, com reescrita automática.
3. **Contexto antes de dado.** O texto conta a história do caso (desde quando, o que mudou) em vez de listar valores.
4. **Humano sempre decide.** O Wave sugere; supervisor e coordenação agem. Não há decisão automática sobre pessoas.
5. **Nada vai para produção sem validação em ensaio.** Mudanças são testadas em jobs somente leitura que imprimem o resultado, sem gravar nem avisar ninguém.

---

## Stack

BigQuery · Dataform · Python · Cloud Run Jobs · modelo de linguagem (via API) · Node.js/Express · React/Vite (telas dentro do totem) · Slack (avisos agregados)
