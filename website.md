# Khoakaka.com — website spec (Jekyll + GitHub Pages)

Use this file as the **single source of truth** when generating a Jekyll site in another Cursor project. It describes the publisher brand, how the **Family Tree** app (this repository) fits as a product, legal URL conventions, and suggested pages with copy-ready metadata.

---

## 1. Publisher / site

| Field | Value |
|--------|--------|
| **Domain** | `https://khoakaka.com` (target production URL) |
| **Site name** | Khoakaka |
| **Tagline** | Smart Code, Happy Life |
| **Motto** | Keep Automating, Keep Advancing |
| **Scope** | Marketing site for mobile (and related) apps. This repo is one product under the umbrella. |

### Brand notes (for design / assets)

- **Logo idea:** A key stylized into the letter “K”, or a subtle smiley inside the app icon silhouette.
- **Accent color (from Flutter launcher config):** `#C62B48` — use as primary brand tint if you align with the Family Tree app icon.

### Jekyll site defaults (suggested `_config.yml`)

```yaml
title: Khoakaka
description: Smart Code, Happy Life — mobile apps by Khoakaka.
url: https://khoakaka.com
# If the repo is username.github.io or project pages, set baseurl, e.g.:
# baseurl: "/repo-name"
author:
  name: Khoakaka
lang: en
```

GitHub Pages: enable **Settings → Pages → Source** (branch/folder or GitHub Actions). For a **project site** (`username.github.io/repo/`), set `baseurl` and use `relative_url` / `absolute_url` filters in layouts.

---

## 2. Product: Family Tree (Clan app — this repository)

**Repository / codebase name:** `giapha`  
**English product name (web / marketing):** Family Tree — genealogy for extended families and clans  

Store listing titles may use a localized name; keep web copy and this spec in English.

**Technical / internal name:** “Clan” (Firestore `clans`, features under `lib/features/clan/`, RevenueCat product ids such as `clan_yearly`, entitlement `clan`).

**One-line pitch:** Family tree and clan management — members, relationships, tree view, sharing, and subscriptions — on Android, iOS, and Web.

### Platforms and stack (for “Features” / “About” pages)

- **Platforms:** Android, iOS, Web (Flutter single codebase).
- **Backend:** Firebase (Authentication, Cloud Firestore, Storage); optional mention of Google Sign-In.
- **Monetization:** In-app subscriptions (for example RevenueCat `purchases_flutter` in the app). Omit pricing on the static site unless you commit to maintaining it.

### Suggested store / app links (placeholders — fill in Jekyll `_data` or `_config`)

Add when you have public URLs:

```yaml
# _data/giapha.yml (example)
name: Family Tree
slug: clan
play_store_url: ""   # Google Play listing
app_store_url: ""    # Apple App Store listing
web_app_url: ""      # e.g. Firebase Hosting custom domain or *.web.app
support_email: ""    # public contact only
```

Do **not** publish demo credentials or internal Firebase project IDs on the marketing site.

### Feature bullets (for landing / product page)

Use or shorten as needed:

- Create and manage **clans** (extended families) with roles and permissions.
- **Member** profiles with photos (Firebase Storage).
- **Family tree** visualization (`lib/features/tree/`).
- **CSV import** for bulk members; multilingual UI.
- **Share clan** / invitations by email (admin flows).
- **Subscriptions** for premium capabilities (configure in app and stores).

### Imagery

- App icon source in repo: `assets/icon/icon.png` (copy exported PNGs into the Jekyll site’s `assets/` — do not hotlink the private repo from production).

---

## 3. Legal and policies URL convention

Each **product** gets its own privacy and terms pages (required for store listings and in-app links). Paths use the slug `clan` to match the app and backend naming.

| Document | Suggested public path (under site root) |
|-----------|----------------------------------------|
| Family Tree / Clan — Privacy Policy | `/legal-policies/clan/privacy.html` |
| Family Tree / Clan — Terms of Use | `/legal-policies/clan/terms.html` |

**Jekyll mapping:**

- Files: `legal-policies/clan/privacy.md` and `legal-policies/clan/terms.md` (or `.html` if not using Markdown).
- Set `permalink: /legal-policies/clan/privacy.html` (and the same pattern for terms) in front matter so URLs match what the app and stores expect.

**Future products:** mirror structure, for example `/legal-policies/<product-slug>/privacy.html`.

---

## 4. Suggested site map (pages to generate)

| Path | Purpose |
|------|--------|
| `/` | Home — Khoakaka intro, slogan, grid of products with links to each product page. |
| `/products/` | Optional index of all apps. |
| `/products/clan/` or `/giapha/` | Family Tree product landing (screenshots, features, store buttons). |
| `/legal-policies/clan/privacy.html` | Privacy policy (product-specific). |
| `/legal-policies/clan/terms.html` | Terms of use (product-specific). |
| `/about/` | Optional — studio or author story. |
| `/contact/` | Optional — support email or form link only. |

Use **English** for URL slugs and filenames.

---

## 5. Front matter templates (copy into Jekyll)

### Home

```yaml
---
layout: default
title: Khoakaka
description: Smart Code, Happy Life — apps and tools by Khoakaka.
---
```

### Product page (Family Tree)

```yaml
---
layout: product
title: Family Tree — Genealogy and clan management
description: Manage your lineage on mobile and web. Members, tree view, sharing, and more.
product_slug: clan
hero_image: /assets/images/giapha-hero.png
---
```

### Privacy (fixed permalink for app stores)

```yaml
---
layout: legal
title: Privacy Policy — Family Tree
description: How Family Tree collects, uses, and protects your data.
permalink: /legal-policies/clan/privacy.html
---
```

### Terms

```yaml
---
layout: legal
title: Terms of Use — Family Tree
description: Terms governing use of the Family Tree application.
permalink: /legal-policies/clan/terms.html
---
```

---

## 6. Content checklist for the other Cursor project

When generating the Jekyll repo:

1. **Minima or custom theme** — set theme in `Gemfile` / `_config.yml`, or use a blank layout plus your CSS using brand color `#C62B48`.
2. **`_data/products.yml`** — list products with `name`, `slug`, `description`, `play_store_url`, `app_store_url`, `web_app_url`.
3. **Navigation** — Home, Products, Legal (dropdown per product or footer links to privacy and terms).
4. **`robots.txt` / sitemap** — optional `jekyll-sitemap` plugin if compatible with GitHub Pages allowed plugins.
5. **Footer** — Copyright “Khoakaka”, year, links to all public legal pages.
6. **Align in-app URLs** — any `url_launcher` or store compliance strings in the Flutter app should match these permalinks exactly.

---

## 7. Relationship: this repo and the website

- **This repo** (`giapha`): Flutter application source — not the Jekyll site.
- **Website repo** (separate): Jekyll plus GitHub Pages at `khoakaka.com` (or GitHub Pages domain until custom DNS).
- **Cross-link:** Product page on the site links to stores and web app; in-app Privacy and Terms open the `legal-policies/clan/*.html` URLs on the same domain.

---

## 8. Other projects (placeholder)

The live site will eventually list **other Khoakaka apps** alongside Family Tree. For each new app, add: product slug, `_data` entry, landing page, and `legal-policies/<slug>/privacy.html` plus `terms.html` using the same pattern as section 3.
