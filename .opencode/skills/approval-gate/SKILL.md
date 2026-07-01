---
name: approval-gate
description: Trava obrigatória de aprovação humana para mudanças de risco alto — nunca pular
---
 
## Quando esta skill é acionada
 
Sempre que a task envolver qualquer um destes pontos, identificados pelo `investigator` ou `planner`:
 
- Mudança de schema de banco de dados (Prisma migration, alteração de tabela/coluna)
- Mudança em fluxo de autenticação/autorização
- Qualquer coisa envolvendo pagamento ou dado financeiro
- Exposição ou manipulação de dados sensíveis de usuário (PII)
- Mudança em contrato de API pública (rota, payload, tipo exportado)
- Alteração em configuração de infraestrutura/deploy/variáveis de ambiente de produção
## Regra
 
Quando qualquer um desses pontos for identificado, o `@orchestrator`:
 
1. **Para** antes de chamar o `@implementer`.
2. Apresenta ao usuário: o que vai mudar, por quê, e qual o pior cenário se der errado.
3. Só prossegue após confirmação explícita do usuário.
Isso é uma trava dura, não uma sugestão — mesmo que o `@planner` classifique o risco como "baixo", esses gatilhos sempre passam por aprovação humana. Não existe autonomia total nesses casos, por design.
 
## Diferença em relação ao fluxo normal
 
No fluxo padrão, o orchestrator só escala pro usuário se detectar risco alto durante o planejamento. Aqui, a lista de gatilhos acima **sempre** força a parada, independente da avaliação de risco do planner — são categorias que exigem julgamento humano por definição, não por heurística de IA.