---
name: quality-gate
description: Executa verificação objetiva e real antes de qualquer task ser considerada concluída
---

## Sempre, antes de marcar como pronto

Detectar quais comandos existem no projeto (via `package.json` scripts, `Makefile`, `tox.ini`, etc) e executar os aplicáveis via bash:

- Type-check: `tsc --noEmit` (ou equivalente do projeto)
- Lint: `eslint .` / `npm run lint`
- Build: `npm run build` / `next build`
- Testes: `npm test` / `pnpm test` / `pytest` (projetos Python/Jinja2)

## Regras

- Rodar os comandos de verdade via bash — nunca "assumir que passaria".
- Se um comando não existir no projeto, reportar isso como ausência/risco, não pular silenciosamente.
- Colar o output relevante (erros, principalmente) no relatório final — não resumir genericamente um erro real.
- Falha em qualquer gate = task `NOT READY`, mesmo que o código pareça correto na leitura.