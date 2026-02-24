# CLAUDE.md -- FloatingWetlands.com

## What This Project Is

Static marketing site for Natural Waterscapes' floating treatment wetland product line. Five self-contained HTML pages with inline CSS/JS. No build step, no dependencies, no framework.

**Live URL:** `https://floatingwetlands.com`
**Hosting:** Cloudflare Pages (Git integration, auto-deploy on push to `main`)
**Owner:** Natural Waterscapes LLC (Jon Klotz)

## Pages

| File | URL | Purpose |
|------|-----|---------|
| `index.html` | `/` | Homepage -- product overview, audience cards, calculator CTA, FAQ, contact form |
| `food-chain.html` | `/food-chain` | Pillar page -- trophic cascade science, nutrient cycling, food chain mechanics |
| `fisheries.html` | `/fisheries` | Pillar page -- Neal & Lloyd research, fisheries habitat, spawning substrate |
| `performance.html` | `/performance` | Pillar page -- removal rates, sizing guidance, peer-reviewed data |
| `faq.html` | `/faq` | FAQ -- sizing, cost, installation, maintenance, structured data (FAQPage schema) |

## Deploy

### First-Time Setup (Cloudflare Pages)

1. Create GitHub repo and push:
   ```bash
   git init
   git add .
   git commit -m "FloatingWetlands.com v2"
   gh repo create jonathanklotz/floatingwetlands-site --private --push
   ```

2. Connect to Cloudflare Pages:
   - Cloudflare dashboard -> Workers & Pages -> Create -> Pages -> Connect to Git
   - Select `floatingwetlands-site` repo
   - **Production branch:** `main`
   - **Build command:** *(leave blank)*
   - **Build output directory:** `/`
   - Click "Save and Deploy"

3. Add custom domains (in Pages project -> Custom domains):
   - `floatingwetlands.com`
   - `www.floatingwetlands.com`

### Ongoing Deploys

```bash
git add .
git commit -m "description of change"
git push
```

That's it. Cloudflare Pages auto-deploys on push. No build step, no CI config needed.

## Brand Standards

- **Primary green:** #1B6B4A (`--nw-primary`)
- **Dark green:** #0F4A30 (`--nw-dark`)
- **Light green:** #2A8C62 (`--nw-light`)
- **Gold accent:** #C5A55A (CTA buttons on pillar pages)
- **Text dark:** #1A1A18
- **Font:** Tahoma, 'Segoe UI', Verdana, Geneva, sans-serif
- **No Google Fonts. No serif fonts. No external font imports.**
- Light theme (white/cream backgrounds, dark text)
- All CSS is inline in each HTML file (no external stylesheets)
- All JS is inline in each HTML file (no external scripts)
- No emojis in UI

## Architecture Notes

- Each HTML file is fully self-contained (inline `<style>` and `<script>` blocks). This is intentional for simplicity and zero-dependency deployment.
- Cloudflare Pages serves `.html` files at clean URLs automatically (`/food-chain.html` serves at `/food-chain`).
- `_redirects` file handles convenience redirects (Cloudflare Pages native feature).
- `_headers` file sets security headers on all responses.
- No node_modules, no package.json, no build tooling.

## Related Projects

| Project | URL | Repo | Stack |
|---------|-----|------|-------|
| FTW Calculator | `calculator.floatingwetlands.com` | `jonathanklotz/ftw-calculator` | Cloudflare Worker + D1 + ArcGIS |
| MyPond | `mypond.naturalwaterscapes.com` | `jonathanklotz/mypond` | Cloudflare Worker + D1 + ArcGIS |
| NW Shop | `shop.naturalwaterscapes.com` | -- | BigCommerce |

## Product Context

The site markets Atlan modular floating treatment wetlands distributed exclusively by Natural Waterscapes.

**Atlan Module Specs:**
- 858mm equilateral triangular modules
- Sold in 2-packs (two triangles form an 858mm square, 8 sq ft)
- $518.00 per 2-pack standard / $498.99 at 20+ units
- Shop URL: `https://shop.naturalwaterscapes.com/modular-floating-island/`

**Coverage Tiers (approved by Jon):**
- Habitat enhancement: 2-3% (Neal & Lloyd fisheries data)
- General water quality: 5-10% (Clemson, NC DEQ)
- Aggressive treatment: 10%+ (high nutrient load)

## Content Sources

All scientific claims on the site are sourced from peer-reviewed literature. Do not add claims without a verifiable source. Key references include:

- Neal & Lloyd (2018) SEAFWA Journal -- fisheries/habitat coverage thresholds
- Clemson Cooperative Extension -- FTW installation and maintenance guide
- NC DEQ -- minimum coverage recommendations
- Headley & Tanner (2012) -- nutrient removal mechanisms
- Various DOI-linked papers cited inline in pillar pages

## Editing Guidelines

- When editing pages, preserve the inline CSS/JS architecture. Do not extract to external files.
- All five pages share a common nav and footer structure. If you update nav links or footer content, update all five files.
- The homepage `#calculator` section links to `https://calculator.floatingwetlands.com`. Do not change this to an anchor-only link.
- Pillar page CTA buttons also link to the calculator. Keep these consistent.
- Do not add tracking scripts, analytics, or third-party JS without explicit approval.
- Images are not hosted locally. Any images referenced are external URLs or inline SVG.

## Common Tasks

**Add a new pillar page:**
1. Copy an existing pillar page as template
2. Update nav links in ALL five (now six) files
3. Update footer links in ALL files
4. Commit and push

**Update calculator link:**
The calculator URL is `https://calculator.floatingwetlands.com`. It appears in:
- `index.html` -- calculator section CTA button + footer
- `food-chain.html` -- CTA button + footer
- `fisheries.html` -- CTA button + footer
- `performance.html` -- CTA button + footer
- `faq.html` -- CTA button + footer

**Update product pricing:**
Pricing appears on the homepage products section and in pillar page CTAs. Grep for `518` and `498.99` to find all instances.
