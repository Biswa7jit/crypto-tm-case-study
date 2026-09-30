# Investigation Report — Case TM-ALERT-88213

**Customer:** Alex Mercer (CX-2025-0847)
**Alert Type:** Deposit Velocity + Adverse Wallet Screening (Combined Rule)
**Alert Priority:** High
**Analyst:** Jordan Ellis
**Investigation Period:** November 14–15, 2025
**Status:** Recommended for SAR filing — see Disposition

> **Data disclosure:** The customer, all wallet addresses, and "Chain
> Analytics Co" (the blockchain screening vendor referenced) are
> entirely fictional, created for this portfolio demonstration.

---

## 1. Alert Summary

On 2025-11-14, a combined transaction-monitoring rule triggered on
customer CX-2025-0847:

1. **Deposit velocity:** November fiat deposit volume exceeded 300%
   of the customer's trailing 3-month average.
2. **Adverse wallet screening:** two of the customer's November
   crypto withdrawals were sent to external wallets that returned a
   Chain Analytics Co risk score of 70 or higher (High/Severe) on
   screening.

## 2. Customer Profile (as declared at onboarding, 2025-08-01)

| Field | Value |
|---|---|
| Occupation | Freelance Graphic Designer |
| Stated source of funds | Freelance/consulting income |
| Stated purpose of account | Personal investment in cryptocurrency |
| Stated expected monthly volume | $4,000 – $6,000 |
| Initial risk rating | Medium |

## 3. Profile vs. Actual Activity

| Period | Deposit Volume |
|---|---|
| August 2025 | $4,500 |
| September 2025 | $5,000 |
| October 2025 | $6,300 |
| **3-month average (Aug–Oct)** | **$5,267** |
| **November 2025 (alert month)** | **$85,000** |
| **Variance** | **+1,514%** |

The customer's activity for the first three months on the platform
was broadly consistent with their stated $4,000–$6,000/month profile
— on its own, October's $6,300 would not have warranted attention.
November's $85,000 is a different order of magnitude entirely, and
nothing on file explains it: no updated source-of-funds documentation,
no customer-initiated profile update, and no response to any
prior inquiry (none had been sent, as the account had not previously
warranted one).

## 4. Payment Channel Analysis

Every deposit from August through October arrived via **ACH bank
transfer** (6 of 6 deposits). Every deposit in November arrived via
**wire transfer** (7 of 7 deposits) — a complete channel switch
coinciding exactly with the volume spike. Wire transfers typically
carry higher per-transaction limits and, depending on the receiving
bank's controls, can involve less consistent beneficiary verification
than ACH transfers tied to a pre-linked account. A customer's
first-ever use of a materially different, higher-limit payment
channel in the same month their volume increases by over 1,000% is,
on its own, a meaningful behavioral change worth documenting —
independent of what it eventually turns out to mean.

## 5. Structuring Analysis

Four of the seven November deposits fell between $9,000 and
$9,999.99 — a tight cluster just under the $10,000 threshold
commonly associated with currency transaction reporting requirements
in traditional banking. While this exchange's own reporting
obligations differ from a bank's CTR regime, a pattern of multiple
deposits clustered just under a round, well-known reporting
threshold is a red flag in its own right, regardless of which
specific regulatory threshold (if any) technically applies to this
platform.

## 6. Wallet Analysis

Three crypto withdrawals occurred during the alert period:

| Transaction | Amount | Destination | Chain Analytics Co Result |
|---|---|---|---|
| TX-023 | $38,000 (BTC) | Previously unseen external wallet | **Severe (97/100)** — Direct: Darknet Marketplace |
| TX-024 | $33,500 (ETH) | Previously unseen external wallet | **High (74/100)** — Indirect: Mixing Service (2 hops) |
| TX-025 | $2,000 (BTC) | Customer's declared personal wallet | Low (5/100) — no adverse exposure |

The pattern here is worth naming directly: the customer withdrew the
overwhelming majority of the suspicious funds (94%) to two
newly-seen external wallets with adverse screening results, while
also sending a small amount (2,000 of 73,500, roughly 2.7%) to their
own previously-verified wallet. Continuing to use the known-clean
wallet alongside the high-risk ones does not offset the finding — if
anything, it is consistent with an attempt to maintain a pattern of
apparently normal activity on the account.

**TX-023's direct darknet marketplace exposure is the most severe
single finding in this case** and would independently warrant
escalation even without the other four red flags.

## 7. Case Risk Score

| Factor | Points |
|---|---|
| Volume deviation > 300% of average | 40 |
| Worst wallet risk category (Severe) | 40 |
| Structuring pattern (4 deposits under $10,000) | 15 |
| New, higher-limit payment channel introduced with spike | 10 |
| **Total** | **105** |

## 8. Risk-Based Disposition

**HIGH RISK — File SAR; restrict withdrawals pending review; escalate
for law enforcement referral consideration.**

This disposition is driven primarily by the direct darknet
marketplace exposure on TX-023, which on its own would meet the
threshold for escalation. The combination of a 15x unexplained
volume spike, a same-month payment channel change, a structuring
pattern, and adverse wallet screening across two separate
destinations makes this a high-confidence finding rather than a
borderline call requiring extensive additional judgment.

### Recommended next steps

1. **File a SAR** documenting the full fund-flow pattern, the wallet
   screening results, and the profile deviation analysis in this
   report.
2. **Restrict further withdrawals** from the account pending
   completion of the review, consistent with the platform's
   high-risk account procedures.
3. **Send an RFI** to the customer requesting an explanation for the
   source of the November deposits and the business purpose of the
   two flagged withdrawals — not because a response is expected to
   change the disposition given the darknet marketplace exposure,
   but because the response itself (or absence of one) is relevant
   evidence for the SAR narrative and any subsequent law enforcement
   referral.
4. **Do not tip off the customer** — the RFI in step 3 should be
   framed as standard account review language, not a disclosure that
   a SAR is being considered, per standard SAR confidentiality
   requirements.
5. **Refer to law enforcement liaison** for consideration of a
   voluntary referral, given the direct sanctioned-typology (darknet
   marketplace) exposure identified.

---

*This report and its underlying data (Customer_Profile,
Platform_Activity, TM_Alert, Wallet_Risk_Screening,
Investigation_Workpaper) are provided in `Crypto_TM_Case_Study.xlsx`
in this repository, along with standalone CSV exports in `data/`.*
