# Documentation project instructions

## About this project

- This is a documentation site built on [Mintlify](https://mintlify.com) for the **Pujante ecosystem** (AgroPujante, Escola Pujante, Pujante Admin, Pujante Mobile)
- Pages are MDX files with YAML frontmatter
- Configuration lives in `docs.json`
- All content is written in **Brazilian Portuguese (pt-BR)**

## Structure

- `index.mdx` — home with product cards + onboarding trail
- `ecossistema.mdx` — how the 4 products connect (Mermaid, handoff, entidades homônimas, matriz de padrões)
- `propriedade-tabelas.mdx` / `convencoes-banco.mdx` / `glossario.mdx` / `changelog.mdx` — transversais
- `operacao/` — mapa de produção, troubleshooting, runbooks, observabilidade, segurança
- `agropujante/` — Portal editorial (FastAPI `/api/v1`); inclui quickstart e convencoes
- `escola/` — LMS + mentoria (FastAPI `/api/v2` + NestJS legado); financeiro dividido em financeiro-dashboards/billing/nfse
- `admin/` — Painel admin unificado; dashboards dividido em visao-geral/financeiro/marketing/observability
- `mobile/` — App Expo/React Native (cliente das APIs v1 e v2)
- `openapi/agropujante.json` — spec gerado do FastAPI (playground beta); regenerar quando a API mudar:
  `cd AgroPujante-LP/backend && .venv/Scripts/python -c "from app.main import app; import json; json.dump(app.openapi(), open('../../docs/openapi/agropujante.json','w',encoding='utf-8'), ensure_ascii=False)"` (reinjetar `servers`)

## Conventions added in this docs

- Cada página tem `icon` no frontmatter; descriptions ≤ ~120 chars
- Páginas de API linkam pra `<produto>/convencoes` em vez de repetir "Erros comuns"
- Diagramas em Mermaid (não ASCII art); `<Tip>`/`<Info>` pra contexto, `<Warning>` só pra risco real
- Atualize `changelog.mdx` (componente `<Update>`) a cada release de doc

## Terminology

- **AgroPujante** (ou "Portal") = portal jurídico do agro com conteúdo editorial. NÃO é landing page e NÃO é a escola.
- **Escola Pujante** = LMS + mentoria. Produto separado do Portal.
- **Jurisprudência** ≠ **julgados** ≠ **boletins**: consulta de jurisprudência (via jurisprudencias.ai) é uma feature; julgados são posts editoriais; boletins são PDFs curados de julgados.
- **Apoiador** (supporter) e **PRO** não coexistem — 1 assinatura por usuário; apoiador ativo já inclui acesso PRO.
- Use "usuário", "assinante", "apoiador", "mentorado" conforme o contexto do produto.

## Style preferences

- Português (pt-BR), voz ativa, segunda pessoa ("você")
- Sentence case nos títulos
- Code formatting para nomes de arquivos, comandos, paths, endpoints e variáveis de ambiente
- Tabelas de endpoints no formato: Método | Path | Descrição | Auth
- Auth levels: Público, JWT, MANAGER, ADMIN, Internal Token, JWT/Key (admin)

## Content boundaries

- NUNCA documentar valores de secrets/chaves — apenas nomes de variáveis de ambiente
- Endpoints que retornam 501 devem ser marcados como "não implementado"
- Migrations do schema `pujante` são manuais (SQL Editor do Supabase) — não documentar como automáticas
