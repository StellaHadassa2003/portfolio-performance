# Detecção de alertas

Um job semanal cruza as fontes de produção, presença e disciplina e classifica cada colaborador por **dimensão**. Cada dimensão tem três níveis: normal, atenção/alerta e crítico. O nível do caso é o mais grave entre as dimensões.

---

## As sete dimensões

| Dimensão | O que observa |
|---|---|
| Volume | Produção do colaborador contra o grupo comparável (mesmo FC, setor e turno) |
| Tendência | Direção da produção nas últimas semanas |
| Presença | Faltas, atrasos e atestados em janela longa |
| Advertências | Quantidade e recorrência de medidas disciplinares |
| Detratoras | Erros operacionais que derrubam a pontuação |
| Cross-setor | Comportamento da pessoa que atua em mais de um setor |
| Saúde do setor | Contexto: o grupo inteiro está mal ou só a pessoa? |

A saúde do setor entra para **não culpar o indivíduo por um problema coletivo** (falta de demanda, tempo morto, quebra de processo).

---

## Princípios do método

**Comparar com o grupo certo.** A referência é sempre a mesma combinação de FC, setor e turno. Em setores como a Expedição, o volume por dia muda muito entre turnos, e comparar turnos diferentes geraria alertas falsos.

**Usar pontos e itens juntos.** Pontos refletem a qualidade (erros pesam) e itens refletem o ritmo. A leitura cruzada separa "produz pouco" de "produz, mas erra".

**Exigir persistência.** A dimensão de volume só aponta quando a queda se repete em mais de uma das últimas semanas; uma semana ruim isolada não vira alerta. Duas condições em níveis diferentes definem alerta e crítico.

**Janelas diferentes por assunto.** Produção usa janela curta, porque reage rápido; presença usa janela longa, porque faltas são esparsas e uma janela curta mostraria ruído.

**Filtros antes do alerta.**
- Quem acabou de entrar só é avaliado pela régua de novatos.
- Quem tem medida de desligamento direto (justa causa) é **descartado**: o alerta existe para prevenir a saída, e essa já está decidida.
- Quem está escalado para tarefa que não conta como produção (por exemplo, conferência de endereços) não é tratado como produtividade baixa.

**Limite por grupo, com crítico visível.** Para o supervisor não receber uma lista impossível de agir, há um teto de casos por grupo. A revisão em andamento garante que casos críticos não fiquem escondidos pelo teto.

---

## Saída

Cada caso gera uma linha com as dimensões, o nível, o destinatário, a ação sugerida pela regra e os dados de apoio. O texto da IA é anexado depois (ver [Textos por IA](./textos-ia.md)). A gravação substitui a semana inteira, o que torna a reexecução segura.
