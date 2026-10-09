# E-N01 redesigns: stronger research questions

Date: 9 October 2026. Two redesigns survive. A third candidate and three variants of the original are listed at the end as **considered and not proposed**.

Readiness labels:
- **READY-CONDITIONAL:** data verified at documentation level; one cheap pilot decides.
- **SPECULATIVE:** data access or contribution not yet shown.

Nothing here is READY in the strict sense. No variable values have been inspected and no estimates exist.

Shared data foundation (register D01–D05):

| Source | Unit | Years | Key fields | Verification |
| - | - | - | - | - |
| SEC **N-CEN** data sets (FUND_REPORTED_INFO, ADVISER) | Series × fiscal year | FY2018–FY2026 filings (data sets Sept 2018–Sept 2026) | `HAS_EXP_LIMIT` (C.8.a), `HAS_EXP_REDUCED_WAIVED` (C.8.b), `HAS_EXP_SUBJ_RECOUP` (C.8.c), `HAS_EXP_RECOUPED` (C.8.d), `MONTHLY_AVG_NET_ASSETS`, `DAILY_AVG_NET_ASSETS`, `IS_MONEY_MARKET`, `IS_INDEX`, `IS_ETF`, adviser names | Form and readme read; **values not inspected** |
| SEC **prospectus risk/return** XBRL data sets | Class × prospectus date | 2011–2025Q3 | Gross expenses, fee waiver/reimbursement (some filers label it "…or (Recovery)"), net expenses, footnote text | Catalog and secondary only; used for waivers by Black & Kölbel (2024) |
| SEC **N-PORT** data sets | Series × month (class for returns) | Oct 2019– | `NET_ASSETS`, monthly sales/reinvestment/redemption flows, class monthly total returns | Readme fields read |
| **N-CSR/N-CSRS** notes | Fund × fiscal period | Any | Recoupment amount, waived amount, remaining balances, expiry/forgiveness (format-dependent) | Demonstrated for 6 funds by the earlier project (not re-verified by me) |

---

## E-R1 (primary). Contingent fee subsidies: prevalence, exercise and scale pass-through of recoupable expense waivers

**Status: READY-CONDITIONAL**. The N-CEN prevalence pilot decides it.

### 1. Research question and economic mechanism

> When fund advisers subsidize expenses through expense caps, how often do they keep a contractual right to recover the subsidy from later shareholders? How often, and how much, do they actually recover? Do recoverable subsidies delay the decline in investors' net fees as funds grow?

**Mechanism.**
- A small fund's fixed costs make its gross expense ratio uncompetitive, so the adviser caps net expenses.
- **Non-recoupable** waiver: a sunk marketing subsidy paid by the adviser.
- **Recoupable** waiver: a *contingent loan* from the adviser to the fund, repaid out of future cap headroom, usually within three years. The repayment falls on whoever holds shares when the fund grows.
- The headline net expense ratio in fee tables and ratings looks the same under both contracts. The future cost differs.

**Predictions.**
- **P1 (pass-through).** Take capped funds whose gross ratio falls below the cap. Net fees of non-recoupable funds fall roughly one-for-one with gross. Net fees of recoupable funds with recent waivers stay near the cap until rights are recovered or lapse. The pass-through slope Δnet/Δgross should be near 1 versus near 0 in the first post-crossing years.
- **P2 (contract choice).** Recoupable terms concentrate where the adviser's subsidy is costlier and the option to recover more valuable: small or independent advisers, multi-adviser series trusts, young and fast-growing funds.
- **P3 (exercise).** Exercise is incomplete. Rights lapse or are forgiven even when headroom exists, as in Towpath FY2024 and Schwab/Vanguard money funds in 2015.
- **P4 (incidence).** Recoupment raises the fees paid by post-growth shareholders by a measurable number of bps over a bounded window.

### 2. Why Finance researchers should care

- It speaks to three live debates:
  - who captures scale economies in delegated asset management (Deli 2002; Wahal & Wang 2011; Section 36(b) litigation);
  - shrouded or deferred pricing in retail finance (Barber, Odean & Zheng 2005; Gabaix & Laibson 2006);
  - how new funds are financed and launched (Evans 2010).
- Christoffersen (2001) explicitly leaves the "recapture higher fees later" motive for future research.
- Recoupment is a **contractual intertemporal transfer between investor cohorts**: earlier shareholders get the subsidy, later shareholders repay it. That is a cleaner object than generic "fees are sticky" evidence.

### 3. Closest competitors

