# FloatingWetlands.com

Static marketing site for the floating treatment wetland product line. Deployed via Cloudflare Pages.

## Pages

- **/** -- Homepage (product overview, calculator CTA, FAQ, contact)
- **/food-chain** -- Pillar: Food Chain Science (trophic cascade, nutrient cycling)
- **/fisheries** -- Pillar: Fisheries Management (Neal & Lloyd research, habitat)
- **/performance** -- Pillar: Performance Data (removal rates, sizing guidance)
- **/faq** -- FAQ (sizing, cost, installation, maintenance)

## Deploy

Connected to Cloudflare Pages. Pushes to `main` auto-deploy.

**Cloudflare Pages settings:**
- Build command: *(none -- static files)*
- Build output directory: `/`
- Root directory: `/`

## Related Projects

- **FTW Calculator** (`calculator.floatingwetlands.com`) -- Cloudflare Worker, separate repo
- **MyPond** (`mypond.naturalwaterscapes.com`) -- Cloudflare Worker, separate repo
- **NW Shop** (`shop.naturalwaterscapes.com`) -- BigCommerce
