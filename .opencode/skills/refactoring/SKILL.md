---
name: refactoring
description: Refatoração segura, sem alterar comportamento
---

## Objetivo

Refatorar sem alterar comportamento observável.

## Priorizar

- Simplicidade
- Legibilidade
- Redução de duplicação

## Regras

- Sempre ter cobertura de teste (ou criar testes de caracterização) antes de refatorar código sem testes.
- Refatoração nunca é combinada com mudança de comportamento no mesmo commit/PR — são coisas separadas.