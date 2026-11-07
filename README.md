![Agro Marketing Analytics](assets/banner.svg)

# Nexa AgroFeeds — Strategic Marketing Analysis · portfolio demo

[![Deployed on Vercel](https://img.shields.io/badge/Vercel-Live%20demo-0F172A?style=flat&logo=vercel&logoColor=white)](https://vercel.com "Live demo placeholder") [![Static app](https://img.shields.io/badge/build-none%20required-10B981?style=flat)](#run-locally) [![Data](https://img.shields.io/badge/data-synthetic-F59E0B?style=flat)](#demo-data-disclaimer)

A one-page, self-contained **marketing-effectiveness review** for a *fictional* feed
business ("Nexa AgroFeeds", part of NexaGroup). Part A reads a quarter of marketing
spend and answers the two questions a review always gets stuck on — *did the money
pay back* (ROMI per campaign) and *what would it take to move up the industry ladder*
(share, growth, gap arithmetic) — then a Target Operating Model and brand-maturity
audit turn each finding into a costed Q2 action with an owner and a target. Dark,
data-dense deck UI (Fira Sans / Fira Code), CSS-bar charts, no framework, no build
step, no backend.

![Deck screenshot](assets/banner.png)

## Quick start

```bash
open index.html       # macOS  · Windows: start index.html · Linux: xdg-open index.html
npm run dev           # optional: npx serve -l 5173 .  (needed for the data/*.csv links)
```

## Features

* **Campaign performance (ROMI):** marketing-led revenue vs the 30% target, topline and profit ROMI per campaign period, a 24-campaign spend detail and top/bottom five.
* **Competitor analysis:** a 16-company volume ladder (share + growth + distance to the next rank) and a digital benchmark (presence, engagement, paid, search).
* **Gap arithmetic:** every gap states its own formula in a hover tooltip (`benchmark − us = gap`); no percentage is quoted without its unit.
* **Target Operating Model + brand-maturity audit:** People / Process / Technology gaps paired one-to-one with solutions, each mapped to a budget line, owner and target.
* **Q2 action plan:** "finding → solution" table, weighted segment-priority scoring, ICP targeting, channel budget proposal, month calendar and monthly scorecard.
* **Design system:** spec-v2 dark-navy tokens with a light-theme toggle, sticky scroll-spy top bar, KPI hover lift, CSS-bar charts with legends and reference lines, focus-visible rings, reduced-motion support, print/PDF-friendly.
* **Charts from small JS arrays** — no chart library; scroll-spy nav and collapsible detail tables in vanilla ES5-style JS.

## Layout

```
index.html    self-contained deck (markup + embedded CSS + CSV-derived figures + chart scripts)
data/         campaign_spend_demo.csv · sales_monthly_demo.csv · industry_share_demo.csv
assets/       banner.png (screenshot)
PROFILE.md    research-style methodology (formulas, frameworks, validity)
package.json  dev/start scripts only — no dependencies
```

## Demo-data disclaimer

Every company name is **fictional** — NexaGroup, Nexa AgroFeeds and the competitor set
(Nutrimax, Zenith Feed, New Dawn Feeds, Sunrise, Apex Feeds, Delta Feed, Pinnacle, Regal
Feeds, Riverine Feeds, Shanti Feeds, Tarna Feed, Vitalis Feed, Karim, Ashroy, Anwar).
Every monetary and volume figure is **synthetic**, rescaled by a single multiplicative
factor over a synthetic industry base; because one factor is applied only to absolute
amounts, the ratios the page shows (shares, growth, ROMI multiples, utilisation, gaps,
price-per-MT) stay internally consistent while describing no real company. No
confidential or personal data is present.

## Deploy on Vercel

Import the folder as a static project — Framework Preset **Other**, no build command, no
output directory. `index.html` is served as-is and `data/` is reachable at `/data/…`.

## License

MIT — sample portfolio project. Built by Abir.
