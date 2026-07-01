---
name: cost-awareness
description: Regras de consciência de custo/tokens ao usar OpenCode com provider GitHub Copilot
---

## Contexto importante

No provider `github-copilot`, o OpenCode tem um comportamento conhecido (issue aberta `anomalyco/opencode#20859`): **todos os Premium Requests de subagentes são cobrados usando o modelo do agente orquestrador (primary)**, independente do modelo configurado em cada subagente individualmente.

Isso muda a estratégia de economia:

- Não adianta só configurar subagentes com modelo barato esperando economizar — o que importa é o modelo do **orchestrator**.
- O que realmente reduz custo é **reduzir a quantidade de chamadas de subagente** (ver skill `task-router`) e usar um modelo mais barato como padrão no orchestrator.

## Regras práticas

- Use um modelo intermediário como padrão no orchestrator para o dia a dia. Suba para um modelo premium (Opus ou equivalente) manualmente só quando a task for genuinamente complexa/arquitetural.
- Sempre prefira o fluxo mínimo indicado pelo `task-router` — não rode os 5 agentes por hábito.
- No fluxo rápido (`quick-fix`), o reviewer roda em modo leve (menos chamadas, output mais curto).
- Periodicamente, rode `opencode stats --models` e compare com o CSV de uso exportado do GitHub Copilot, para confirmar que a config está sendo respeitada e identificar picos de consumo.
- Se notar que todo o consumo está caindo no modelo do orchestrator independente da config dos subagentes, isso é o bug conhecido, não um erro de configuração seu — verifique se já foi corrigido em versões recentes do OpenCode antes de tentar contornar de outra forma.

## O que NÃO fazer

- Não assuma que "modelo caro só no implementer, barato no resto" economiza automaticamente no Copilot — teste e confirme com `opencode stats --models`.
- Não rode o fluxo completo (5 agentes) para tasks triviais só para "seguir o processo" — isso é desperdício direto de requests premium.