---
name: quick-fix
description: Critério objetivo para pular o fluxo completo em tasks realmente triviais
---

## Quando usar o fluxo rápido

A task é candidata a fluxo rápido somente se **todos** os itens abaixo forem verdade:

- Menos de ~15 linhas alteradas
- Não muda contrato de API pública, schema de banco, ou tipo exportado
- Não introduz dependência nova
- Escopo de um único arquivo (ou dois arquivos fortemente relacionados, ex: componente + estilo)
- Já se sabe exatamente onde mexer, sem precisar mapear o projeto

## Fluxo rápido

1. `@implementer` faz a mudança diretamente.
2. `@reviewer` faz uma checagem leve (apenas Critical Issues + Verdict, sem o relatório completo).
3. A skill `quality-gate` roda de qualquer forma — isso nunca é pulado, nem no fluxo rápido.

## Quando NÃO usar (sempre fluxo completo)

- Mudança de schema (Prisma, banco, contrato de API)
- Qualquer feature nova, mesmo que pareça pequena
- Qualquer alteração em código legado sem cobertura de teste
- Qualquer coisa envolvendo autenticação, pagamento, ou dados sensíveis
- Task com motivo pouco claro — na dúvida, não é trivial