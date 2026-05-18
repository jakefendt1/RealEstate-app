# Net Proceeds Calculator v2

A single-file seller net proceeds calculator for real estate transactions. Estimates your take-home cash after commissions, closing costs, mortgage payoff, taxes, and prorations — with Conservative / Expected / Optimistic scenario comparison.

---

## Quick Start

Open `index.html` directly in any modern browser — no server, build step, or internet connection required (fonts and React load from CDN on first open).

To deploy to Vercel:
1. Push `index.html` to a GitHub repo (already set up at `RealEstate-app`)
2. Import the repo at [vercel.com](https://vercel.com)
3. Vercel detects a static site automatically — click **Deploy**
4. Done. Every push to `main` auto-deploys.

---

## Features

| Feature | Details |
|---|---|
| **State auto-fill** | Select a state to auto-populate transfer tax rates, title insurance %, and tax billing convention |
| **Tax proration conventions** | Arrears (seller debit), Advance (seller credit), or Custom sign |
| **Mortgage interest accrual** | Separate payoff date field; per diem auto-calculated from principal × APR |
| **HOA dues proration** | Optional section with arrears/advance billing convention |
| **Misc seller debits** | 5 editable label+amount rows (utility bills, wire fees, HOA transfer, etc.) |
| **Capital gains v2** | Cost basis = purchase price + purchase closing costs + improvements list − depreciation |
| **Exclusion auto-flag** | Shows $250K (single) / $500K (MFJ) exclusion if 2+ years in primary residence |
| **Scenario toggles** | Conservative: higher costs, repair concessions, extended marketing. Optimistic: faster close. |
| **Named scenario saves** | Up to 5 named slots with timestamps, saved in localStorage separately from your working state |
| **PDF export** | jsPDF-based export with summary boxes, line items, and scenario comparison table |
| **Print stylesheet** | `Ctrl+P` / `Cmd+P` produces a clean, nav-free single-page output |
| **Mobile responsive** | Stacks cleanly on phones; inputs readable without zooming |
| **Real-time calculations** | All results update instantly as you type |

---

## Property Tax Billing Convention by State

| State | Convention | Explanation |
|---|---|---|
| **WI** | Arrears | Taxes billed Jan of following year. Seller owes through closing date. |
| **IL** | Arrears | Taxes paid in arrears, roughly 18 months behind. Seller debits buyer. |
| **MN** | Arrears | Current year taxes paid in following year. Seller debit. |
| **IA** | Arrears | Taxes billed in arrears. Seller owes their share. |
| **CA** | Advance | Taxes due Nov 1 (1st half) and Feb 1 (2nd half) for current year. Seller credit for days after closing. |
| **FL** | Advance | Taxes billed in November for the current year. If paid, seller gets credit for remaining days. |
| **TX** | Advance | Taxes due Jan 31 for prior year — effectively advance. Seller credit common. |
| **NY** | Arrears | School taxes often advance, municipal taxes in arrears. Verify with title company. |
| **CO** | Arrears | Taxes billed in January for prior year. Seller owes through closing. |
| **AZ** | Advance | Taxes billed in October for current year (2 halves). Seller credit typical. |
| **All others** | Set manually | Use the Tax Billing Convention dropdown to select the correct convention. Verify with your title company. |

> **Important:** Tax conventions can vary even within a state by county or municipality. Always confirm with your title company — the HUD/ALTA will show the exact proration at closing.

---

## Transfer Tax Rates by State (Pre-loaded Defaults)

| State | State Rate | County Rate | Notes |
|---|---|---|---|
| WI | 0.30% | 0% | Paid by seller |
| IL | 0.10% | 0.05% | Chicago adds $7.50/$1K city tax |
| MN | 0.33% | 0% | "Deed tax" |
| IA | 0.16% | 0% | $1.60 per $1,000 |
| CA | 0.11% | 0.11% | County is Documentary Transfer Tax; many cities add more |
| FL | 0.70% | 0% | Documentary stamp tax; Miami-Dade adds 0.45% |
| TX | 0% | 0% | No transfer tax |
| NY | 0.40% | 0% | Additional NYC and mansion taxes apply for high-value sales |
| CO | 0.01% | 0% | Very low state rate |
| AZ | 0% | 0% | No state transfer tax |

All rates are editable — always verify with your title company.

---

## Capital Gains Assumptions

- Long-term gain rate options: 0%, 15%, 20% (federal). Enter your bracket rate.
- Add 3.8% NIIT if your income exceeds $200K (single) / $250K (MFJ) — enter 18.8% or 23.8% total.
- **Primary residence exclusion**: $250K single, $500K MFJ, if you've lived there 2 of the last 5 years.
- **Partial exclusion**: Available for job relocation, health, or unforeseen circumstances — not calculated here. See IRS Publication 523.
- **Depreciation recapture**: If the home was ever rented, the depreciation you claimed is recaptured at 25%. Enter it in the Depreciation Claimed field.
- **1031 exchanges and installment sales** are not supported — consult a CPA.

---

## localStorage

Two keys are used:
- `npc-v2` — auto-saves your current working inputs on every change
- `npc-saves-v2` — stores up to 5 named scenario saves with timestamps

To clear all saved data: open browser DevTools → Application → Local Storage → delete both keys.

---

## Deployment

### Vercel (recommended)
```bash
# From repo root
git add index.html README.md
git commit -m "Add v2 calculator"
git push origin main
# Vercel auto-deploys from main
```

### Netlify
Drag and drop the folder containing `index.html` onto [app.netlify.com/drop](https://app.netlify.com/drop).

### GitHub Pages
1. Go to repo Settings → Pages
2. Set Source to "Deploy from a branch" → `main` → `/ (root)`
3. Site available at `https://yourusername.github.io/RealEstate-app/`

---

## Disclaimers

This tool is for **estimation purposes only** and does not constitute financial, legal, or tax advice. Actual proceeds depend on:
- Official lender payoff statement (interest accrues daily)
- Title company's exact fee schedule
- County recorder's recording fees at time of closing
- IRS and state tax rules specific to your situation

Always review your HUD-1 / ALTA Settlement Statement with your title company and consult a CPA for tax questions.
