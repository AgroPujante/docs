# Documentation project instructions

## About this project

- This is a documentation site built on [Mintlify](https://mintlify.com) for the **Pujante ecosystem** (AgroPujante, Escola Pujante, Pujante Admin, Pujante Mobile)
- Pages are MDX files with YAML frontmatter
- Configuration lives in `docs.json`
- All content is written in **Brazilian Portuguese (pt-BR)**

## Structure

- `index.mdx` — home with product cards
- `ecossistema.mdx` — how the 4 products connect (shared Supabase, auth handoff, proxies)
- `agropujante/` — Portal editorial (FastAPI `/api/v1`)
- `escola/` — LMS + mentoria (FastAPI `/api/v2` + NestJS legado)
- `admin/` — Painel admin unificado (FastAPI agregador)
- `mobile/` — App Expo/React Native (cliente das APIs v1 e v2)

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
