# Portfolio Analyzer — Mobile Web App

Fully **client-side** portfolio tool for iPhone Safari (and desktop).  
Statements and balances **never leave your device**.

**Current version:** **v55**

---

## Quick start (iPhone)

### GitHub Pages

1. Put these files in a public repo (same folder):
   - `index.html`
   - `xlsx.min.js`
   - `apple-touch-icon.png`, `favicon.png`, `icon-192.png` (home-screen icons)
2. **Settings → Pages → Deploy from branch** (root).
3. Open: `https://YOUR-USER.github.io/YOUR-REPO/?v=55`
4. Safari → Share → **Add to Home Screen**.

After updates, bump `?v=55` (or clear Website Data for the site).

### Privacy when sharing the link

The URL only serves **app code**. Positions, prices, home values, Roth/Budget inputs live in **that browser’s `localStorage` only**. Another person opening the same link sees a blank app on *their* device.

---

## Features (v55)

### Load accounts
- Multiple **CSV / Excel** files: **Fidelity**, **E\*TRADE**, **RW Baird**, similar brokers
- Toggle files with chips; **All / None**
- Exclude kids’ / 529 Baird accounts by suffix
- Optional **Home valuation** (manual address + dollar value; include/exclude from totals)

### Overview
- Metrics: investments, home, net-ish total, tickers / accounts
- **Live-ish valuation**
  - **↻ Refresh prices** button
  - **Pull down from the top of the screen** (iPhone) to refresh prices
  - Yahoo prior close via CORS-safe proxies (paced requests + retries)
  - Cash / money markets @ $1
  - Lincoln / Jackson index annuities scaled by **SPY** vs statement baseline
  - Failed symbols listed when some tickers can’t be priced
- **Asset class mix** pie + detail
- **Equity / style mix** pie (growth, large, small, international, bonds, …)
- Allocation by account, top holdings

### Positions
- By ticker; latest price; tap price for **$ ↔ %** change
- Green / red vs prior refresh
- Tap ticker → Yahoo Finance

### Look-thru
- ETF / fund holdings heatmap (VOO, QQQ, QQQM, QQQJ, …)
- Overlap / **HHI** concentration + diversity commentary

### Optimize
- Peer / lower-cost alternatives with research links (Yahoo, Morningstar, ETF.com)

### Budget (left of Roth)
- **Guyton–Klinger-style guardrails**
- Base rate from equity mix: **3.5% / 4.0% / 4.5%**
- **Safe spend range** this month (lower rail – upper rail) + recommended amount inside the band
- Re-evaluates when you **refresh prices** or portfolio value moves
- Optional inflation (January), include-home toggle, manual override, reset rails
- Next-12-months schedule

### Roth
- Birth year → RMD age (SECURE 2.0: **75** if born 1960+)
- Auto-detects Traditional IRA / 401(k) / Roth / taxable from account names
- Year-by-year conversions to a chosen federal bracket
- **Automatically compares avoid-IRMAA vs full-bracket** and picks the lower estimated all-in cost
- IRMAA / NIIT notes; spending schedule (IRA / 401k / Roth balances + RMD)
- First-RMD with-plan vs no-conversion summary

---

## Why price refresh was failing (and the fix)

Browsers block direct Yahoo Finance calls (**CORS**). Older builds hit dead or rate-limited proxies (`corsproxy.io` keyless URLs, allorigins bursts with 4 parallel workers), so most symbols failed while a few succeeded.

**v55 changes:**
1. Try **direct Yahoo** (query1 / query2), then **allorigins `/get`** (parse `contents`), then **allorigins `/raw`**
2. **Retry once** on transient failures
3. **2 paced workers** (~120 ms between symbols) instead of a 4-wide blast
4. List **failed tickers** under Live-ish valuation
5. **Pull-to-refresh** from the top of the page on iPhone

CUSIPs, internal `NON*` codes, and unmapped symbols still use **statement value** (not priced).

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
