# sulibreaks.com

WordPress site management, SEO updates, and version snapshots for sulibreaks.com (hosted on SiteGround).

## Project tracks

1. **SEO fixes** — Phase 1/2/3 improvements to existing WordPress site
2. **New website** — Full rebuild (separate repo when ready)

## Repo structure

```
db/                     # DB snapshots — wp db export dumps
  sulibreaks-YYYY-MM-DD.sql
pages/                  # Page content snapshots (JSON)
  pages-index.json      # All page IDs, titles, slugs
  page-{ID}.json        # Full content per key page
  seo-meta.txt          # Yoast title + meta per page
theme/                  # Child theme files
  functions.php
  style.css
plugins.json            # Active plugin list
```

## SSH access

- Host: `uk31.siteground.eu` port `18765`
- User: `u1235-xeqtg1ihbvt2`
- Key: `~/.ssh/id_siteground_claude` (passphrase removed for autonomous use)
- WP root: `~/www/sulibreaks.com/public_html`

## WP-CLI examples

```bash
ssh -i ~/.ssh/id_siteground_claude -p 18765 u1235-xeqtg1ihbvt2@uk31.siteground.eu \
  "cd ~/www/sulibreaks.com/public_html && wp <command>"

# Snapshot DB
wp db export /tmp/sulibreaks-$(date +%Y-%m-%d).sql

# Purge cache after edits
wp sg purge

# Update page content via eval-file
wp eval-file /tmp/my-script.php
```

## Stack

- WordPress on SiteGround (uk31)
- SEO plugin: Yoast
- Theme: Salient + salient-child
- Cache: SiteGround Speed Optimizer

## SEO Roadmap

### Phase 1 — Immediate Wins
- [x] Rewrite page titles and meta descriptions (homepage, speaker, services, book me)
- [x] Rebuild Speaker page (H1, 700+ words, keywords, client names, testimonials, FAQs)
- [x] Fix `user-scalable=0` in viewport meta tag
- [ ] Fix broken ticket link (LA show, returning 404 — Eventbrite widget in wp-admin)
- [ ] Create 4 service sub-pages (keynote, workshops, live performances, brand collabs)

### Phase 2 — Conversion & Authority
- [ ] Reorder homepage sections (put speaking proof higher)
- [ ] Rename "Book Me" to something more intent-clear
- [ ] Add FAQ sections to all key pages
- [ ] Improve enquiry flow / response time signal

### Phase 3 — AI Search + Long-Term
- [ ] Add Person + Event + FAQ schema markup (JSON-LD)
- [ ] Launch blog / Insights section
- [ ] Strengthen E-E-A-T signals (client names in text, media logos)
- [ ] Image compression + Core Web Vitals
