---
name: legacy-project
description: Trabalhar com segurança em sistemas legados
---

## Nunca

- Reescrever módulos inteiros
- Trocar arquitetura ou framework
- Trocar bibliotecas por preferência pessoal
- Criar abstrações grandes para um caso de uso único

## Sempre

- Alterar o mínimo possível
- Preservar comportamento existente
- Validar impactos antes de mexer
- Combinar com `work-stack-jinja-vanilla` quando aplicável

## Identificar

- Pontos frágeis
- Dependências ocultas
- Side effects (ex: omissão de um campo disparando comportamento amplo)

## Retornar

Plano conservador, com o menor diff possível.