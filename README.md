# Site da organização (GitHub Pages)

Este diretório contém um site estático pronto para ser publicado no GitHub Pages da organização. A publicação foi ajustada para usar o build via GitHub Actions com a versão mais recente do Jekyll (em vez do pacote `github-pages` fixo do Pages).

## Como publicar

1) Crie o repositório na organização:

   - Nome do repositório: `Electivus.github.io`
   - Visibilidade: Public

2) Configure o domínio customizado

   - O arquivo `CNAME` já contém `electivus.com`.
   - No DNS do seu provedor, aponte:
     - Para usar o domínio raiz `electivus.com`:
       - Registros `A` para os IPs do GitHub Pages: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.
       - (Opcional recomendado) `CNAME` de `www` para `Electivus.github.io` e, nos settings do Pages, marque `Enforce HTTPS`.
     - Alternativa (se seu DNS suportar ALIAS/ANAME no apex): crie `ALIAS/ANAME` de `electivus.com` apontando para `Electivus.github.io`.

3) Faça o primeiro push

   Dentro deste diretório (`github-pages-site`):

   ```bash
   git init -b main
   git add .
   git commit -m "Initialize org site"
   git remote add origin git@github.com:Electivus/Electivus.github.io.git
   git push -u origin main
   ```

4) Ative o GitHub Pages (via Actions)

   - Em `Settings` → `Pages`:
     - Em "Build and deployment", selecione `Source: GitHub Actions`.
     - O workflow `.github/workflows/jekyll.yml` já faz o build com Jekyll mais recente e publica no Pages.
   - Garanta que o campo `Custom domain` esteja `electivus.com`. Salve e ative `Enforce HTTPS` quando disponível.

   Observações:
   - O build usa Ruby 3.3 e `jekyll ~> 4.3` (definido no `Gemfile`).
   - Arquivos estáticos existentes (por exemplo, `index.html`, `assets/`) continuam funcionado normalmente; o Jekyll apenas copia para `_site`.

## Personalização

- Edite `index.html` para atualizar conteúdo, links e visual.
- O link do apex-log-viewer aponta para `Electivus/apex-log-viewer`.
- Adicione páginas/ativos conforme necessário (por exemplo, `assets/img/`, `docs/`, etc.).

## Estrutura

```
github-pages-site/
├─ index.html
├─ CNAME
├─ robots.txt
├─ Gemfile
├─ _config.yml
├─ .github/
│  └─ workflows/
│     └─ jekyll.yml
└─ assets/
   └─ css/
      └─ styles.css
```
