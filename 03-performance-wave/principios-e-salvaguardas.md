# Princípios e salvaguardas

O Wave lida com informação sensível sobre pessoas. Estas regras são parte do desenho, não complementos.

---

## O que o sistema não faz

- **Não decide sobre pessoas.** Sugere e registra; supervisor e coordenação decidem.
- **Não pune nem premia por resposta de pesquisa.** A pesquisa só coleta.
- **Não alerta sobre liderança no nível individual.** Problemas de liderança são tratados como problemas da empresa, não como alerta de colaborador.
- **Não alerta quem já está de saída decidida** (desligamento direto).
- **Não culpa o indivíduo por problema coletivo.** A saúde do setor entra na leitura.
- **Não afirma o que os dados não mostram.** Causa presumida, ausência afirmada e número inventado são bloqueados.

## Proteção de dados

- Dados pessoais de contato (documento, e-mail, telefone) não entram em textos, logs, exemplos nem fixtures.
- Identificadores de acesso são tratados como credenciais: nunca aparecem em relatórios.
- Segredos ficam em gerenciador de segredos, nunca no código.
- Respostas da pesquisa são privadas, com acesso restrito e leitores definidos.

## Controle humano e de mudança

- Mudanças de regra, prompt ou modelo passam primeiro por **ensaio somente leitura**.
- Nada é aplicado em produção (visões, agente, tabelas, alertas) sem aprovação explícita.
- Mensagens enviadas em nome de uma pessoa são **rascunhos revisados por ela**; avisos automáticos carregam apenas contagens.
- Todo o código vai por revisão em repositório (ramo, pull request, revisão, merge); não há publicação direta de código de aplicação.

## Qualidade do texto

- O texto fala em nome do sistema, sem citar a ferramenta de IA.
- Sem gênero presumido, sem emojis, sem corporativês.
- Limites de tamanho fixos, para a leitura caber na rotina do supervisor.
