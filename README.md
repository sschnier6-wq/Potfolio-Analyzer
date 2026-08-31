# Portfolio Analyzer — Mobile Web App

Fully **client-side** portfolio tool for iPhone Safari (and desktop).  
Statements and balances **never leave your device**.

**Current version:** **v63**

---

## Quick start (iPhone)

### GitHub Pages

1. Put these files in a public repo (same folder):
   - `index.html`
   - `xlsx.min.js`
   - `apple-touch-icon.png`, `favicon.png`, `icon-192.png` (home-screen icons)
2. **Settings → Pages → Deploy from branch** (root).
3. Open: `https://YOUR-USER.github.io/YOUR-REPO/?v=63`
4. Safari → Share → **Add to Home Screen**.

After updates, bump `?v=63` (or clear Website Data for the site).

### Privacy when sharing the link

The URL only serves **app code**. Positions, prices, home values, Roth/Budget inputs live in **that browser’s `localStorage` only**. Another person opening the same link sees a blank app on *their* device.

---

## Features (v63)

### Load accounts
- Multiple **CSV / Excel** files: **Fidelity**, **E\*TRADE**, **RW Baird**, similar brokers
- Toggle files with chips; **All / None**
- Exclude kids’ / 529 Baird accounts by suffix
- Optional **Home valuation** (manual address + dollar value; include/exclude from totals)

### Overview
- Metrics: investments, home, net-ish total, tickers / accounts
- **Live-ish valuation**
  - **↻ Refresh prices** and **pull-down** on iPhone
  - Yahoo / Nasdaq / optional Finnhub key
  - Cash @ $1; Lincoln / Jackson annuities scaled by SPY
- **Asset class mix** and **equity / style mix** pies
- Allocation by account, top holdings

### Positions
- By ticker; latest price; tap price for **$ ↔ %** change
- Green / red vs prior refresh
- Tap ticker → Yahoo Finance

### Look-thru
- ETF / fund holdings heatmap (VOO, QQQ, QQQM, QQQJ, …)
- Overlap / **HHI** concentration + diversity commentary

### Optimize
- Peer / lower-cost alternatives with research links

### Budget
- **Guyton–Klinger-style guardrails** (3.5% / 4.0% / 4.5% by equity mix)
- Safe spend **range** + recommended amount
- **Past 12 months** reconstructed from first-of-month prices
- One sequential walk; current month is the last step of that walk

### Roth
- Birth year → RMD age (SECURE 2.0: **75** if born 1960+)
- Detects Traditional IRA, 401(k), Roth, taxable from account names
- Year-by-year conversions; auto-compares avoid-IRMAA vs full-bracket
- Spending schedule (IRA / 401(k) / Roth balances + RMD)
- First-RMD with-plan vs no-conversion snapshot
- **RMD-era tax table, first RMD year through age 95**
  - Each year: RMD if you leave 401(k)/IRA in place, tax on that RMD, tax if you follow the conversion plan, tax saved
  - Summary: sum of RMDs, sum of taxes with/without conversions, **total RMD-era tax saved through age 95**
  - Uses IRS Uniform Lifetime Table divisors through age 95 and the plan growth rate
  - **Net tax savings of conversions** = RMD-era tax avoided − conversion tax paid before RMDs (spending withdrawals excluded from that conversion-tax figure)
  - Not present-valued; estimates only

---

## Files to deploy

| File | Required | Purpose |
|------|----------|---------|
| `index.html` | Yes | App |
| `xlsx.min.js` | Yes | Excel parsing |
| `apple-touch-icon.png` | Recommended | iOS home screen |
| `favicon.png` / `icon-192.png` | Optional | Icons |
| `README.md` | Optional | This doc |

---

## Local only

No server, no accounts, no analytics. Clear data anytime with **Clear**.