1. **Christoffersen (2001, JF)**: waivers as flexible pricing in money funds, 1990–95. No contractual recoupment data.
2. **Black & Kölbel (Dec 2024 WP), "The Puzzle of ESG Fund Fees"**: waivers drive the ESG net-fee gap. Funds that *discontinue* waivers show no subsequent fee increases. Uses prospectus waiver data; no recoupment rights.
3. **Di Maggio & Kacperczyk (2017, JFE)**: money-fund waivers as sponsor subsidies at the ZLB. No recoupment exercise.

Scale-pass-through background: Deli (2002).

### 4. Exact remaining novelty

- First universe-level measurement (2018–2025) of **which subsidies are recoverable and when recovery is exercised**.
- First test of whether recoupment rights **delay scale-economy pass-through** to shareholders.
- A dollar/bps incidence estimate anchored on a validated, stratified subsample.

No paper using N-CEN Item C.8 was found. Black & Kölbel's "discontinued waiver → no fee increase" test does not capture recovery, because recovery raises *net* expenses through a recovery line while the waiver line merely disappears.

### 5. Variables and verified availability

| Variable | Source | Availability |
| - | - | - |
| ELA exists; waived in year; waived fees recoupable; recouped in year | N-CEN C.8.a–d | **Field names verified**; values unknown |
| Average net assets | N-CEN C.19 | Field verified |
| Adviser identity | N-CEN ADVISER table | Table documented |
| Gross, waiver, net expense ratio by class | Prospectus RR XBRL | Existence documented; element names from SEC XBRL renderings; **sign convention for recoveries unverified** |
| Cap level and recoupment terms | RR footnote text; ELA exhibits (485BPOS) | Text exists; parsing effort unknown |
| Monthly net assets, flows, returns | N-PORT | Field names verified |
| Recoupment $ and remaining balance | N-CSR notes (hand) | Feasible per earlier pilot; ~1–3 hours per fund-year (unmeasured) |

### 6. Unit of observation and estimands

- Units: series × fiscal year (N-CEN), linked to class × prospectus year (RR) and series × month (N-PORT).
- **E1 (prevalence and exercise):**
  - share of funds and AUM with C.8.c = Y among funds that waived;
  - annual exercise rate P(C.8.d = Y | recoupable waivers in t−1..t−3);
  - by year, adviser type, size, age, asset class.
- **E2 (pass-through):** difference in Δnet/Δgross between recoupable and non-recoupable capped funds in an event window around the first year in which waivers stop being needed (C.8.b switches Y→N, or gross falls below net).
- **E3 (incidence):** recouped dollars over average net assets (bps), from a stratified random N-CSR subsample, reweighted to the N-CEN population. Also the cumulative excess net fee relative to the non-recoupable counterfactual over the recovery window. This is an **accounting counterfactual, not an equilibrium one**.

### 7. Identification assumptions and main confounders

- **E1 is descriptive.** Its validity rests on measurement. N-CEN C.8 is self-reported and has documented misreporting (SEC staff letters, register D05). Validate against N-CSR on a random sample and report error rates.
- **E2 is associational.** Contract type is chosen by the adviser. Confounders:
  - adviser fee policy;
  - cap changes and ELA terminations (the cap itself can be lowered or raised);
  - share-class mix changes;
  - prospectus/fiscal-year timing mismatches;
  - fund mergers and liquidations (survivorship).
- Mitigations:
  - compare within adviser or trust where both contract types exist;
  - event-time profiles aligned on the headroom crossing;
  - placebo crossings for funds without waivers;
  - leave-one-adviser-out;
  - cluster by adviser.
- The core contrast is mechanical *if* rights are exercised. The empirical content is **how often and how strongly** the mechanical effect materializes. No causal claim about contract choice.

### 8. Type of contribution

Descriptive (E1, E3) plus associational (E2). Not causal.

### 9. Required new data collection

- N-CEN quarterly ZIPs: small, structured.
- RR quarterly ZIPs: moderate size; XBRL facts and contexts must be parsed.
- N-PORT fund-level tables only.
- 40–80 N-CSR fund-years, stratified by recoupment status and schedule format, hand-coded with the existing ledger protocol. A second coder for 20.

### 10. Feasibility by April–May 2027

**Feasible if the pilot passes.** Indicative plan:
- Oct–Nov 2026: N-CEN + RR panel.
- Dec 2026–Jan 2027: N-CSR validation and amounts.
- Feb–Mar 2027: E1–E3.
- Apr–May 2027: draft.

Main risk: RR XBRL parsing (class contexts, restatements). Fallback: E1 and E3 without RR, using N-CEN plus N-CSR only.

### 11. Main referee objection

