# Deploy — Minhas Primeiras Palavras com Deus (Cloudflare Pages, GitHub-first)

LP estática (HTML único + assets). Deploy via integração Git do Cloudflare Pages.

## 1. Subir para o GitHub

```bash
cd deploy/github-cloudflare
git init
git add .
git commit -m "LP Minhas Primeiras Palavras com Deus"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/minhas-primeiras-palavras.git
git push -u origin main
```

## 2. Conectar no Cloudflare Pages

Dashboard → Workers & Pages → Create → Pages → Connect to Git → selecionar o repo.

Configuração de build:
- **Framework preset:** None / Static HTML
- **Build command:** (deixe em branco)
- **Build output directory:** `public`
- **Root directory:** `/`

Salvar e fazer o deploy. A URL sai como `minhas-primeiras-palavras.pages.dev`.

## 3. Antes de rodar tráfego (placeholders P0)

Editar `public/index.html` e substituir:
1. `#checkout` → link real do Kiwify/Hotmart (em todos os CTAs).
2. `[IMAGEM HERO / MOCKUP DO KIT]` → mockup real dos 5 PDFs; e criar `public/assets/images/og-cover.webp` (imagem de compartilhamento — hoje a tag `og:image` aponta pra esse caminho).
3. `[DEPOIMENTO 1..3]` → depoimentos reais (foto + nome + cidade + resultado).
4. `[FOTO/ BIO TEACHER SANDRA]` → conteúdo real (ou remover a seção).
5. `META_PIXEL_ID` e `GA4_ID` → IDs reais de rastreamento (ainda não inseridos no HTML; adicionar os snippets quando disponíveis).

## Estrutura
```
public/
  index.html      ← LP completa (CSS + JS embutidos)
  _headers        ← cabeçalhos de segurança + cache de assets
  _redirects      ← rotas (vazio por ora)
```
