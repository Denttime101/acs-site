# Auto Cosmetic Solutions — Site Build README
> Built by AI Ops Squad (aiopssquad.com) for Darren Burt / Auto Cosmetic Solutions
> autocosmeticsolutions.com | 949-282-9653

---

## FILES IN THIS BUILD

```
acs-site/
├── index.html                          ← Full homepage (all 14 sections)
├── pages/
│   ├── services/
│   │   └── bumper-repair.html          ← Service page TEMPLATE (clone × 12)
│   └── cities/
│       └── mission-viejo.html          ← City page TEMPLATE (clone × 19)
└── README.md                           ← This file
```

---

## WHAT'S BUILT

### Homepage (index.html)
All 14 sections fully built and populated:
1. Top bar — rating + phone + service area
2. Sticky nav — hamburger on mobile
3. Hero — full-bleed image, H1, trust badges, inline estimate form
4. Services — 9 service cards with links
5. Why Choose Us — 6 dark-section pillars
6. About — Darren's story + stats
7. Gallery — 6 before/after photo grid
8. Reviews — 3 real Yelp reviews (G.S. C., John C., Christy Z.)
9. Process — 4-step horizontal
10. Service Areas — 19 city links + Google Map embed
11. Promotions — 3 promo cards
12. FAQ — 8 accordion questions (FAQPage schema)
13. Contact — info blocks + full contact form
14. Footer — logo, services, cities, copyright

Includes:
- LocalBusiness (AutoBodyShop) schema JSON-LD
- FAQPage schema JSON-LD
- Full OG / Twitter meta tags
- Scroll reveal animations
- Mobile responsive down to 480px
- Google Fonts: Barlow Condensed + Barlow

### Service Page Template (bumper-repair.html)
Full service page structure including:
- Page hero with breadcrumb
- Content + sticky sidebar form layout
- What is / Why Choose / How it Works / Pricing sections
- 4-photo gallery strip
- 6-question service FAQ (FAQPage schema)
- Related services (3 cards)
- City chip list (all 19 OC cities)
- Bottom CTA bar
- Service schema JSON-LD

### City Page Template (mission-viejo.html)
Full city page structure including:
- City hero with breadcrumb + inline form
- Content + sidebar layout
- City-specific intro (local context, neighborhoods, landmarks)
- Services list grid (linked)
- Why locals choose ACS (trust bullets)
- Google Map embed (city-centered)
- 3 reviews
- City-specific FAQ accordion
- Nearby cities list
- Bottom CTA bar
- AutoBodyShop + FAQPage schema

---

## HOW TO CLONE PAGES

### Clone Service Pages (12 total)

Copy `bumper-repair.html` and replace these values:

| Token | Replace With |
|---|---|
| `Bumper Repair` (title, H1, schema) | Service name |
| `bumper-repair-orange-county` (slug) | Service slug |
| Meta description | Service-specific description |
| H1 subhead | Service-specific subhead |
| Hero intro paragraph | Service-specific 150-200 word intro |
| "What Is..." section | Service explanation (2 paragraphs) |
| Trust bullets | Service-specific reasons to choose ACS |
| How it Works steps | Service-specific 3-step process |
| Pricing box copy | Service-specific pricing context |
| FAQ questions + answers (6) | Service-specific FAQ |
| Related services cards (3) | Adjacent services |
| Gallery images + captions | Photos of that specific repair type |

**12 service pages to generate:**
1. bumper-repair-orange-county ✅ (template)
2. scratch-repair-orange-county
3. dent-removal-orange-county
4. bumper-replacement-orange-county
5. rock-chip-repair-orange-county
6. headlight-refinishing-orange-county
7. front-bumper-repair-orange-county
8. rear-bumper-repair-orange-county
9. paint-repair-orange-county (color match)
10. plastic-bumper-repair-orange-county
11. bumper-crack-repair-orange-county
12. mobile-bumper-repair-orange-county

---

### Clone City Pages (19 total)

Copy `mission-viejo.html` and replace these values:

