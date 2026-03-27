# Creative Force + Dreem — Pricing Page Mockup

Internal design mockup for the combined CF + Dreem pricing page. Not customer-facing.

---

## What this is

A single-file HTML mockup (`index.html`) exploring how to present Creative Force and Dreem as a unified product on one pricing page. Covers:

- Plan cards (Core + Enterprise) with embedded Dreem credit callouts
- AI Content Generation section (Dreem-styled, dark)
- Credit capacity section (contract-level reference table)
- Add-ons
- Feature comparison table with Dreem AI dark takeover block
- FAQ with Dreem-specific credit questions
- Interactive credit info panel (click the `i` icon on either plan card)

---

## Design system

Two brand systems in use — do not mix their tokens:

**Creative Force** (`/design/cf-tokens.md`)
- Font: Inter
- Primary: `#2741f1` (blue), `#1b1a3d` (navy), `#040087` (deep blue)
- Background: `#f3f3f8`
- Cards: `border-radius: 24px`, shadow: `rgba(39,65,241,0.10) 0px 0px 40px`

**Dreem** (`/design/dreem-tokens.md`)
- Font: Space Grotesk (headings), Inter (body)
- Accent: `#3ecf6e` (green)
- Backgrounds: `#060606` (page), `#121212` (surface), `#1a1a1a` (elevated)
- Cards: `border-radius: 15px`, border: `#2b2b2b`

**Rule:** CF sections use CF tokens. Dreem sections (AI block, credit capacity, compare table Dreem rows) use Dreem tokens. Hard cuts between sections — no gradient blending.

---

## Page structure

```
hero-wrapper (CF gradient: #1b1a3d → #040087)
  ├── internal-banner
  ├── nav (CF + Dreem CTA)
  ├── hero
  └── plan-cards (Core + Enterprise)

ai-section (Dreem: #060606)
  └── 4 AI feature cards + 1 "in development" card

topup-section (Dreem: #060606)
  └── credit capacity reference table

addons-section (CF light: #f3f3f8)
  └── 4 add-on cards

compare-section (CF light: #f3f3f8)
  └── compare table
      ├── Platform rows (CF white card column)
      ├── Planning rows
      ├── dreem-header-row + dreem-rows (full dark takeover)
      ├── Reporting rows
      ├── Support rows
      └── Security rows

faq-section (CF light)
footer-cta (CF gradient)

#creditPanel (modal, triggered by i icon on plan cards)
#creditOverlay (backdrop)
```

---

## Key decisions still open

| # | Decision | Status |
|---|---|---|
| 1 | Credits vs. assets terminology (Lane 1 = keep credits, Lane 2 = per-image pricing) | Pending — discuss with Matthias |
| 2 | Minimum credit allocation for Core: 500 or 1,000/mo? | Pending |
| 3 | "Powered by Dreem" vs "Creative Force AI" brand language | Pending — brand review with Marianne |
| 4 | BYOM (bring your own model) policy | Unresolved |
| 5 | Should Color Variations stay on page as "in development"? | Pending |

---

## Deployment

This is a single self-contained HTML file. No build step, no dependencies.

**Vercel:** Drop `index.html` into a new Vercel project. Enable Password Protection in Project Settings.

**GitHub → Vercel (recommended for team iteration):**
```bash
git init
git add .
git commit -m "initial pricing mockup"
git remote add origin <your-private-repo>
git push origin main
```
Then connect the repo to Vercel. Auto-deploys on every push.

---

## How to update with Claude Code

The file is entirely self-contained CSS + HTML. Key areas to edit:

- **Plan card copy/pricing** → search `plan-card` in `index.html`
- **Credit callout** → search `dreem-callout`
- **Credit info panel content** → search `credit-panel-body`
- **AI feature cards** → search `ai-section`
- **Credit capacity table** → search `topup-section`
- **Compare table** → search `compare-table`
- **FAQ answers** → search `faq-answer`
- **Dreem row styling** → search `.dreem-row` in `<style>`

---

## Pricing data reference

| Action | Credits | Cost (enterprise annual) |
|---|---|---|
| Virtual Model 2K | 11 cr | $0.66 |
| Virtual Model 4K | 14 cr | $0.84 |
| Packshot 2K | 8 cr | $0.48 |
| Image-to-Video 5s | 10 cr | $0.60 |
| Image Refining | 4 cr | $0.24 |

Credit top-up blocks: 500 ($59) · 2,000 ($199) · 10,000 ($899) · 50,000 ($4,199)

Traditional on-model photography: $61–$245/image. Virtual: $0.66. Up to 371x cheaper.
