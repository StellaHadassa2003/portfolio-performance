# Automações — Carteira, Ranking e Relatórios

Scripts Python que rodam após o fechamento do pipeline semanal e automatizam o ciclo completo de pagamento: do ranking à planilha de folha.

---

## Scripts

| Script | O que faz |
|---|---|
| `exportar_rankings.py` | Exporta os rankings da semana para as planilhas de cada FC no Google Drive |
| `atualizar_carteira.py` | Atualiza o saldo de bonificação de cada colaborador no BigQuery |
| `preencher_planilha_performance.py` | Preenche a planilha de pagamento para o time de folha processar |
| `adicionar_bonus_pdf.py` | Adiciona bônus pontuais aprovados via PDF ao ciclo atual |
| `subir_bonus_planilha.py` | Registra bônus extras na planilha consolidada |
| `relatorio_bonus_ranking.py` | Gera PDF de relatório semanal com resumo de ranking e pagamentos |

---

## Fluxo da semana

```
Pipeline Dataform fecha
    ↓ exportar_rankings.py     → planilhas Drive de cada FC atualizadas
    ↓ atualizar_carteira.py    → saldo BQ atualizado
    ↓ preencher_planilha_*.py  → planilha de pagamento preenchida
    ↓ relatorio_bonus_*.py     → PDF gerado e publicado no Drive
    → notificação Slack para o time de folha
```

---

## Stack

Python · Google Sheets API · Google Drive API · BigQuery · Slack API · ReportLab (PDF)
