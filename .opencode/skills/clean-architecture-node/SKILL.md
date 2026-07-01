---
name: clean-architecture-node
description: Convenções de Clean Architecture para projetos Node.js, React, Next.js e TypeScript — stack principal
---

## Quando aplicar

Sempre que o `detect-stack` identificar Node.js/React/Next.js/TypeScript como stack do projeto. Esta é a stack principal — o padrão de qualidade aqui é o mais rígido de todo o setup.

## Camadas (quando o projeto já segue Clean Architecture)

```
domain/        → entidades e regras de negócio puras, zero dependência externa
use-cases/     → orquestração de regras de negócio, depende só de domain
infra/         → implementações concretas (banco, HTTP, filas), depende de domain via interface
presentation/  → controllers, componentes React, rotas Next.js
```

## Regra de dependência (nunca violar)

- `domain` nunca importa de `infra` ou `presentation`.
- `use-cases` depende de interfaces (ports), não de implementações concretas — inversão de dependência.
- Se o projeto ainda não tem essas camadas explícitas, **não force a estrutura de uma vez só** numa task pontual — siga o padrão já existente (ver `legacy-project`) e sugira a evolução como observação separada, não como parte da entrega atual.

## Validação na borda

- Toda entrada externa (body de API, query params, form) é validada com `zod` (ou a lib de validação já usada no projeto) antes de chegar na camada de domínio/use-case.
- Nunca confiar em tipo do TypeScript sozinho para validar dado vindo de fora — tipo é checagem em compile-time, não em runtime.

## Tratamento de erro

- Definir um padrão único no projeto (Result/Either explícito ou exceptions customizadas) e segui-lo — não misturar os dois estilos na mesma base de código.
- Nunca engolir erro silenciosamente (`catch {}` vazio).
- Erros de domínio (regra de negócio violada) são diferentes de erros técnicos (falha de infra) — tratar e logar diferente.

## React / Next.js específico

- Server Components por padrão; `"use client"` só quando necessário (interatividade, hooks de estado, browser API).
- Componentes de apresentação não devem conter lógica de negócio — lógica de negócio fica em `use-cases` ou hooks dedicados, nunca dentro do JSX diretamente.
- Evitar prop drilling excessivo — se passar de 2-3 níveis, considerar contexto ou composição.
- Nomes de hooks customizados sempre `use*`, com responsabilidade única.

## TypeScript

- Strict mode sempre ativo.
- Nunca `any` sem comentário explicando o motivo pontual.
- Preferir `unknown` + narrowing a `any` quando o tipo realmente não é conhecido de antemão.
- Tipos de domínio compartilhados entre front e back (se for monorepo) ficam num pacote/módulo comum, não duplicados.

## Retornar (quando usada via investigator/planner)

```
# Aderência ao padrão
# Desvios encontrados
# Recomendação (mudança mínima necessária, nunca reescrita completa numa task pontual)
```