> "This is a mechanical accounting feature affecting small funds and small dollars."

The answer must show:
- (i) material prevalence: thousands of fund-years and a non-trivial share of funds with ELAs;
- (ii) economically meaningful bps for affected cohorts, comparable to fee gaps the literature treats as important (e.g., the 9.5–12.7 bp ESG gap);
- (iii) non-mechanical content in *exercise* (P3) and *contract choice* (P2).

Second objection: "N-CEN flags are noisy." Answer: measured error rates and bounds.

### 12. Is a null informative?

- **Partly.** If recoupment rights are common but rarely exercised even when feasible, the paper shows that recoupment clauses are mostly unexercised options. Disclosed net fees are then not systematically misleading. That is useful for regulators and for interpreting waiver data (e.g., Black & Kölbel).
- If recoupable waivers are **rare**, the null is uninteresting and the project should stop.

### 13. Realistic research-paper potential

- **Good master's thesis** with a distinctive, verifiable dataset: high probability if the pilot passes.
- **Working paper:** credible.
- **Field journal** (asset-management or banking/finance field journals): possible only with material prevalence and a convincing E2. That is a plausible target family, not a forecast.

### 14. Cheapest decisive pilot (4–8 hours, needs approval)

1. Download all N-CEN quarterly ZIPs (about 30 files, roughly 0.6–5.6 MB each). The SEC requires a declared contact User-Agent, which you must supply.
2. Parse FUND_REPORTED_INFO and ADVISER. Deduplicate amendments.
3. Tabulate C.8.a–d by fiscal year, unweighted and weighted by average net assets, excluding money-market funds and ETFs in a second cut.
4. Count distinct advisers with C.8.d = Y.
5. Open N-CSR notes for 10 random C.8.d = Y and 10 random C.8.c = Y/C.8.d = N fund-years. Record agreement and recoupment amounts.

**Screening thresholds** (set before seeing the data; justified by the minimum needed for E2 event-time estimates with adviser clustering):

| Outcome | Rule |
| - | - |
| Continue | ≥150 series-years with C.8.d = Y over FY2018–2025, from ≥40 distinct advisers, none of which accounts for >25%; **and** ≥500 series per year with C.8.c = Y; **and** ≤4 of 20 validation cases contradicted by N-CSR |
| Stop E-N01 entirely | <75 recouped series-years, **or** >50% concentrated in ≤5 advisers, **or** ≥8 of 20 validation cases contradicted |
| Re-adjudicate | Anything in between: likely a descriptive-only thesis |

### Publication value

| Question | Answer |
| - | - |
| New knowledge | How often advisers convert fee subsidies into recoverable claims on future shareholders, how often they collect, and how much this slows the decline of fees as funds grow |
| Who cares | Asset-management and fee-competition researchers; SEC and ESMA disclosure policy; Section 36(b) scale-economy arguments; data users who treat net expense ratios as the price |
| Why not answered yet | The literature studies waivers as cuts (Christoffersen; Black & Kölbel), not as loans. The universe-level recoupment flag exists only since N-CEN (2018) and appears unused |
| Distinguishing test | A recoupable fund's net fee stays flat while gross falls, and a recovery line appears (N-CSR) or C.8.d = Y; the non-recoupable comparator's net fee falls. Competing explanations (cap changes, class mix) predict cap revisions or composition changes, which are observable |
| Why a referee would not reject immediately | Universe data, a clear contractual mechanism, a validated measurement protocol, an explicit open question in a classic JF paper |
| What could make it disappear | Low prevalence or exercise; N-CEN misreporting so severe that flags are unusable; a recent unpublished paper on N-CEN C.8 (SSRN could not be searched directly) |

---

## E-R2 (extension). Is discretionary recoupment a back-door asymmetric performance fee?

**Status: SPECULATIVE.** It depends on the size of the "feasible but discretionary" set.

### 1. Research question and mechanism

> When recovery is contractually feasible, do advisers recoup more after strong performance and inflows, and forgo it after weak performance?

If so, recoupment creates an **upside-only, performance-contingent fee**. Mechanism:
- Investors' attention to fees is lower after good performance (Christoffersen 2001; Christoffersen & Musto 2002).
- Recouping after losses is reputationally costly.
- The Advisers Act allows registered-fund performance fees only in symmetric "fulcrum" form (§205(b)(2); secondary source, verify). Discretionary recoupment could reproduce an asymmetric incentive outside the explicit fee contract.

### 2. Why Finance researchers should care

- It links the regulation of incentive fees (Elton, Gruber & Blake 2003) to an unregulated discretionary margin.
- It extends Christoffersen's "waivers as flexible fees" from cuts to recoveries.

