---
name: test-strategy
description: Define estratégia de testes antes de qualquer implementação
---

## Antes de qualquer alteração

Identificar:

- Framework de testes já usado (Jest, Vitest, Testing Library, pytest, etc)
- Testes existentes que cobrem a área afetada
- Se não existe framework de testes configurado, reportar isso explicitamente — não silenciar

## Gerar

```
# Unit Tests
# Integration Tests
# E2E Tests (se aplicável)
# Edge Cases
# Regression Scenarios
```

## Priorizar

- Menor custo de implementação, maior cobertura de risco
- Cenários críticos de negócio antes de casos triviais
- Em projetos sem testes: sugerir o mínimo viável para a task atual — não propor suíte completa do zero como bloqueio