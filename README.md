# khoakaka.com

Marketing site for **Khoakaka** — a small studio that ships focused mobile
apps. The first product on the site is **Family Tree** (internal name `Clan`,
repository `giapha`).

The single source of truth for the site's intent is [`website.md`](./website.md).

The site is built with **Jekyll** and deployed to **GitHub Pages**.

---

## Stack and theme decision

GitHub Pages supports two ways to use a theme:

1. **Bundled themes** (Minima, Cayman, Modernist, etc.) — stable but visually
    dated for a marketing site.
2. **Remote themes** via `jekyll-remote-theme` (e.g. `jekyll-serif`).
3. **Custom theme** — full control over branding and layout.

This repo uses option 3: a small **custom theme** (3 layouts + 4 includes
+ ~500 lines of CSS) so the brand color `#C62B48` and the "K + smiley" identity
drive the visual design. `jekyll-remote-theme` is still wired in `_config.yml`,
so swapping in a community theme later is a one-line change.

The site uses only the GitHub Pages allowed plugins:

* `jekyll-seo-tag`
* `jekyll-sitemap`
* `jekyll-feed`
* `jekyll-remote-theme`

---

## Repository layout

```text
.
├── _config.yml               # Jekyll config + brand tokens
├── _data/                    # YAML data
│   ├── products.yml          # Product catalog (rendered on home + /products)
│   ├── navigation.yml        # Header + footer links
│   └── giapha.yml            # Extra metadata for Family Tree
├── _includes/                # Reusable HTML fragments
│   ├── head.html
│   ├── header.html
│   ├── footer.html
│   └── product-card.html
├── _layouts/                 # Page layouts
│   ├── default.html
│   ├── product.html
│   └── legal.html
├── assets/
│   ├── css/main.scss         # Compiled by Jekyll's Sass
│   └── images/               # Logo, favicon, hero illustration
├── about/
├── contact/
├── legal-policies/
│   └── clan/
│       ├── privacy.md        # → /legal-policies/clan/privacy.html
│       └── terms.md          # → /legal-policies/clan/terms.html
├── products/
│   ├── index.html            # Product index
│   └── clan/index.md         # Family Tree landing
├── 404.html
├── CNAME                     # Custom domain
├── Gemfile
├── index.html                # Home
├── robots.txt
└── website.md                # Spec — do not delete
```

---

## URL contract (must stay stable)

These URLs are referenced from the Family Tree app and may be required in app
store listings. **Do not change them without coordinating with the app.**

| Page                       | URL                                          |
| -------------------------- | -------------------------------------------- |
| Home                       | `/`                                          |
| Products index             | `/products/`                                 |
| Family Tree product page   | `/products/clan/`                            |
| Family Tree privacy policy | `/legal-policies/clan/privacy.html`          |
| Family Tree terms of use   | `/legal-policies/clan/terms.html`            |

For each new product, mirror the structure under
`/products/<slug>/` and `/legal-policies/<slug>/`.

---

## Run locally

Requires Ruby 3.1+ and Bundler.

```bash
bundle install
bundle exec jekyll serve --livereload
```

The site will be available at <http://127.0.0.1:4000>.

> **Windows note.** Ruby's `wdm` filesystem-watch gem does not build on
> Ruby ≥ 3.3, so we don't depend on it. If you need auto-rebuild on save,
> add `--force-polling`:
>
> ```bash
> bundle exec jekyll serve --livereload --force-polling
> ```

To preview a production-style build:

```bash
JEKYLL_ENV=production bundle exec jekyll build
```

---

## Deploy

Pushing to `main` triggers `.github/workflows/jekyll.yml`, which builds the
site and publishes it via the **GitHub Pages** environment using the official
`actions/configure-pages`, `actions/upload-pages-artifact`, and
`actions/deploy-pages` actions. No `gh-pages` branch is needed.

Before the first deploy:

1. **Settings → Pages → Source:** set to **GitHub Actions**.
2. **Settings → Pages → Custom domain:** enter `khoakaka.com`. Make sure
    your DNS has the four GitHub `A` records (or a `CNAME` for `www`)
    pointing at GitHub Pages, and enable **Enforce HTTPS**.

---

## Adding a new product

1. Add an entry to `_data/products.yml` with a unique `slug`.
2. Create `products/<slug>/index.md` using `layout: product` and
    `product_slug: <slug>`.
3. Create `legal-policies/<slug>/privacy.md` and `terms.md` with the
    matching `permalink:` values.
4. (Optional) Add the product to `_data/navigation.yml` footer links.

That's it — the home page, products index, and product page pick everything
up from the data file automatically.

---

## Specs

See [`website.md`](./website.md) for the full publisher / brand /
URL-convention spec.
