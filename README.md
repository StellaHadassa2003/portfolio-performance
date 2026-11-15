# Portfolio — Sistemas de Performance Shopper

Conjunto de sistemas e agentes construídos para acompanhamento de performance individual e coletiva nas operações da Shopper (FCs e darkstores).

---

## Produtos

| Produto | Descrição | Stack |
|---|---|---|
| [Sistema de Performance — FCs](./01-performance-fcs/README.md) | Pipeline de dados, ranking semanal, totem de feedback e agentes de operação | BigQuery · Dataform · Node.js · Vue.js · Gemini AI · Cloud Run |
| [Sistema de Performance — Darkstores](./02-performance-darkstores/README.md) | Dashboard intraday, painel de lideranças e pipeline de dados das darks | BigQuery · Node.js · Vue.js · Firebase · Cloud Run |
| [Performance Wave](./03-performance-wave/README.md) | Camada de acompanhamento ativo: detecta risco de saída, explica por IA, direciona à liderança, registra o retorno e ouve o colaborador. Documenta apenas a metodologia | BigQuery · Dataform · Python · Cloud Run Jobs · LLM · Node.js · React |

---

## Impacto consolidado

- **+89%** de crescimento de headcount coberto (jun/25 → out/26)
- **+203%** de produtividade em picking desde implantação do sistema
- **74 mil** feedbacks individuais processados (nov/25 → out/26)
- **193.870** acessos ao totem diário por **2.272 colaboradores únicos**
- **148.670** acessos ao totem semanal por **2.628 colaboradores únicos**

---

## Arquitetura geral

```
BigQuery (dados brutos)
    ↓
Dataform (transformação e pipeline semanal)
    ↓
Cloud Run (APIs Node.js)
    ↓
Totem / Dashboard (Vue.js — Firebase Hosting)
    ↓
Colaborador / Liderança
```

O **Performance Wave** fecha o ciclo sobre essa base: o ranking mostra o que aconteceu, e o Wave decide quem precisa de atenção, o que a liderança deve fazer e se a ação aconteceu (detalhes em [03-performance-wave](./03-performance-wave/README.md)).

Todos os sistemas usam autenticação via Google OAuth2 e integração nativa com BigQuery via service account ou OAuth user credentials.
