# Nexa AgroFeeds — Strategic Marketing Analysis & Quarterly Action Plan

**One-liner:** A one-page marketing effectiveness review — ROMI per campaign, competitor
ladder, gap arithmetic, Target Operating Model and the next-quarter plan — built as a single
static HTML deck with CSV datasets behind it.

## Problem

A feed business had spent a quarter of marketing money and could answer neither of two
questions: *did the spend pay back*, and *what exactly would it take to move up the
industry ranking?* Evidence lived in separate workbooks (campaign spend, industry volumes,
digital audit, brand maturity scorecard, budget planner), each with its own definition of
"actual". Reviews turned into debates about numbers instead of decisions.

## Solution

One printable page that turns the evidence into a chain of arithmetic the reader can audit:

1. **Campaign performance (ROMI)** — topline and profit ROMI per campaign period, a
   24-campaign spend detail, budget-vs-actual utilisation by channel, top/bottom five.
2. **Competitor analysis** — a volume ladder of 16 companies (share, growth, distance to
   the next rank) plus a competitor digital benchmark (presence, engagement, paid, search).
3. **Gap table** — every gap stated with its formula in a hover tooltip
   (`benchmark − us = gap`), so no percentage is quoted without its unit.
4. **TOM (Target Operating Model)** — People / Process / Technology gaps paired one-to-one
   with solutions, each mapped to a budget line, owner and target.
5. **Q2 action plan** — "from finding to action" table, segment priority scoring, ICP
   table, channel budget proposal, month calendar and a monthly scorecard linked to the CSVs.

## Features

- Single self-contained `index.html` + three small CSVs; no framework, no build step.
- ROMI model that states its own formulas (marketing-led revenue, 16% gross margin, hurdle rate).
- Gap arithmetic shown on hover, so every displayed difference is reproducible by hand.
- CSS-bar charts rendered from two small JS arrays (market share, growth, budget utilisation)
  — no chart library, prints cleanly.
- Scroll-spy navigation, collapsible detail tables, print/PDF-friendly stylesheet.
- Dark-mode support through CSS custom properties.
- Every claim tied to a downloadable demo dataset referenced in-page (`data/*.csv`).

## Tech stack

- Vanilla JavaScript (ES5-style, no dependencies), semantic HTML5, CSS3 custom properties
- Data as CSV files in `data/`; report values hard-set from those datasets
- Static hosting only (any CDN / object storage); works from the local file system

## Synthetic demo data — disclaimer

This is a portfolio copy of a real engagement. All company names are **fictional**
(NexaGroup, Nexa AgroFeeds and the competitor set — Nutrimax, Zenith Feed, New Dawn Feeds,
Sunrise, Apex Feeds, Delta Feed, Pinnacle, Regal Feeds, Riverine Feeds, Shanti Feeds,
Tarna Feed, Vitalis Feed, Karim, Ashroy, Anwar), and every monetary and volume figure has
been rescaled by a single multiplicative factor with a synthetic industry base. Because one
factor is applied to absolute amounts only, all ratios that the page displays — market
shares, growth rates, ROMI multiples, utilisation percentages, gap differences and the
price-per-MT assumption — stay internally consistent, while the underlying numbers describe
no real company. Internal workbook links, spreadsheet URLs and file names were removed and
replaced with the three demo CSVs. No confidential or personal data is present.

## Run locally

No install, no build:

```bash
# just open it
start index.html          # Windows
open index.html           # macOS
xdg-open index.html       # Linux

# or serve it (needed if you want the data/*.csv links to open in the browser)
npm run dev               # npx serve -l 5173 .
python -m http.server 8000
```

## Deploy

Import the folder into Vercel (or Netlify / GitHub Pages) as a static project — framework
preset "Other", no build command, no output directory. `index.html` is served as-is and
`data/` is reachable at `/data/...`.
