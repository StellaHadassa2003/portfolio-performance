# Automações — Relatórios e Exportações

Scripts que rodam periodicamente para exportar dados consolidados das darkstores e gerar relatórios para a liderança operacional.

---

## Scripts

| Script | O que faz |
|---|---|
| `exportar_produtividade.py` | Exporta a produtividade consolidada por setor/turno/semana para o Google Sheets da liderança |
| `relatorio_sla_semanal.py` | Gera PDF com o resumo de SLA e tempo de ciclo por loja, publicado no Drive |
| `alertar_ruptura.py` | Monitora rupturas acima do limiar e envia alerta via Slack para o coordenador da loja |

---

## Fluxo semanal

```
Pipeline Dataform fecha
    ↓ exportar_produtividade.py   → planilha Drive da liderança atualizada
    ↓ relatorio_sla_semanal.py    → PDF publicado no Drive
    → notificação Slack para coordenadores
```

---

## Stack

Python · BigQuery · Google Sheets API · Google Drive API · Slack API · ReportLab (PDF)
