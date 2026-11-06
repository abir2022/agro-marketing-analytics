# Nexa AgroFeeds — Strategic Marketing Analysis & Quarterly Action Plan

*Research-style methodology profile for a synthetic portfolio deck.*
All entities and figures are fictional and synthetic (see §8). Formulas and frameworks are
the analyst's working conventions, restated here so every number on the page is reproducible.

---

## 1. Abstract

This artefact turns one quarter of marketing spend at a fictional compound-feed business
(Nexa AgroFeeds) into a single, auditable narrative. It pairs two review lenses the same team
would otherwise debate in separate spreadsheets. The first is a **ROMI ledger** — marketing-led
revenue, topline and profit return on marketing investment per campaign period, budget
utilisation by channel, and top/bottom campaigns — so the question "did the money pay back?" is
answered from one dataset. The second is **market-share and gap analysis** — a competitor volume
ladder (share, growth, distance to the next rank) plus a per-metric gap table in which every
difference states its own formula. A **brand-maturity audit** (a five-level capability checklist)
and a **Target Operating Model** (People / Process / Technology) then convert each finding into a
costed next-quarter action with a budget line, owner and measurable target. The build is a
self-contained static HTML deck with CSS-bar charts and three small CSVs; no framework, no
backend, no build step. The result reads as a presentation, but every claim resolves to an
arithmetic expression the reader can check by hand against the demo data.

## 2. Problem Framing

A feed business had spent a quarter of marketing money and could answer neither of two questions:
*did the spend pay back*, and *what exactly would it take to move up the industry ranking?*
Evidence lived in separate workbooks — campaign spend, industry volumes, a digital audit, a brand
maturity scorecard, a budget planner — each with its own definition of "actual". Reviews therefore
drifted into arguments about numbers rather than decisions about actions. The deck exists to give
one page that (a) states each metric's formula once, (b) shows the competitor ladder and the exact
gap to the next rank, and (c) maps every finding to a named owner, budget line and target, so the
same evidence becomes an executable next-quarter plan.

## 3. Related Practice

Marketing-effectiveness reviews commonly lean on a small set of analyst conventions rather than a
single standard. **ROMI ledgers** treat marketing as an investment line and compute a return
multiple per campaign, distinguishing top-line (revenue) from bottom-line (profit) payback.
**Market-share analysis** reads share of market and share of growth over a fixed competitor set,
often visualised as a BCG-style ladder to expose where volume is actually available. **Competitive
gap / benchmark tables** express each shortfall as `benchmark − us` with an explicit unit, so a
"percentage gap" is understood as percentage *points*, not a share of the benchmark. **Capability
maturity models** score an operating model against an L1→L5 checklist (foundation → build →
measure → scale → intelligence). This deck combines all four lenses; no external source or company
statistic is cited because the underlying engagement and its benchmarks are synthetic.

## 4. Methodology & Data Design

Three demo CSVs sit behind the page. Report values are transcribed from them; charts are drawn
from two small JS arrays so the deck stays dependency-free and prints cleanly.

- `campaign_spend_demo.csv` — Q1 campaign-level spend, category, period and the model's topline /
  profit ROMI; Q1 budget-vs-actual by channel; proposed Q2 budget by channel.
- `sales_monthly_demo.csv` — monthly volume (MT), revenue (BDT crore), sales and marketing-revenue
  targets, marketing-led revenue, achievement multiple; Q2 scorecard.
- `industry_share_demo.csv` — fictional competitor volumes, share, growth and digital counters.

**Metric definitions (formulas as shown in the UI):**

