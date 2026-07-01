---
name: detect-stack
description: Detecta linguagem, framework, arquitetura e ferramentas do projeto atual — sempre executar primeiro
---

## Sinais para checar

### Node / TypeScript / React / Next.js
- `package.json` (dependencies, scripts, engines)
- `tsconfig.json` (strict mode ativado?)
- `next.config.js`/`.ts` (App Router vs Pages Router)
- `pnpm-workspace.yaml` / `turbo.json` / `nx.json` (monorepo)
- `.eslintrc*`, config de prettier

### Python / Jinja2
- `requirements.txt` / `pyproject.toml` / `Pipfile`
- Templates `.html` com `{{ }}` ou `{% %}` → Jinja2
- `settings.py`, `wsgi.py`, `manage.py` → Django
- `app.py`, `Flask(__name__)` → Flask

### JavaScript puro (sem framework/bundler)
- Ausência de `package.json` com framework, mas presença de `.js` soltos
- Scripts carregados diretamente via `<script src="">`
- Ausência de bundler configurado (webpack/vite/rollup)

### Ferramentas internas / restritas (ecossistemas corporativos fechados)
- Imports/requires de pacotes com escopo privado ou nomes não encontráveis no npm público
- CLIs ou configs proprietárias sem documentação pública
- **Nesses casos: nunca assumir comportamento. Buscar usos existentes no próprio repositório como referência de contrato/API antes de escrever qualquer coisa contra essas ferramentas.**

## Identificar

- Linguagem principal e secundárias
- Framework(s)
- ORM / camada de dados
- Banco de dados
- Testes (framework e cobertura aproximada)
- Arquitetura (ver skill `architecture-analysis`)
- Se é monorepo e como os pacotes se relacionam

## Retornar

Resumo direto, sem floreio — isso alimenta diretamente o relatório do `@investigator`.