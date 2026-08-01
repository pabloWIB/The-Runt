# The Runt

Static landing page for a fictional $0/month online real estate advisory service, built with no JavaScript and no dependencies.

## Description

The offer is free advice, and "free" is a claim people distrust — so the page states the price first and spends the rest of the layout earning it back. The headline is the price (`True $0/Month Online Real Estate Advisor`), followed by the reasons to choose the service and a single closing call to action.

Type carries the design. Poiret One, a geometric display face, sets every heading and the wordmark; body copy runs in the system UI stack so it stays legible at small sizes and costs nothing to download. That split is taken from the original design mockup, kept in `docs/diseno-original.webp`.

The page ships as three CSS files and one HTML file. There is no JavaScript anywhere in the project: no mobile menu to toggle, no carousel, no form. Everything the page does, it does with markup and CSS.

## Tech stack

| Layer | Technology | Role in project |
|---|---|---|
| Markup | HTML5 | `index.html` and `404.html` |
| Styling | CSS3 | Custom properties, grid, flexbox, `clamp()` type scale |
| Typography | Poiret One | Self-hosted WOFF2, 14.4 KB, SIL Open Font License 1.1 |
| Typography | System UI stack | Body copy, no download |
| Icons | Inline SVG | Three icons drawn for this project, no icon library |
| Scripting | None | The project contains no JavaScript files |
| Build | None | No bundler, no package manager, no dependencies |

## Project structure

```
.
├── index.html                  # Landing page
├── 404.html                    # Not-found page, links back to index
├── robots.txt                  # Allows all crawlers, points at the sitemap
├── sitemap.xml                 # Single URL, the home page
├── assets/
│   ├── css/
│   │   ├── base.css            # Variables, @font-face, reset, typography, focus
│   │   ├── layout.css          # Container, header, sections, hero, footer
│   │   └── components.css      # Brand, nav, buttons, cards, links, 404
│   ├── fonts/
│   │   ├── poiret-one-regular.woff2
│   │   └── poiret-one-ofl.txt  # SIL Open Font License 1.1
│   └── img/
│       ├── logo/
│       │   ├── the-runt-logo.webp   # Header and footer wordmark, 176×176
│       │   └── favicon.png          # Favicon and apple-touch-icon, 180×180
│       └── content/
│           ├── casa-contemporanea-hero.webp        # Hero, 1536×1024
│           ├── edificio-terrazas-ajardinadas.webp  # Closing band, 750×422
│           └── og-cover.jpg                        # Open Graph card, 1200×630
└── docs/
    ├── auditoria.md            # Inventory and state before the reorganisation
    ├── cambios.md              # Change log, grouped by phase
    └── diseno-original.webp    # Original design mockup, kept as reference
```

## Design tokens

The palette is derived from the original stylesheet and the design mockup. Every text pair clears WCAG AA (4.5:1).

| Token | Value | Use |
|---|---|---|
| `--color-navy` | `#000673` | Headings, wordmark, focus ring |
| `--color-accent` | `#d40000` | Eyebrow, link hover |
| `--color-ink` | `#333333` | Body copy |
| `--color-muted` | `#5c5c5c` | Secondary copy |
| `--color-surface` | `#f4f4f4` | Reasons band |
| `--color-footer` | `#f0f0f0` | Footer |
| `--color-black` | `#0d0d0d` | Primary button |

Spacing follows a 4 / 8 / 16 / 24 / 32 / 48 / 64 / 96 scale. Breakpoints are mobile-first at 480, 768, 1024 and 1440.

## Running it locally

The page has no build step. Open `index.html` in a browser and it works, self-hosted font included.

To serve it over HTTP instead:

```bash
git clone https://github.com/pabloWIB/The-Runt.git
cd The-Runt
python -m http.server 4321
```

Then open `http://127.0.0.1:4321/`. If you prefer Node:

```bash
npx serve .
```

## Deployment

Deployed on Vercel at [therunt.wib.digital](https://therunt.wib.digital). Static hosting with no configuration: upload the repository root as-is, no build command and no output directory. The canonical URL, `og:url` and `sitemap.xml` all point at that domain — change them if you deploy elsewhere.

## Author

**Pablo Nieto Pérez** — [wib.digital](https://wib.digital)
GitHub: [@pabloWIB](https://github.com/pabloWIB)

---

## Hire me

I build **custom internal tools, CRMs and dashboards** for small teams, and
**conversion-focused websites** for businesses.

- [Custom internal tool, CRM or dashboard](https://www.fiverr.com/pablonietop/build-a-custom-internal-app-for-your-business) — from $45
- [Conversion-focused website](https://www.fiverr.com/pablonietop/convert-your-landing-page-design-to-code) — from $80
- [All my services on Fiverr](https://www.fiverr.com/pablonietop)
- [wib.digital](https://wib.digital)