### 3. Closest competitors

Christoffersen (2001); Elton, Gruber & Blake (2003); Christoffersen & Musto (2002).

### 4. Remaining novelty

No test of discretionary *exercise* of recoupment rights was found.

### 5. Variables and availability

- **Feasible set** constructed from N-CEN alone: C.8.c = Y with C.8.b = Y in some year t−1..t−3 (recent recoupable waivers, so an unexpired balance is likely), and C.8.b = N in year t (no waiver needed, so gross is below the cap and headroom exists).
- Outcome: C.8.d.
- Regressors: prior-year returns (N-PORT class returns), flows (N-PORT), asset growth (N-CEN, N-PORT), adviser size.
- Availability: documented fields; **feasible-set size unknown**.

### 6. Unit and estimand

Series × fiscal year within the feasible set. Estimand: the difference in P(recoup) between top- and bottom-tercile prior performance, conditional on asset growth (a headroom proxy) and year effects.

### 7. Identification and confounders

- **Performance → flows → headroom is the central confounder.** Better performance mechanically creates more room to recoup. Condition on growth and size, and use cases where headroom exists in both performance groups.
- The feasible-set proxy misclassifies funds whose balance was already recovered or forgiven, and funds whose ELA ended.
- Validate on the N-CSR subsample.
- Adviser-level policies: adviser fixed effects where possible.

### 8. Type

Associational.

### 9. New data

None beyond E-R1. Additional N-CSR checks of 20 feasible-but-not-exercised cases to separate forgiveness from "no balance".

### 10. Feasibility by April–May 2027

Only as a chapter of E-R1.

### 11. Main referee objection

> "Recoupment simply follows headroom, and headroom follows performance."

This is answerable only if there is variation in exercise **holding headroom fixed**. Phase 3's small sample suggests exercise tracks headroom closely, which is a warning sign.

### 12. Is a null informative?

Yes. "Exercise is near-automatic whenever feasible" would show recoupment is a deterministic deferred fee, not a discretionary instrument. That strengthens E-R1's incidence interpretation.

### 13. Paper potential

It raises E-R1's ceiling if discretion exists. It is not a standalone thesis.

### 14. Cheapest decisive pilot

Part of the E-R1 N-CEN tabulation: count feasible series-years and the exercise rate.

**Continue only if** there are ≥300 feasible series-years with an exercise rate between 20% and 80%. Outside that band there is little discretion to explain.

### Publication value

| Question | Answer |
| - | - |
| New knowledge | Whether advisers use contractual recovery rights strategically, as a hidden incentive fee |
| Who cares | Fee-regulation scholars, SEC, fund-governance researchers |
| Why not answered | No exercise data before N-CEN |
| Distinguishing test | Performance predicts exercise within the feasible set, conditional on growth; forgiveness concentrates after poor returns |
| Why not rejected immediately | A direct link to a statutory restriction and a classic open question |
| What could make it disappear | Exercise is mechanically determined by headroom; feasible set too small |

---

## Considered and not proposed

| Candidate | Why not |
| - | - |
| **Original E-N01: recovery timing near expiry** | Not identifiable. Every vintage's age equals its time-to-expiry under common 3-year windows; recovery is governed by headroom, which moves with growth; vintage allocation is undisclosed under original-amount schedules (Phase 3). Any causal deadline claim would need contractual variation in windows that is not available in the observed data. **Stop.** |
| **Narrowed E-N01: six-fund ledger reconciliation and incidence** | Feasible but not important on its own: two positive-recovery funds, no population meaning, no reconciled-with-full-disclosure interval. **Keep only as the validation protocol inside E-R1.** |
| **Vintage-level reconstruction at scale** | Requires remaining-balance formats and disclosed expiry/forgiveness, which are often missing. That is the "impossible reconstruction" the brief tells me to reject. **Reject.** |
| **E-R3: Do investors and ratings price recoupable waivers?** (flows vs net fee by recoupment status) | Interesting (shrouding), but identification is weak: contract type is chosen by advisers with different distribution models. A possible competitor (Mugerman & Steinberg, SSRN 4603217) could not be read. **Not proposed**; possible descriptive appendix to E-R1. |
| **Money-market fund recapture after 2022** | Large sponsors renounced recapture in 2015 (Schwab, Vanguard). Recent money-fund waivers were largely described as voluntary yield support. Rate pass-through was about 97% of the EFFR rise by 2023, so any unwind effect is front-loaded and small. **Reject** (see `adjacent_alternatives.md`). |
