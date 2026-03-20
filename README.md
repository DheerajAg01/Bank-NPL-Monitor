# 🏦 Bank NPL Concentration Monitor

**Real-time distressed loan sourcing intelligence powered by live FDIC Call Report data.**

A single-file dashboard that screens community and regional banks for rising nonperforming loan concentrations using publicly filed regulatory data. Built to identify which institutions are likely approaching loan disposition decisions — before those assets hit the market.

**Live Dashboard:** `https://dheerajag01.github.io/Bank-NPL-Monitor/`

---

## What This Does

Deal flow in distressed debt depends on relationships with bank workout officers and loan sales desks. This tool systematically monitors public FDIC call report filings to flag banks accumulating NPL concentrations, giving you early sourcing signals before loans are marketed.

The dashboard pulls live data from the FDIC BankFind Suite API, computes a composite distress score for each institution, and classifies them into actionable sourcing phases.

---

## Signals Tracked

- **NPA / Total Assets** — Schedule RC-N noncurrent loans as a percentage of total assets
- **Net Charge-Off Rate** — Schedule RI-B net loan losses annualized against average loans
- **Texas Ratio** — (Noncurrent Loans + OREO) / (Tangible Equity + ALLL), the single best predictor of forced disposition
- **Classified / Capital** — Past-due exposure relative to total capital, the metric examiners use for MOUs
- **Provision Build** — When provisions outpace charge-offs, management is signaling they expect more losses ahead
- **ALLL Coverage Ratio** — Loan loss reserves relative to noncurrent loans, indicates remaining buffer

---

## Distress Scoring

Each bank receives a composite score from 0 to 100 based on weighted signal inputs, then gets classified into a sourcing phase:

| Score | Phase | What It Means | Your Action |
|-------|-------|---------------|-------------|
| 70–100 | **Likely Selling / Workout Active** | Active special assets desk, regulatory pressure driving disposition | Contact SVP Special Assets, reference public call report deterioration |
| 50–69 | **Stress Emerging** | Internal credit committee discussions likely underway | Build relationship with CLO, offer portfolio review framework |
| 30–49 | **Early Watch** | Deterioration signals emerging, not yet at decision stage | Add to quarterly watchlist, begin outreach for first-mover positioning |
| 0–29 | **Performing** | Well-managed portfolio, limited distress indicators | Low priority, monitor for trend changes |

---

## Features

- **Live FDIC API integration** — pulls directly from banks.data.fdic.gov, no stale data
- **8-quarter trend analysis** — tracks trajectory across two full years of call report filings
- **Sortable and filterable** — by state, asset size tier, distress phase, or free-text search
- **Click-to-expand detail panel** — full metric cards with sparklines, bar charts, signal flags, and sourcing playbook
- **Sourcing playbook** — each bank gets a tailored outreach strategy based on its distress phase, including who to target and how to frame the conversation
- **Zero dependencies** — single HTML file, runs entirely in the browser, no backend or build step

---

## Screen Parameters

- **State** — filter to any US state or screen nationally
- **Size Tier** — Community (<$1B), Small Regional ($1B–$10B), Regional ($10B–$50B), or Custom Range
- **Phase Filter** — isolate just the "Likely Selling" names or focus on your "Early Watch" pipeline
- **Name/City Search** — find specific institutions

---

## Data Source

All data comes from the FDIC BankFind Suite API (`banks.data.fdic.gov/api`). This is a public API maintained by the Federal Deposit Insurance Corporation — no API key or authentication required. Financial data is updated quarterly when institutions file call reports with their regulators.

### Call Report Schedules Used

- **Schedule RC-N** — Past Due and Nonaccrual Loans
- **Schedule RC-O** — Other Real Estate Owned
- **Schedule RI-B** — Charge-Offs and Recoveries
- **Schedule RC-R** — Regulatory Capital

---

## Setup

No build step. No dependencies. No server.

1. Clone this repo
2. Open `index.html` in a browser

Or host it anywhere that serves static files.

---

## Deployment

### GitHub Pages

1. Push `index.html` to a GitHub repo
2. Go to Settings → Pages → Source → select `main` branch, root `/`
3. Dashboard goes live at `https://YOUR_USERNAME.github.io/REPO_NAME/`

### Other Options

Works with Vercel, Netlify, Cloudflare Pages, S3, or any static hosting. Just upload the single file.

---

## Disclaimer

This tool is for informational and research purposes only. Distress scores are derived from publicly available regulatory filings and are indicative screening signals — not investment advice. Always verify with direct institution contact and independent due diligence before any outreach or transaction. Not affiliated with the FDIC.

---

## License

MIT
