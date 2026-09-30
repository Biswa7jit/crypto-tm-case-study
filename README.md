# Crypto Transaction Monitoring Case Study

A complete, single-case walkthrough of a crypto exchange
transaction-monitoring program — from customer onboarding through
alert investigation to a risk-based disposition. Built entirely in
Excel formulas. No Python, no SQL, no VBA.

This is the seventh project in an AML/KYC portfolio series, and the
one that ties the full lifecycle together: a simulated customer, the
alert that triggered on their activity, the investigation comparing
their stated profile against what they actually did, wallet-level
analysis of where their funds went, and the risk-based disposition
that follows from all of it.

## ⚠️ About the data

The customer, every wallet address, and "Chain Analytics Co" (the
blockchain screening vendor referenced throughout) are entirely
fictional, created for this portfolio demonstration. No real person,
wallet, or blockchain analytics company is referenced.

## What's in this repo

```
Crypto_TM_Case_Study.xlsx           ← the main workbook (open this)
Investigation_Report.md             ← the formal case memo (read this)
README.md
data/
  customer_profile.csv              ← KYC data, standalone CSV
  platform_activity.csv             ← the customer's actual transactions, standalone CSV
  wallet_risk_screening.csv         ← blockchain analytics results, standalone CSV
  tm_alert.csv                      ← the alert details, standalone CSV
  investigation_workpaper_output.csv ← computed analysis, exported as CSV
screenshots/
  wallet_risk_screening.png
  investigation_workpaper.png
```

**Start with `Investigation_Report.md`** — it's written as the actual
case disposition memo. The workbook is the supporting analytical
evidence behind it.

## The case, in six stages

| # | Stage | Where it lives |
|---|---|---|
| 1 | Simulated crypto customer | `Customer_Profile` — Alex Mercer, onboarded with a stated $4,000–$6,000/month profile |
| 2 | Transaction-monitoring alert | `TM_Alert` — triggered on deposit velocity + adverse wallet screening |
| 3 | Customer profile vs. actual activity | `Investigation_Workpaper` §1 — a 15x unexplained volume spike |
| 4 | Alert investigation | `Investigation_Workpaper` §1–3 — payment channel shift + structuring pattern |
| 5 | Wallet analysis | `Investigation_Workpaper` §4 — two withdrawal destinations with adverse blockchain screening |
| 6 | Risk-based disposition | `Investigation_Workpaper` §5 — a computed case risk score and final recommendation |

## The case, briefly

Alex Mercer onboarded to a crypto exchange as a freelance graphic
designer expecting $4,000–$6,000 in monthly activity. For three
months, that held up. In November, seven wire-transfer deposits
totaling $85,000 arrived — a 1,514% increase over the account's own
trailing average, on a payment channel the customer had never used
before, with four of the seven deposits clustered just under
$10,000. The funds were converted to crypto and withdrawn to two
previously-unseen wallets. One screened as **directly exposed to a
darknet marketplace**; the other, to a mixing service.

## Workbook structure

| Tab | Purpose |
|---|---|
| `README` | Methodology (same content as this file) |
| `Customer_Profile` | What the customer told the exchange at onboarding |
| `Platform_Activity` | What the customer actually did, transaction by transaction |
| `TM_Alert` | The alert that triggered on this activity |
| `Wallet_Risk_Screening` | Third-party blockchain analytics results for every external wallet involved |
| `Investigation_Workpaper` | The analytical engine — every number is a live formula, ending in a computed risk score and disposition |

## Key formulas used

All standard Excel — no add-ins, no VBA:

- **`SUMIFS` with `DATE()` criteria** — computing monthly deposit
  totals from a flat transaction list. Date-range criteria are built
  with `">="&DATE(2025,11,1)` rather than a quoted date string, which
  is the more reliable pattern across Excel and other spreadsheet
  engines.
- **`COUNTIFS`** — detecting the structuring pattern (deposits
  clustered just under $10,000) and counting payment-method usage by
  period to catch the channel shift.
- **`INDEX`/`MATCH`** — resolving each withdrawal's destination wallet
  into its Chain Analytics Co risk category and exposure type.
- **Nested `IF`** — converting the volume-deviation percentage, worst
  wallet risk category, and the structuring/channel-shift flags into
  a single weighted case risk score and a plain-English disposition.
- **Conditional formatting** — flagging Severe/High risk wallet rows
  directly in the data.

## Results

![Wallet risk screening](screenshots/wallet_risk_screening.png)

![Investigation workpaper](screenshots/investigation_workpaper.png)

The full investigation workpaper computes a case risk score of
**105** (against a 70-point threshold for the highest disposition
tier) and returns:

> **HIGH RISK — File SAR; restrict withdrawals pending review;
> escalate for law enforcement referral consideration.**

## Why this project is structured as one case, not many

The other projects in this portfolio use multiple cases to show
range (the QA review scores 10 different files; the risk rating model
scores 25 different customers). This one is deliberately a *single*
case, worked end to end, because the six components the case study
asks for — customer, alert, investigation, profile comparison, wallet
analysis, disposition — aren't independent data points to aggregate.
They're sequential stages of one investigation, each one setting up
the next, and the point of this project is to show that chain of
reasoning intact rather than a table of isolated findings.

## Limitations (stated honestly)

- Synthetic data only — a single clean case, sized for a readable
  demonstration. A real exchange's alert queue runs thousands of
  cases against constantly-updated wallet screening data.
- The case risk scoring weights (40/40/15/10, 70-point threshold) are
  illustrative for this case, not a validated production model.
- Wallet risk screening is treated as a single point-in-time result
  from one vendor; real programs often cross-reference multiple
  screening providers and re-screen periodically, since wallet risk
  scores change as new on-chain activity is observed.
- No cross-reference to the wallet-level fund-flow tracing technique
  from this portfolio's separate on-chain investigation project — a
  real follow-up to this case would trace TX-023 and TX-024 further
  downstream using that same methodology.

## About

Built by [Your Name], CAMS-certified compliance analyst exploring
crypto-asset AML/compliance, as a portfolio piece. See also: [link to
SQL AML project], [link to Excel AML transaction monitoring project],
[link to Sanctions & PEP screening project], [link to Customer Risk
Rating Model project], [link to AML QA Review project], [link to
On-Chain Transaction Investigation project], and [link to Medium
AML/crypto compliance article series].
