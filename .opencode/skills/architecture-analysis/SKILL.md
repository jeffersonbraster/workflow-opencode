---
name: architecture-analysis
description: Analisa arquitetura e decisões de design do projeto
---

## Objetivo

Entender profundamente a arquitetura antes de propor qualquer mudança estrutural.

## Analisar

- Estrutura de pastas e módulos
- Boundaries entre camadas
- Padrões arquiteturais aplicados
- Acoplamento e dependências circulares
- Mistura de padrões (ex: parte do projeto em Clean Architecture, parte em código legado sem camadas)

## Identificar padrão

- Clean Architecture (domain / use-cases / infra / presentation)
- DDD
- MVC
- Hexagonal
- Modular Monolith
- Microservices
- Server-rendered com templates (Jinja2/Django/Flask) — sem camadas explícitas de domínio
- Script ou página solta sem arquitetura formal (comum em JS puro legado)

## Retornar

```
# Architecture Summary
# Patterns
# Risks
# Improvement Opportunities
```

`Improvement Opportunities` deve ser realista: se o projeto é legado e estável, melhoria não significa recomendar reescrita.