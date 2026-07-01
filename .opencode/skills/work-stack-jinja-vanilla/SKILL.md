---
name: work-stack-jinja-vanilla
description: Convenções para projetos de trabalho com Jinja2, JavaScript puro e ferramentas internas restritas
---

## Contexto

Esses projetos costumam ser mais antigos, com menos testes automatizados e dependências de ferramentas proprietárias. Prioridade máxima: não quebrar nada, não modernizar por iniciativa própria.

## Jinja2 / templates server-side

- Respeitar a separação já existente entre lógica de view (template) e lógica de negócio (backend) — não colocar lógica complexa dentro de `{% %}`.
- Escapar variáveis por padrão; usar `| safe` apenas quando já for o padrão do projeto e houver razão clara.
- Não converter templates Jinja2 para componentes React/Next a menos que explicitamente solicitado.

## JavaScript puro (sem framework/bundler)

- Manter compatibilidade com carregamento via `<script>` se for o padrão do projeto — evitar `import`/`export` de ES modules se não houver bundler.
- Cuidado com ordem de execução e escopo global: variáveis podem estar sendo compartilhadas entre arquivos via `window`.
- Não introduzir TypeScript ou bundler nesses projetos sem alinhamento explícito — isso é decisão arquitetural, não "melhoria" unilateral.

## Ferramentas internas / restritas (ecossistema corporativo fechado)

- Nunca presumir a API de uma ferramenta interna desconhecida — buscar (grep) exemplos de uso reais no repositório antes de escrever código novo contra ela.
- Se não encontrar exemplo de uso e a documentação não estiver acessível, reportar isso explicitamente como risco/unknown — não inventar a interface.
- Preferir copiar o padrão de uso já existente no projeto a inferir a partir do nome da função/classe.

## Regra geral para todo código legado

Combinar sempre com a skill `legacy-project`: mudança mínima, comportamento preservado, sem reescritas.