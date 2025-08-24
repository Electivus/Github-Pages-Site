# Organization site (GitHub Pages)

This directory contains a static site ready to be published to the organization’s GitHub Pages. The deployment is configured to use GitHub Actions to build with the latest Jekyll (instead of the fixed `github-pages` gem).

## How to publish

1) Create the repository in the organization:

   - Repository name: `Electivus.github.io`
   - Visibility: Public

2) Set the custom domain

   - The `CNAME` file already contains `electivus.com`.
   - In your DNS provider, point:
     - To use the root domain `electivus.com`:
       - `A` records to GitHub Pages IPs: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`.
       - (Optional, recommended) `CNAME` from `www` to `Electivus.github.io` and enable `Enforce HTTPS` in Pages settings.
     - Alternative (if your DNS supports ALIAS/ANAME at apex): create an `ALIAS/ANAME` from `electivus.com` to `Electivus.github.io`.

3) First push

   From this directory (`github-pages-site`):

   ```bash
   git init -b main
   git add .
   git commit -m "Initialize org site"
   git remote add origin git@github.com:Electivus/Electivus.github.io.git
   git push -u origin main
   ```

4) Enable GitHub Pages (via Actions)

   - In `Settings` → `Pages`:
     - Under "Build and deployment", select `Source: GitHub Actions`.
     - The workflow `.github/workflows/jekyll.yml` already builds with the latest Jekyll and publishes to Pages.
   - Ensure `Custom domain` is `electivus.com`. Save and enable `Enforce HTTPS` when available.

   Notes:
   - The build uses Ruby 3.3 and `jekyll ~> 4.3` (see `Gemfile`).
   - Existing static files (e.g., `index.html`, `assets/`) continue to work; Jekyll copies them into `_site`.

## Customize

- Edit `index.html` to update content, links, and visuals.
- The Apex Log Viewer link points to `Electivus/apex-log-viewer`.
- Add pages/assets as needed (e.g., `assets/img/`, `docs/`, etc.).

## Structure

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
