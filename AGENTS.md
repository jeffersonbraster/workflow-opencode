# Engineering Rules

## Princípios sempre válidos

- Investigar antes de implementar.
- Seguir os padrões já existentes no projeto — nunca impor um framework ou estilo pessoal num projeto que não usa.
- Não criar arquitetura nova sem necessidade real.
- TypeScript strict quando o projeto for TS; nunca introduzir `any` sem comentário justificando o motivo.
- Evitar duplicação de código.
- Código pronto para produção: sem `console.log` de debug, sem TODO esquecido, sem código morto/comentado.
- Nunca assumir o comportamento de bibliotecas ou ferramentas internas/proprietárias desconhecidas — investigar exemplos reais de uso no repositório antes de escrever contra elas.

## Contextos suportados

Este setup atua em dois contextos diferentes, e o `investigator` é responsável por identificar qual deles se aplica antes de qualquer decisão:

1. **Projetos pessoais** — Node.js, React, Next.js, TypeScript, Clean Architecture.
2. **Projetos de trabalho** — Jinja2/Python, JavaScript puro (sem framework/bundler), TypeScript, e ferramentas internas/restritas de ecossistema corporativo fechado.

Ver skill `detect-stack` (identificação) e `work-stack-jinja-vanilla` (convenções específicas do contexto 2).

## Fluxo obrigatório (tasks não triviais)

```
investigator → planner → implementer → reviewer → tester
```

Toda feature nova, mudança de contrato/API/schema, ou alteração em código sem cobertura de teste segue esse fluxo completo, sem exceção.

## Fluxo rápido (tasks triviais)

Ver skill `quick-fix` para os critérios exatos. Regra geral: se você tem dúvida se é trivial, não é — siga o fluxo completo.

## Contrato de saída entre agentes

Cada agente que produz um relatório (investigator, planner, reviewer, tester) segue um template fixo, definido no próprio arquivo do agente. Isso existe para que o próximo agente da cadeia consiga consumir o resultado sem ambiguidade. Não improvise formatos diferentes.

## Nenhuma task termina sem quality gate

Ver skill `quality-gate`. Lint, type-check, build e testes (os que existirem no projeto) são executados de verdade via bash antes de qualquer task ser considerada concluída. Avaliação "por leitura" não substitui execução real.

## Escalonamento

Se qualquer agente encontrar ambiguidade, bloqueio, ou dependência de algo desconhecido (ex: ferramenta interna sem documentação acessível), ele reporta isso explicitamente em vez de assumir. O orchestrator decide se resolve sozinho ou pergunta ao usuário — nunca segue adiante sobre uma suposição não confirmada.

## Fonte de verdade

Este `AGENTS.md` e os arquivos em `.opencode/agents/` e `.opencode/skills/` são a fonte principal de convenções globais. Um `AGENTS.md` dentro de um projeto específico tem prioridade sobre este quando houver conflito direto.