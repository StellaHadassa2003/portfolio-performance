# Textos por IA com travas determinísticas

Cada alerta recebe dois textos: **Análise** (o que aconteceu) e **Ação** (o que o responsável deve fazer). Um modelo de linguagem escreve; o código garante que o texto respeite as regras.

---

## Entrada

A IA recebe um resumo estruturado do caso, nunca a base bruta: séries por semana e por dia, médias da pessoa e do grupo, direção da produção, desde quando houve queda, ausências, advertências, erros e a ação indicada pela regra. Dados pessoais de contato não entram no texto enviado.

## O que o prompt exige

- **Contar a história do caso**: desde quando, o que mudou, o que explica. Dado solto não é análise.
- **Comparar sempre com a referência**: nunca um valor sozinho.
- **Só o que existe**: não citar ausência ("sem faltas"), nem dado que não muda a ação. Isso mantém o texto curto.
- **Sem conclusões que os dados não sustentam**: dificuldade na atividade só quando a média está abaixo da referência; queda recente com média normal é descrita como trajetória a entender.
- **Sem julgamento da pessoa**: o alerta serve para começar uma conversa.
- **Sem gênero presumido**: usar o nome ou "a pessoa".

## Travas depois da resposta

| Trava | Como funciona |
|---|---|
| Limite de frases | Análise até 5, ação até 3. Acima disso a IA reescreve (até 2 vezes); persistindo, o código corta |
| Limite de números | A análise tem teto de números. Datas, tempo de casa e identificadores de grupo não contam |
| Ausência afirmada | Frases do tipo "não há faltas" são detectadas; a IA reescreve, e se insistir a frase é removida |
| Coerência da série | "Caiu de X para Y" é conferido contra os números; narrativa invertida volta para reescrita |
| Verificação de números | Valores citados que não existem nos dados enviados geram aviso para revisão |
| Pronomes | Pronomes de gênero voltam para reescrita ou são trocados por "a pessoa" |
| Recuperação de identificadores | Se a IA devolver o texto com identificador trocado, o texto é reatribuído ao caso certo; se algum caso ficar sem texto, há nova tentativa |

## Casos que não usam texto livre

Quando a regra já sabe a conduta, o texto de ação é fixo. Exemplo: casos de risco de abandono na integração ficam só para visibilidade da coordenação, com texto padrão.

## Escolha de modelo

O modelo foi comparado em fidelidade aos dados e custo por execução. O ganho de fidelidade de um modelo maior pesou mais que a diferença de custo, que em volume semanal continua pequena em valor absoluto. A troca de modelo é feita por configuração, sem mudar o código.

## Como o texto foi melhorado

Um **job de ensaio somente leitura** roda o fluxo real com dados reais, imprime o relatório (dados enviados à IA, texto, avisos) e não grava nada nem envia mensagens. Cada rodada revelou falhas concretas (soma de erros incorreta, janela errada, série narrada ao contrário, afirmação de ausência, texto longo demais), e cada falha virou regra no prompt ou trava no código.
