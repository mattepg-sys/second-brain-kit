# Recipe: Monthly spending summary

> Every month, bank transactions become a one-page summary: where the money went, recurring subscriptions, anything unusual, and how this month compares with the last.

**Suggested path:** standard (financial data is sensitive; the owner decides which services see it).
This recipe only **reads** financial data. We strongly advise not connecting anything that can make payments; if the owner wants that, explain the risks first and get an explicit yes.

---

## 1. Pre-filled flow card (adapt it)

| Label | Default |
|---|---|
| **What** | Transactions → a monthly summary by category, subscriptions, unusual items |
| **When** | Monthly (e.g., the 2nd of each month), or on demand |
| **Who** | The owner's AI assistant |
| **Checkpoint** | The owner reads the summary and corrects categories; corrections are remembered |

- **From:** bank exports (CSV, Excel, PDF statements) in `Finance/bank-exports/` (registered as a `folder` with status `active, protected`: the AI only reads it)
- **To:** `Finance/monthly/YYYY-MM.md`; subscriptions list `Finance/subscriptions.md`
- **Done means:** on the first days of each month there is a one-page summary the owner trusts, built without manual spreadsheets.

## 2. Choose your version

Recommend starting with A. It works with every bank, in every country, for free.

| Version | How the data arrives | Good for | Cost direction |
|---|---|---|---|
| **A. Monthly export** | Once a month the owner downloads the CSV/Excel (or PDF) export from each bank's website or app and drops it in `Finance/bank-exports/` | Everyone | Free |
| **B. Budgeting app + export** | A budgeting app (e.g., Actual Budget, open source; or a commercial one) collects transactions; the owner exports monthly, or the AI reads the app's export | People who already use a budgeting app | Free to a few euros/month |
| **C. Open banking (automatic)** | An open-banking service connects to the bank with the owner's consent and feeds a budgeting app or a small script; the summary is generated on schedule | Technical users | See below |

**Open banking as of October 2026 (verify before relying on it):**
- **EU and UK:** Enable Banking offers a free "restricted" mode for linking your own accounts (needs registering an app and keeping a private key: technical). GoCardless Bank Account Data (formerly Nordigen), recommended by many older tutorials, stopped accepting new accounts in July 2025.
- **United States:** SimpleFIN Bridge (about $15/year) works with budgeting apps such as Actual Budget.
- **Consent expires** (typically every 90–180 days under EU rules): expect to re-authorize periodically.
- Coverage varies by bank: check the owner's specific banks.

**Italy, bonus source (checked October 2026; verify):** private citizens can download their electronic invoices (B2C, as XML) from the Agenzia delle Entrate portal ("Fatture e corrispettivi", logging in with SPID/CIE/CNS, role "consumatore finale"). Files are kept only for about two years, so a regular download is worth it.

## 3. Privacy (advice; the owner decides)

Explain once, plainly:
- The summary requires an AI to read the transactions. That AI's provider will process them.
- Options to reduce exposure: remove account numbers and IBANs from exports before the AI reads them; use only the totals; keep finance in a separate area; or use a local tool for this flow.
- Keep bank passwords, tokens and keys out of the brain's files.

Record the owner's choice in `AGENTS.md` section 5.

## 4. Setup (version A)

1. Create `Finance/`, `Finance/bank-exports/` (register it as a `folder` with status `active, protected`: the AI only reads it) and `Finance/monthly/`. Register them.
2. Ask: which banks and cards, and roughly which categories matter (default: housing, groceries, transport, eating out, kids, health, subscriptions, travel, work, other).
3. The owner downloads last month's exports and drops them in `Finance/bank-exports/` (file names like `2026-09-bankname.csv`).
4. Do it by hand: read the exports together, propose categories, let the owner correct them. Save the agreed rules in `memory.md` (e.g., "transfers to my savings account are not spending").
5. Write the runbook (draft below).
6. Choose how it runs: on demand ("make my spending summary") or monthly scheduled, if the AI assistant supports it. Add a monthly reminder for the owner to drop the exports.
7. Register the flow.

## 5. Runbook draft

```markdown
---
name: monthly-spending
description: Turns the month's bank exports into a one-page spending summary with categories, subscriptions and unusual items. Use monthly or when the owner says "make my spending summary".
---

# Monthly spending summary

## Context to read
1. _system/profile.md (household, currency)
2. Finance/bank-exports/ files for the month (read-only)
3. Finance/subscriptions.md and last month's summary
4. memory.md (category rules, known transfers, merchant names)

## Steps
1. Read all exports for the month; normalize dates, amounts, currency.
2. Remove duplicates (the same transaction in two exports) and internal transfers.
3. Categorize each transaction (memory.md rules first; otherwise best guess, marked "?").
4. Detect recurring payments; update Finance/subscriptions.md (name, amount, frequency, last seen).
5. Flag unusual items: new merchants above a threshold, amounts much higher than usual, possible double charges.
6. Compare totals with last month.

## Output: Finance/monthly/YYYY-MM.md
# Spending — Month YYYY
Total out · total in · difference vs last month
By category: category · amount · vs last month
Subscriptions: active list · new · possibly unused
Unusual: date · merchant · amount · why flagged
Uncertain categories (?): to confirm

## Rules
- Read-only: never modify files in bank-exports.
- Never contact banks, never initiate payments.
- Don't copy full account numbers into the summary.

## After the run
- Log one line. Owner's category corrections → memory.md "Proposed".
```

## 6. Tests
| Test | Expected |
|---|---|
| Two exports with the same card payment | Counted once |
| A transfer to own savings | Not counted as spending (after the rule is learned) |
| A new €400 merchant | Flagged as unusual |
| A monthly streaming payment | Appears in subscriptions |

## 7. Pitfalls and tips
- **Export formats differ** between banks (separators, date formats, decimal commas). The first run takes longest; save what you learn in memory.
- **Categories are personal.** Expect the owner to correct many in month one and few by month three.
- **Don't automate before trusting it:** run version A for 2–3 months before considering open banking.

## 8. Grow it next
- **Receipts and invoices** collected from email.
- **Bills and deadlines** in the calendar.
- A **yearly overview** for taxes.
