# Expansão para novos setores

O método do Wave nasceu em setores de separação e embalagem. A expansão para **Expedição** e **Reposição** mostra o que é reutilizável e o que precisa ser reaprendido a cada setor.

> Status: em validação por ensaio. Nada foi ativado em produção para esses setores.

---

## O que se reaproveita

- As sete dimensões de detecção e os níveis de alerta.
- A lógica de encaminhamento e as diretrizes de ação.
- O mecanismo de texto por IA e todas as suas travas.
- A régua de novatos.

## O que muda por setor

| Aspecto | Adaptação |
|---|---|
| **Vocabulário** | A produção deixa de ser "itens" e passa a ser a unidade do setor (volumes expedidos; movimentações feitas) |
| **Escala do volume** | Em Expedição o volume por dia depende do turno, então a referência é sempre por turno |
| **Pontos de erro** | Erros de gestão de estoque e divergência de endereços entram como detratoras, com a unidade correta de cada um |
| **Check de endereços** | Quem foi escalado para conferência não é tratado como produtividade baixa; os dois números aparecem lado a lado |
| **Referência de novatos** | Estudo à parte, com as mesmas colunas da referência original |
| **Fiscal e célula por pedido** | Só existem em alguns setores; Reposição e Expedição seguem o ramo padrão |

## Como foi validado

1. **Estudo de risco de saída** por setor, para decidir quais dimensões fazem sentido em cada um.
2. **Exemplos escritos à mão**, com dados fictícios em ordem de grandeza real, para a liderança avaliar tom e conteúdo antes de qualquer código.
3. **Ensaio com dados reais** em job somente leitura: o relatório mostra o que a IA recebeu, o que escreveu e quais travas dispararam.
4. **Comparação com a semana anterior** antes de qualquer ativação.

## Lição principal

O que parecia "bug de escala" era diferença real entre turnos. Todo setor novo precisa de **uma análise de como a produção se distribui** antes de se definirem limiares.

## Ordem de publicação

1. Mudanças gerais (travas, filtro de desligamento, regra de integração) entram primeiro, nos setores atuais.
2. Depois, a referência de novatos dos setores novos e as alterações de dados.
3. Por último, os próprios setores, com ensaio sem IA e sem aviso antes de ligar o fluxo completo.