| Token | Replace With |
|---|---|
| `Mission Viejo` (all instances) | City name |
| `mission-viejo` (slug) | City slug |
| Meta title + description | City-specific |
| Schema `areaServed.name` | City name |
| H1 `em` text | City name |
| Hero intro `p` | City-specific intro (use city name) |
| Intro section 2 paragraphs | City-specific context (landmarks, roads, neighborhoods) |
| Map embed `pb=` coordinates | City-specific Google Maps embed |
| "Our [City] Service Area" paragraph | City neighborhood context |
| Sidebar "Nearby Cities" list | Adjacent 6 cities |
| FAQ `[City]` references | City name |
| Canonical URL | City-specific URL |

**19 city pages to generate:**
1. mission-viejo ✅ (template)
2. irvine
3. newport-beach
4. laguna-beach
5. laguna-niguel
6. laguna-hills
7. dana-point
8. aliso-viejo
9. san-clemente
10. anaheim-hills
11. corona-del-mar
12. huntington-beach
13. rancho-santa-margarita
14. ladera-ranch
15. lake-forest
16. san-juan-capistrano
17. foothill-ranch
18. coto-de-caza
19. balboa-island

---

## PENDING ITEMS (CLIENT MUST PROVIDE)

| Item | Status | Notes |
|---|---|---|
| Form endpoint / webhook | ❌ Missing | Replace `action="#"` on all forms with GHL webhook URL or email |
| Email address | ❌ Missing | Add to contact section block |
| Physical/mailing address | ⚠️ Partial | Aliso Viejo, CA — confirm street address for footer + schema |
| Current Yelp review count | ⚠️ Verify | Currently shows "100+" — confirm exact count |
| Additional gallery photos | ⚠️ Swap | Real before/after photos replace placeholder WP images |
| Google Maps embed API | ⚠️ Optional | Replace embed URLs with client's Google Maps embed key for accuracy |

---

## DEPLOYMENT

### Static HTML on DigitalOcean Droplet
The site is static HTML — no server-side processing required.

```bash
# From existing droplet (143.198.69.46)
# Copy files to web root

scp -r acs-site/ root@143.198.69.46:/var/www/autocosmeticsolutions/

# Or via n8n deployment webhook
# Set up same pattern as Dent Time deployments
```

### WordPress / Elementor
If client wants WP admin access:
1. Install on WP Engine or similar
2. Use a base WP theme (GeneratePress or Astra)
3. Import this HTML as page templates via Elementor's Custom Code blocks
4. Or: use full-page template plugin (Elementor PRO custom templates)

**Recommendation:** Static HTML on DigitalOcean is faster to deploy, faster to load, and simpler to maintain for a site of this structure.

---

## DESIGN SYSTEM

```css
--red:       #c0392b   /* Primary accent — CTAs, highlights */
--red-hover: #a93226   /* Hover state */
--dark:      #0f0f0f   /* Deep background */
--dark-2:    #1a1a1a   /* Nav, dark sections */
--dark-3:    #252525   /* Dark cards */
--light-bg:  #f4f4f2   /* Alternating light sections */
--white:     #ffffff
--text:      #2a2a2a   /* Body text */
--text-mid:  #555      /* Secondary text */
--font-head: 'Barlow Condensed' — headlines, nav, labels
--font-body: 'Barlow' — all body copy
```

---

## NOTES FOR AI OPS SQUAD PROPOSAL

This site was built as a full turnkey delivery:
- 1 homepage (all sections, schemas, SEO meta)
- 1 service page template (cloneable × 12)
- 1 city page template (cloneable × 19)
- Populated spec document
- This README

**Total pages to deliver:** 32 (1 homepage + 12 service + 19 city)

**Remaining work to quote separately:**
- About, Gallery, FAQ, Contact standalone pages
- Form backend wiring (GHL webhook)
- Deployment + DNS
- Ongoing city page / service page generation automation (n8n workflow)

---

*Site by AI Ops Squad — aiopssquad.com*
*Build date: 2025*
