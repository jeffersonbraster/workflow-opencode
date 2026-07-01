# OpenCode Engineering Team

Sistema de agentes e skills para transformar o OpenCode em um ambiente de desenvolvimento assistido por IA com fluxo semelhante ao de uma equipe de engenharia.

---

## Objetivo

Padronizar a forma como tarefas são analisadas, planejadas, implementadas, revisadas e testadas.

O foco é:

* Menos improvisação
* Mais aderência ao padrão do projeto
* Melhor qualidade de código
* Menos regressões
* Melhor produtividade

---

# Estrutura

```text
~/.config/opencode/

AGENTS.md

agents/
├── orchestrator.md
├── investigator.md
├── planner.md
├── implementer.md
├── reviewer.md
└── tester.md

skills/
├── detect-stack/
│   └── SKILL.md
├── feature-workflow/
│   └── SKILL.md
├── bugfix-workflow/
│   └── SKILL.md
├── architecture-analysis/
│   └── SKILL.md
├── test-strategy/
│   └── SKILL.md
├── legacy-project/
│   └── SKILL.md
├── create-pr/
│   └── SKILL.md
├── code-review/
│   └── SKILL.md
├── root-cause-analysis/
│   └── SKILL.md
├── refactoring/
│   └── SKILL.md
└── performance-analysis/
    └── SKILL.md
```

---

# Agentes

## Orchestrator

Responsável por coordenar o fluxo completo.

Responsabilidades:

* Delegar investigação
* Delegar planejamento
* Delegar implementação
* Delegar revisão
* Delegar testes
* Consolidar resultados

Não deve implementar código diretamente.

---

## Investigator

Responsável por analisar o projeto.

Atividades:

* Detectar stack
* Detectar arquitetura
* Identificar arquivos
* Identificar dependências
* Mapear impactos

Não deve modificar código.

---

## Planner

Responsável por criar planos de execução.

Atividades:

* Dividir tarefas
* Identificar riscos
* Definir ordem de implementação
* Definir estratégia de testes

Não deve modificar código.

---

## Implementer

Responsável pela implementação.

Atividades:

* Criar funcionalidades
* Corrigir bugs
* Aplicar padrões existentes
* Respeitar arquitetura do projeto

---

## Reviewer

Responsável pela revisão.

Atividades:

* Encontrar bugs
* Identificar regressões
* Avaliar performance
* Avaliar segurança
* Avaliar legibilidade

---

## Tester

Responsável pela validação.

Atividades:

* Criar cenários
* Identificar edge cases
* Validar fluxos
* Sugerir testes automatizados

---

# Skills

## detect-stack

Identifica:

* Linguagem
* Framework
* ORM
* Banco de dados
* Ferramentas
* Arquitetura

---

## feature-workflow

Fluxo completo para novas funcionalidades.

Etapas:

1. Investigação
2. Planejamento
3. Implementação
4. Revisão
5. Testes

---

## bugfix-workflow

Fluxo completo para correção de bugs.

Etapas:

1. Reprodução
2. Causa raiz
3. Correção
4. Revisão
5. Testes

---

## architecture-analysis

Analisa a arquitetura do sistema.

Identifica:

* MVC
* DDD
* Clean Architecture
* Hexagonal
* Modular Monolith
* Microservices

---

## test-strategy

Define estratégia de testes.

Inclui:

* Unitários
* Integração
* E2E
* Regressão

---

## legacy-project

Especializado em sistemas legados.

Objetivos:

* Minimizar riscos
* Evitar reescritas desnecessárias
* Preservar comportamento existente

---

## create-pr

Gera Pull Requests padronizados.

Inclui:

* Contexto
* Problema
* Solução
* Impacto
* Validação
* Rollback

---

## code-review

Realiza revisão técnica.

Analisa:

* Bugs
* Segurança
* Performance
* Complexidade
* Legibilidade

---

## root-cause-analysis

Investiga causas raízes de problemas.

Objetivo:

Corrigir a origem do problema, não apenas os sintomas.

---

## refactoring

Refatoração segura.

Objetivos:

* Reduzir complexidade
* Melhorar legibilidade
* Remover duplicações

---

## performance-analysis

Análise de performance.

Avalia:

* Queries
* Renderizações
* Consumo de memória
* Gargalos

---

# Fluxo recomendado

Nova funcionalidade:

```text
Investigator
↓
Planner
↓
Implementer
↓
Reviewer
↓
Tester
```

Bug:

```text
Investigator
↓
Root Cause Analysis
↓
Implementer
↓
Reviewer
↓
Tester
```

---

# Como utilizar

Análise inicial do projeto:

```text
@investigator

Analise completamente este projeto.
```

Nova funcionalidade:

```text
@orchestrator

Adicionar exportação CSV para usuários.
```

Correção de bug:

```text
@orchestrator

Corrigir erro 500 ao salvar cliente.
```

Revisão de código:

```text
@reviewer

Revise as alterações realizadas.
```

Análise de performance:

```text
Use performance-analysis para analisar gargalos.
```

---

# Boas práticas

* Sempre investigar antes de implementar.
* Sempre revisar antes de concluir.
* Sempre validar impactos.
* Seguir padrões existentes do projeto.
* Evitar reescritas desnecessárias.
* Priorizar simplicidade e manutenção.
* Utilizar AGENTS.md como fonte principal de convenções.

```
```
