# Modelo de retenção x reposição

Direção de um modelo **determinístico, sem IA**, para apoiar a pergunta que o alerta sozinho não responde: **vale mais manter a pessoa atual ou repor com um novato?**

> Status: desenhado e parcialmente construído; em pausa para priorizar as telas de retorno e pesquisa. Não está em produção.

---

## Ideia

Comparar dois valores esperados ao longo de um horizonte:

- **Manter**: produção esperada da pessoa atual, considerando presença (quantos dias ela realmente vem), produtividade nos dias presentes e a chance de sair.
- **Repor**: produção esperada de um novato, com a curva de rampa da referência e a retenção típica da fase.

O modelo é de **apoio à decisão**. Desligamento nunca é automático e sempre tem revisão humana.

## Princípios

- **Esperado = média da pessoa nos dias presentes x dias previstos.** Não usa metas teóricas de pontuação.
- **Peso do dia de pico.** Falta em dia de alta demanda custa mais; o peso do dia vem do padrão de produção do grupo.
- **Concentração de faltas no pico** é um sinal separado, com mínimo de ocorrências para evitar ruído.
- **Suavização da probabilidade por dia**, para não reagir a oscilações pequenas.
- **Faixas de tempo de casa** para a persistência (menos de 60 dias, até 90, até 180, até 1 ano, acima de 1 ano).
- **Sem custo em reais por ora**: motivo da ausência e erros ficam para uma etapa posterior.
- **Parâmetros versionados em tabela**; o modelo propõe mudanças, mas não as aplica sozinho.

## Cobertura

O modelo cobre quem já passou da fase de rampa. Para os novatos há uma abordagem à parte, com a curva de rampa e a retenção da referência de novatos.

## Saídas planejadas

- Previsão diária por pessoa, comparada ao realizado depois.
- Aba de acompanhamento no Wave.
- Alerta de risco de pico de ausência por grupo e dia (planejamento de pessoal).
- Resumo agregado para as lideranças, com aprovação humana antes de qualquer envio.
