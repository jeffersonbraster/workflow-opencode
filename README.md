# OpenCode Engineering Team

Sistema de agentes e skills para transformar o OpenCode em um ambiente de desenvolvimento assistido por IA, com fluxo semelhante ao de uma equipe de engenharia — funcionando tanto em projetos modernos (Node/React/Next/TS) quanto em projetos de trabalho com Jinja2, JavaScript puro e ferramentas internas restritas.

---

## Objetivo

Padronizar como tarefas são analisadas, planejadas, implementadas, revisadas e testadas.

Foco:

* Menos improvisação
* Mais aderência ao padrão de cada projeto
* Melhor qualidade de código, com verificação real (não só "parece certo")
* Menos regressões
* Velocidade sem pular etapas críticas

---

## Estrutura real

```text
.opencode/
├── agents/
│   ├── orchestrator.md
│   ├── investigator.md
│   ├── planner.md
│   ├── implementer.md
│   ├── reviewer.md
│   └── tester.md
└── skills/
    ├── detect-stack/SKILL.md
    ├── quick-fix/SKILL.md
    ├── quality-gate/SKILL.md
    ├── work-stack-jinja-vanilla/SKILL.md
    ├── feature-workflow/SKILL.md
    ├── bugfix-workflow/SKILL.md
    ├── architecture-analysis/SKILL.md
    ├── test-strategy/SKILL.md
    ├── legacy-project/SKILL.md
    ├── create-pr/SKILL.md
    ├── code-review/SKILL.md
    ├── root-cause-analysis/SKILL.md
    ├── refactoring/SKILL.md
    └── performance-analysis/SKILL.md

AGENTS.md
```

> **Importante:** confira na sua versão instalada do OpenCode se o nome esperado das pastas globais é `agent`/`skill` (singular) ou `agents`/`skills` (plural) — a documentação oficial usa singular para configuração global em `~/.config/opencode/`, mas versões/forks podem variar. Rode `opencode agent list` e `opencode skill list` (ou equivalente) após instalar para confirmar que tudo foi reconhecido.

Para uso **global** (todos os projetos): copie o conteúdo de `.opencode/` para `~/.config/opencode/` (ajustando o nome das pastas conforme a nota acima) e o `AGENTS.md` para `~/.config/opencode/AGENTS.md`.

Para uso **por projeto**: coloque a pasta `.opencode/` na raiz do projeto. Um `AGENTS.md` local nesse projeto tem prioridade sobre o global.

---

## Agentes

### Orchestrator
Coordena o fluxo completo. Nunca implementa diretamente (tools de escrita desabilitadas no próprio agente). Decide entre fluxo completo e fluxo rápido.

### Investigator
Analisa stack, arquitetura, arquivos e impactos. Somente leitura (write/edit desabilitados).

### Planner
Gera plano de execução a partir do relatório do investigator. Somente leitura.

### Implementer
Único agente com permissão de escrita. Implementa seguindo o plano e os padrões existentes.

### Reviewer
Revisão técnica cética: bugs, regressões, segurança, performance, legibilidade. Somente leitura.

### Tester
Define cenários de teste e roda a skill `quality-gate` (lint, type-check, build, testes) de verdade via bash.

---

## Skills

| Skill | Função |
|---|---|
| `detect-stack` | Identifica linguagem, framework, arquitetura, monorepo |
| `quick-fix` | Critério para pular o fluxo completo em tasks triviais |
| `quality-gate` | Executa lint/type-check/build/testes reais antes de finalizar |
| `work-stack-jinja-vanilla` | Convenções para Jinja2, JS puro e ferramentas internas restritas |
| `feature-workflow` | Fluxo completo para novas funcionalidades |
| `bugfix-workflow` | Fluxo completo para correção de bugs |
| `architecture-analysis` | Identifica o padrão arquitetural do projeto |
| `test-strategy` | Define estratégia de testes antes de implementar |
| `legacy-project` | Regras de segurança para sistemas legados |
| `create-pr` | Gera Pull Request padronizado |
| `code-review` | Revisão técnica avulsa (ex: PR de terceiros) |
| `root-cause-analysis` | Investiga causa raiz, não só sintoma |
| `refactoring` | Refatoração segura sem alterar comportamento |
| `performance-analysis` | Identifica gargalos de performance |

---

## Fluxo recomendado

**Nova funcionalidade:**
```
Investigator → Planner → Implementer → Reviewer → Tester
```

**Bug:**
```
Investigator → Root Cause Analysis → Implementer → Reviewer → Tester
```

**Task trivial** (ver critérios em `quick-fix`):
```
Implementer → Reviewer (leve) → Quality Gate
```

---

## Como usar

Análise inicial do projeto:
```
@investigator
Analise completamente este projeto.
```

Nova funcionalidade:
```
@orchestrator
Adicionar exportação CSV para usuários.
```

Correção de bug:
```
@orchestrator
Corrigir erro 500 ao salvar cliente.
```

Revisão avulsa de código (ex: PR de outra pessoa):
```
Use a skill code-review para revisar esse PR.
```

Análise de performance:
```
Use performance-analysis para analisar gargalos.
```

---

## Boas práticas

* Sempre investigar antes de implementar.
* Sempre revisar antes de concluir.
* Nunca considerar uma task pronta sem o `quality-gate` passar de verdade.
* Seguir os padrões já existentes do projeto — modernizar não é o objetivo por padrão.
* Priorizar simplicidade e manutenção sobre abstração prematura.
* Usar `AGENTS.md` como fonte principal de convenções.
* Em código legado (Jinja2, JS puro, ferramentas internas): mudança mínima, comportamento preservado, sempre.