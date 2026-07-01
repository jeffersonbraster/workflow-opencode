---
name: task-router
description: Classifica a task e decide quais agentes são realmente necessários — sempre rodar antes de escolher o fluxo
---

## Objetivo

Evitar rodar os 5 agentes quando a task não precisa disso. Cada chamada de subagente tem custo real (ver skill `cost-awareness`), então o orchestrator deve decidir conscientemente quem entra no fluxo.

## Passo 1 — Classificar o domínio

- **Front-end**: React/Next, componentes, UI, hooks, estado de cliente
- **Back-end**: API routes, server actions, banco de dados, integrações externas
- **Full-stack**: envolve os dois lados (ex: nova feature com endpoint + tela)
- **Infra/config**: build, CI, variáveis de ambiente, deploy

## Passo 2 — Classificar o tamanho/risco (ver também `quick-fix` e `approval-gate`)

- **Trivial**: fluxo rápido (`implementer` + `reviewer` leve + `quality-gate`)
- **Padrão**: fluxo completo, mas só com os agentes relevantes ao domínio
- **Alto risco** (schema, auth, pagamento, dado sensível): fluxo completo + `approval-gate` obrigatório antes do implementer agir

## Passo 3 — Montar o fluxo mínimo necessário

Nem toda task precisa do pipeline inteiro. Exemplos:

| Task | Fluxo mínimo |
|---|---|
| Ajustar estilo de um componente existente | `implementer` → `reviewer` leve |
| Novo componente React reutilizável, sem tocar em API | `investigator` (rápido) → `implementer` → `reviewer` → `tester` |
| Nova API route com regra de negócio | fluxo completo (todos os 5) |
| Bug isolado num único arquivo, causa óbvia | `implementer` → `reviewer` leve |
| Bug com causa não óbvia | `investigator` → `root-cause-analysis` → `implementer` → `reviewer` → `tester` |
| Mudança de schema/contrato de API | fluxo completo + `approval-gate` |
| Pergunta/dúvida sobre o código, sem alteração | só `investigator`, nada mais |

## Regra

O orchestrator relata explicitamente, antes de começar, qual fluxo foi escolhido e por quê:

```
# Rota escolhida
Domínio: front | back | full-stack | infra
Risco: trivial | padrão | alto
Agentes acionados: [...]
Motivo: ...
```

Isso dá visibilidade pra você decidir se concorda com a economia de agentes antes de gastar requests.