| Metric | Definition |
|---|---|
| Volume | revenue ÷ realised price; realised price ≈ ৳58,915/MT |
| Marketing-led revenue | (monthly revenue − 6-month organic base) × campaign-spend share; base = 6-month average organic sales (৳23.7 Cr/month) |
| Achievement vs target | marketing-led revenue ÷ marketing-revenue target, target = 30% of monthly sales target |
| Topline ROMI | (marketing-led revenue − spend) ÷ spend |
| Profit ROMI | (marketing-led profit − spend) ÷ spend, with marketing-led profit = marketing-led revenue × 16% gross margin |
| Channel utilisation | actual spend ÷ plan spend |
| Market share | company monthly volume ÷ industry monthly volume (industry base = 620,000 MT/month) |
| Growth vs 2025 | (Jan–Aug'26 monthly average − 2025 average) ÷ 2025 average |
| Gap | benchmark − Nexa; **%** = percentage-point difference, **MT** = volume per month, **×** = ROMI multiple |
| Segment priority score | 0.25·size + 0.20·growth + 0.25·right-to-win + 0.15·competitive-intensity + 0.15·margin, each scored 1–5 (higher intensity score = less crowded) |
| Brand-maturity audit | count of "Yes" across a 39-check, five-level ladder (L1 Foundation → L5 Intelligence) |

Transformation is arithmetic only: absolute amounts are rescaled by a single factor (§8), so ratios
derived from them — shares, growth, ROMI multiples, utilisation, gap differences, price-per-MT —
are left internally consistent.

## 5. Analytical Framework

The UI encodes a decision chain. Part A diagnoses, Part B treats:

1. **Is growth real?** Compare Nexa's volume growth (+96% on 2025) with the industry (+5.6%) and
   with each competitor — growth that beats the market is the only defensible signal.
2. **Did spend pay back?** Every campaign period must clear a profit-ROMI hurdle; the deck reports
   ranges against a stated 1.0× minimum and flags where spend shifted out of brand-building
   (ATL/digital) into trade/gift lines that outran plan.
3. **How far to the next rank?** The ladder above Nexa turns "get bigger" into a concrete
   MT/month requirement to overtake rank #14, #13 and #10; the gap table repeats the arithmetic per
   metric so no target is soft.
4. **What closes the gap?** Each gap is attributed to a People / Process / Technology root cause,
   paired with exactly one solution, then costed into a Q2 budget line with an owner, timing and a
   monthly-reviewable target.

Because maturity and TOM are scored on fixed rubrics, the framework is re-runnable each quarter:
same formulas, same ladder, only the numbers change.

## 6. System Design

- **Architecture:** a single self-contained `index.html` (markup + embedded `<style>` design system
  + embedded figures) with three `data/*.csv` files linked for provenance. `package.json` exposes a
  static `serve` for the CSV links; there is no bundler or runtime.
- **Rendering:** report tables are static HTML so they print and screen-read reliably; the three
  bar charts (budget utilisation, market share, growth) are generated by vanilla ES5-style JS from
  two arrays, using CSS gradients / positioned fills — no chart library. Scroll-spy and collapsible
  detail tables are small DOM handlers; a separate script toggles a `data-theme` attribute.
- **Design system:** spec-v2 dark-navy tokens (blue + amber accents only), Fira Code for numerals /
  headings and Fira Sans for body, one card and one radius scale, KPI hover lift, legends and
  reference lines on every chart, focus-visible rings, an equal-edge container, and a
  `prefers-reduced-motion` guard on the single first-paint stagger.
- **Why static:** the deliverable is a read-only quarterly review; static files keep it offline-capable,
  versionable and trivially hostable, and remove any dependency on a live backend.

## 7. Findings & Design Decisions

The synthetic story the data tells: Nexa grew far faster than the market (+96% vs +5.6%) and beat
its quarterly volume plan (~104%), and every campaign period cleared the profit-ROMI hurdle
(≈17.1×–58.6×) — but growth is off a small base (≈2.4% share, rank #15), spend drifted from brand
building into trade/gift lines running at multiples of plan, and ROMI is not yet measurable per
campaign. Overtaking rank #13 is quantified at roughly +4,827 MT/month.

Key UI choices follow from that: charts and numbers are the hero (no filler, no invented quotes);
the hero states the four headline findings before any detail; each gap carries a hover formula so
the reader can audit it; the TOM pairs gaps and solutions one-to-one; and Q2 turns findings into
owners and targets. Design-wise the deck stays a presentation — narrative sections, a sticky
scroll-spy bar carrying the "Synthetic demo data" chip and theme toggle, a fixed navy hero band,
KPI cards with subtle hover lift — while adopting the same tokens, palette and motion rules as the
rest of the portfolio.

## 8. Limitations & Validity

- **Synthetic data.** Every company (NexaGroup, Nexa AgroFeeds and the competitor set — Nutrimax,
  Zenith Feed, New Dawn Feeds, Sunrise, Apex Feeds, Delta Feed, Pinnacle, Regal Feeds, Riverine
  Feeds, Shanti Feeds, Tarna Feed, Vitalis Feed, Karim, Ashroy, Anwar) is **fictional**.
- **Rescaling.** Monetary and volume figures are regenerated by applying a single multiplicative
  factor over a synthetic industry base. Internal workbook links, spreadsheet URLs and file names
  were removed and replaced by the three demo CSVs. No confidential or personal data is present.
- **Scope / validity.** Because one factor is applied only to absolute amounts, the *ratios* shown
  remain internally consistent, which is what the analysis argues from; the absolute magnitudes
  describe no real business. Segment scores, channel splits and maturity levels are drafts meant to
  demonstrate method, not measured truth. No academic citation or real-company statistic is asserted.

## 9. Reproducibility & Deployment

```bash
# Run locally — no install, no network for the deck itself
start index.html            # Windows  ·  open index.html (macOS)  ·  xdg-open index.html (Linux)

# Optional: serve so the data/*.csv provenance links open in the browser
npm run dev                 # npx serve -l 5173 .
python -m http.server 8000
```

**Deploy:** import the folder into Vercel (or Netlify / GitHub Pages) as a static project — Framework
Preset **Other**, no build command, no output directory. `index.html` is served as-is and `data/` is
reachable at `/data/…`. There are no environment variables and no secrets; the theme preference is
stored only in the browser's `localStorage`.
