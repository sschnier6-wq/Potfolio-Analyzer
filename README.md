# Portfolio Analyzer — Mobile Web App

A fully **client-side** portfolio tool for iPhone Safari (and desktop browsers).  
All processing happens in your browser. Your statements and balances **never leave your device**.

**Current version:** v49

---

## Quick start (iPhone)

### Recommended: GitHub Pages

1. Put these files in a public GitHub repo (same folder):
   - `index.html`
   - `xlsx.min.js` (Excel support)
   - `apple-touch-icon.png`, `favicon.png`, `icon-192.png` (optional home-screen icons)
2. Enable **Settings → Pages → Deploy from branch** (root).
3. Open: `https://YOUR-USER.github.io/YOUR-REPO/?v=49`
4. Safari → Share → **Add to Home Screen**.

Use a `?v=49` (or newer) cache-buster after updates, or clear Website Data for the site.

### Privacy when sharing the link

The public URL only serves the **app code**.  
Positions, prices, home values, and Roth inputs live in **that browser’s `localStorage` only**.  
Someone else opening the same link gets a blank app on their device.

---

## What it does

### Load accounts
- Upload **multiple** CSV / Excel files from **Fidelity**, **E\*TRADE**, **RW Baird**, and similar brokers
- Toggle which files are included with chips at the top
- Kids’ / 529 Baird accounts can be excluded by account suffix
- Data stays in the browser until you Clear

### Overview
- Live-ish valuation: **Refresh prices** uses Yahoo prior closes; annuities can scale with SPY
- **Asset class mix** pie (equities, bonds, cash, annuities, real estate, …)
- **Equity & style mix** pie (large blend/growth/value, mid/small, international, bonds, …)
- Allocation by account, top holdings, holdings summary
- Optional **Home valuation**: enter address/label + your own dollar value (no online lookup)

### Positions
- By ticker with latest price; tap price to toggle **$ vs %** change
- Green / red vs prior refresh
- Tap ticker → Yahoo Finance

### Look-thru
- ETF / fund look-through (e.g. VOO, QQQ, QQQM, QQQJ) with weight heatmap
- Overlap / concentration (**HHI**) and diversity commentary with suggested funds

### Optimize
- Per-holding peer suggestions (expense ratio / risk role)
- Research links: Yahoo, Morningstar, ETF.com

### Roth (conversion + spending)
- **Birth year** → RMD age under SECURE 2.0 (73 if born 1951–1959; **75** if 1960+)
- Detects Traditional IRA, 401(k), Roth, and taxable balances from account names
- Year-by-year **Roth conversion** plan filling a chosen federal bracket (12% / 22% / 24%)
- **IRMAA** tier flags, **NIIT** risk notes, early-withdrawal penalty notes
- **Annual spending** from a start age (default 60): draw order **RMD → taxable → IRA → 401(k) → Roth**
- Spending schedule shows **spend, IRA balance, 401(k) balance, Roth balance, RMD** each year
- First-RMD summary: balance and RMD **with plan vs no conversions**, plus estimated tax difference

---

## Files to deploy

| File | Required | Purpose |
|------|----------|---------|
| `index.html` | Yes | App |
| `xlsx.min.js` | Yes | Excel (.xlsx) parsing |
| `apple-touch-icon.png` | Recommended | iOS home-screen icon |
| `favicon.png` / `icon-192.png` | Optional | Browser / PWA icons |
| `README.md` | Optional | This doc |

---

## Broker tips

- Prefer **CSV** exports when possible.
- **Excel** works via the bundled SheetJS file (same origin as the page).
- Account type for Roth planning is inferred from names (`IRA`, `Roth`, `401k`, `Rollover`, etc.). If detection looks wrong, check labels in the export.
- Values and lots come from your statements; price refresh is best-effort (Yahoo chart API).

---

## Privacy

- No login, no backend, no analytics endpoint for your holdings.
- `localStorage` keys are local to the origin (e.g. your github.io site).
- Clearing Safari Website Data for the site wipes holdings and Roth settings on that device.

---

## Disclaimer

This tool is for **personal organization and planning sketches only**.  
It is **not** tax, investment, or legal advice. Confirm conversions, RMDs, IRMAA, and withholding with a qualified advisor or CPA. Bracket and IRMAA figures are approximate and change with law and inflation.
