---
name: bugfix-workflow
description: Fluxo completo para correção de bugs
---

## Etapas

1. Reproduzir o bug
2. Causa raiz (`root-cause-analysis`)
3. Corrigir (mudança mínima necessária)
4. Revisar impacto (`@reviewer`)
5. Validar com testes + quality gate (`@tester`)

Se o bug for trivial e isolado (ex: typo, off-by-one em um único lugar), pode seguir a skill `quick-fix`.