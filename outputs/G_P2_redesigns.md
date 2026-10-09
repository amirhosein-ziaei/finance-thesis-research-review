# G-P2 redesigns: stronger research questions

Date: 9 October 2026. Three questions are proposed, ranked: one primary redesign, one speculative extension, and one dependable narrowed fallback.

**Rule observed.** None of these is chosen because the old outcome gave a null. Each changes the outcome **on mechanism grounds** (`G_P2_literature_audit.md` §3, explanation 8). Each must be **prespecified before any estimation**, with all prespecified outcomes reported. Searching subgroups or outcomes for significance is excluded.

Shared data (register SD1–SD5). Checked by reading only headers and codebooks:
- **SCE core:** monthly; Q13new, Q22new, Q30new, employment, demographics, `_STATE`, `_COMMUTING_ZONE`.
- **SCE Credit Access (CA) module:** Feb, Jun and Oct waves from Oct 2013; same `userid` format. Contents:
  - debt holdings (N1) and balances (N2);
  - maxed-out card (N3);
  - applications and limit-increase requests in the past 12 months (N4);
  - discouragement (N5–N7) and approvals (N9–N11);
  - lender closures and limit cuts (N14);
  - **late payments >30 and >90 days in the past 12 months (N15, N16)**;
  - planned applications (N17), expected approval (N21), credit score (N22);
  - needing / being able to raise $2,000 next month (N24, N25).
- **SCE Household Finance module:** liquid savings and debt levels; lower frequency.
- **Not verified:** the actual `userid` match rate between public core and CA files, and the end date of public CA coverage.

---

## G-R1 (primary). Precautionary credit, rationing and delinquency under perceived labor-income risk

**Status: READY-CONDITIONAL.** Data documented and linkable in format; the merge pilot decides.

### 1. Research question and economic mechanism

> Do employed households that perceive higher job-loss risk build borrowing capacity before the shock, through new cards and limit-increase requests? Or are they rationed, through rejection, discouragement and lender limit cuts? Does the response depend on how quickly they expect to be re-employed? Do these beliefs predict later delinquency beyond credit score and stated payment expectations?

**Mechanism.**
- Revolving lines are long-term, non-contingent contracts. If obtained while employed, they can be drawn after job loss (Braxton, Herkenhoff & Phillips 2024).
- Access to *new* credit deteriorates after job loss (Druedahl & Jørgensen 2018), which gives a precautionary motive to acquire credit early.
- Credit is a bridge for **short** spells. For long spells it is costly and risky, so reemployment beliefs (Q22) have a well-defined role here: they moderate the value of precautionary credit. This contrasts with the original Q30 design, where the role of Q22 was scaled down by the small probability of job loss within the horizon.
- Lenders do not observe beliefs. If beliefs predict delinquency conditional on lender-relevant observables, workers hold **private information** in credit markets (in the spirit of Hendren 2017).

**Prespecified hypotheses.**
- **H1:** higher Q13 raises (planned and realized) credit-line acquisition among *unconstrained* households (good score, not maxed out).
- **H2:** higher Q13 raises discouragement and rejection among *constrained* households.
- **H3:** the H1 response is larger when Q22 is high (short expected spell).
- **H4:** Q13 (and Q22) predict **new delinquency onset** between CA waves, conditional on score bin, income, debt holdings and Q30.

### 2. Why Finance researchers should care

- Household liquidity insurance through credit is central to the credit-card-debt puzzle and consumption smoothing.
- It informs UI design when credit substitutes for insurance (Braxton, Herkenhoff & Phillips).
- It speaks to adverse selection in consumer credit.
- The "credit smoothing" puzzle (Hundtofte, Olafsson & Pagel 2019) asks why unemployed people do not borrow. Ex ante behaviour, whether people pre-arrange credit and whether they are rationed, is the missing half.

### 3. Closest competitors

1. **Fermand, Kuhnen, Li & Ben-David (2024, Management Science)**: SCE core + CA + Household Finance. Expectation *uncertainty* predicts more cautious behaviour, including seeking credit-line increases (N17a).
2. **Braxton, Herkenhoff & Phillips (2024, JPE)**: credit-bureau and employment data. Credit is extended before and after job loss; constrained job losers delever and default. No beliefs.
3. **Hundtofte, Olafsson & Pagel (2019, NBER WP)**: no credit smoothing during unemployment.

Also Hartmann & Leth-Petersen (2024): beliefs → savings and UI, Denmark.

### 4. Exact remaining novelty

- The **level** of perceived job-loss risk (not uncertainty) and its interaction with perceived reemployment speed.
- Mapped into **both sides of the credit market**: acquisition, and rationing/discouragement.
- Plus **realized** delinquency onset, in public U.S. data, with debt ownership observed.
- None of the three competitors does this combination. The novelty is a well-defined increment, not a new field.

### 5. Variables and verified availability

| Construct | Item | Status |
| - | - | - |
| Job-loss risk; reemployment belief; payment expectation | Q13new, Q22new, Q30new (core) | Verified in earlier project (raw) and in the header |
| Debt holdings and balances | N1_1–N1_7, N2/N2b | Codebook verified |
| Credit acquisition | N4_1 (new card), N4_4 (card limit increase), N4_5 (loan limit increase) in past 12m; N17a/b planned | Codebook verified. N17a/N17b randomly assigned Feb–Oct 2014 (different formats) |
| Rationing | N9 granted; N5_5, N6_*, N7_* discouraged; N14_2, N14_4 lender closure or limit cut; N21 expected approval | Codebook verified |
| Realized distress | N15 (late >30d, 12m), N16 (late >90d, 12m), N3 (maxed out) | Codebook verified; **question routing (asked of all vs debt holders) not yet checked** |
| Lender-relevant observables | N22 self-reported credit score; `_HH_INC_CAT`; age; education | Verified in headers |
| Liquidity buffer | N24, N25; Household Finance d16new (savings) | Verified in codebooks |
| Linkage | `userid` + `date` | Same format; **match rate unverified** |

### 6. Unit and estimand

- **Unit:** employed person × CA wave. Core beliefs come from the same month and the preceding core months.
- **Primary estimands** (pp per 10pp Q13):
  - (a) probability of a card-limit-increase request or new-card application in the past 12 months (N4_1 or N4_4);
  - (b) probability of discouragement or rejection;
  - (c) new delinquency onset between consecutive waves (N15 = 0 at wave w and = 1 at w+1). This identifies a late payment within the 4 months after w, because the two 12-month windows overlap except for that interval.
- Each estimand is conditional on score-bin × wave FE, income, age, education, debt holdings and Q30.
- **Prespecified heterogeneity:** constrained vs unconstrained (score bin and N3), and the Q13 × Q22 interaction. Nothing else.

### 7. Identification assumptions and main confounders

- **Associational.** Main confounders:
  - **Need-driven borrowing.** Distressed households both fear job loss and seek credit. Mitigations: control Q30, N3, N25; test the unconstrained subsample; look at limit-increase *requests* rather than balances.
  - **Reverse causality.** Rejection raises pessimism. Mitigation: beliefs measured in months before the application window where possible.
  - **Common pessimism.** Mitigation: control expected U.S. unemployment (Q4new) and the Fermand et al. uncertainty measure (constructible from core density items).
  - **Unobserved lender information.** Self-reported score is a coarse proxy, so a positive H4 shows predictive content, not proof of private information.
- Within-person estimates across at most three waves are a robustness check only.

### 8. Type

Associational and predictive. Not causal.

### 9. Required new data

Download two public modules (CA ~16 MB; Household Finance ~9 MB) and merge to the existing core panel. No new collection.

### 10. Feasibility by April–May 2027

**High.** The core pipeline exists. CA variables are mostly binary or categorical.

Planning power calculation (**illustrative, not an estimate**):
- Assume about 20,000 employed person-waves, SD(Q13/10) ≈ 1.9, and an outcome SD of about 0.46 (base rate about 30%).
- Then SE(β) ≈ 0.46/(1.9·√20,000) ≈ 0.17pp per 10pp, about 0.26pp with clustering.
- Minimum detectable effect ≈ 0.7pp per 10pp. For delinquency onset (base rate about 3%), the MDE is roughly 0.25pp per 10pp if about 10,000 wave pairs exist.
- These assumptions must be replaced by pilot counts.

### 11. Main referee objection

> "Fermand et al. already show belief uncertainty predicts credit-line seeking. Your job-loss belief is just a proxy for distress or uncertainty."

Answer:
- control their uncertainty measure and current distress;
- show the effect in the unconstrained group and its predicted moderation by Q22;
- show the rationing side (H2) and realized delinquency (H4), which they do not study.

Second objection: "Self-reported, 12-month retrospective outcomes." Answer: wave-to-wave onset design, plus external evidence that delinquency status is accurately self-reported (BIS WP 1258, secondary).

### 12. Is a null informative?

**Moderately.** If unconstrained households with high perceived job-loss risk do *not* acquire credit ahead of the shock, the credit-smoothing puzzle is at least partly a **demand-side** phenomenon: households do not pre-arrange credit insurance. That matters for models in which revolving lines insure job loss.

A null on H4 (beliefs carry no delinquency information beyond score and Q30) speaks against a private-information channel. A null on everything, with tight CIs, still yields a coherent thesis.

### 13. Realistic paper potential

- **Strong master's thesis:** high completion probability.
- **Credible working paper.**
- **Field-journal potential** (household finance, banking): conditional on clear H1/H2 patterns and a convincing distinction from Fermand et al.
- Top-journal potential: low.

### 14. Cheapest decisive pilot (3–5 hours, needs approval)

1. Download the CA file and merge to the existing core panel by `userid` and `date`.
2. Report:
   - match rate;
   - number of employed person-waves; persons with ≥2 waves;
   - CA coverage end date;
   - routing of N15 and N4 (who is asked);
   - base rates of N4_1/N4_4, discouragement and N15;
   - number of N15 0→1 onsets among the employed;
   - within-person SD of Q13 across waves.
3. **No regressions.**

**Continue** if:
- ≥10,000 employed person-waves are matched;
- ≥3,000 persons have ≥2 waves;
- ≥150 delinquency onsets among the employed;
- coverage extends at least to 2023.

**Stop G-R1** if the match rate is below 50%, or onsets are below 75 (H4 infeasible; H1–H2 might still justify a smaller thesis — re-adjudicate).

### Publication value

| Question | Answer |
| - | - |
| New knowledge | Whether perceived labor-income risk changes U.S. households' credit access ex ante (acquisition vs rationing), and whether those beliefs carry information about later delinquency |
| Who cares | Household-finance and macro-finance researchers (credit as insurance, UI design), consumer-credit regulators, credit-risk modelers |
| Why not answered yet | Credit-market papers on job loss use realized shocks without beliefs (Braxton et al.; Keys); belief papers study search, savings or uncertainty (Mitra; Hartmann & Leth-Petersen; Fermand et al.) |
| Distinguishing test | Precaution predicts acquisition among the unconstrained and moderation by expected spell length. Need-driven borrowing predicts effects concentrated among the distressed and no Q22 moderation. Pessimism predicts that macro beliefs absorb the effect |
| Why not rejected immediately | Public, linkable data with debt ownership and delinquency; mechanism derived from recent JPE/MS work; prespecified tests |
| What could make it disappear | A low match rate; few onsets; a paper using exactly CA × Q13 (none found; SSRN could not be searched directly); effects fully absorbed by distress controls |

---

## G-R2 (extension). Do ex ante beliefs shape the financial consequences of realized job loss?

**Status: SPECULATIVE.** The number of observed job-loss events is unknown.

### 1. Research question and mechanism

> Among SCE respondents observed employed and then unemployed, does the post-separation rise in payment distress (Q30) and in realized delinquency or credit rationing (CA) depend on whether the loss was anticipated (prior Q13) and on prior reemployment beliefs (prior Q22)? Were those Q22 beliefs accurate (realized reemployment within the panel)?

Mechanism: anticipation allows precautionary adjustment (Stephens 2004; Hendren 2017). Expected duration governs how much distress a given loss causes.

### 2. Why care

It tests the reemployment-belief mechanism **in the state where it should matter**, after job loss. This is a sharper test than the original design.

### 3. Closest competitors

1. **Dias da Silva, Rusinova & Weißler (ECB WP 2817, 2023)**: consumption response to expected vs unexpected job loss, euro area.
2. **Stephens (2004)**.
3. **Keys (2018)**: credit consequences of displacement.

### 4. Remaining novelty

The U.S. debt and credit analogue of ECB WP 2817, plus validation of *employed* respondents' conditional finding beliefs against realized reemployment.

### 5. Variables

- Core monthly employment status (Q10/Q12), Q13, Q22 before; Q30, Q17/Q18 after; CA outcomes when waves straddle the event.
- Available; **event counts unverified**.
- Rough expectation of 600–1,000 E→U transitions, from about 108k employed person-months and a monthly hazard of about 0.6–0.9%. This assumption must be checked.

### 6. Unit and estimand

- Person × event time (−3…+6 months).
- Estimand: difference in ΔQ30 (post minus pre) between high and low prior Q13, and its slope in prior Q22.

### 7. Identification and confounders

- Associational.
- Job loss is not random; anticipation correlates with job type.
- Panel exit after job loss is likely selective (attrition rises with Q30).
- Short post-event windows.

### 8. Type

Associational and descriptive (belief accuracy).

### 9. New data

None beyond G-R1.

### 10. Feasibility

As a chapter only, and only if events suffice.

### 11. Main referee objection

> "Small, selected sample of job losers; ECB WP 2817 already shows the anticipation pattern."

Answerable only with enough events and a debt/credit outcome the ECB paper lacks.

### 12. Null informative

Weakly: power is the binding constraint.

### 13. Paper potential

A chapter; not standalone.

### 14. Cheapest pilot (1–2 hours)

Count E→U transitions in the existing panel with at least one pre-event and one post-event Q30, and the subset with CA waves on both sides.

**Continue** only if ≥600 events with Q30 on both sides and ≥150 with CA on both sides.

### Publication value

| Question | Answer |
| - | - |
| New knowledge | Whether anticipation and perceived reemployment speed cushion the financial impact of actual job loss in the U.S. |
| Why not answered | Euro-area consumption only; U.S. credit studies lack beliefs |
| What could make it disappear | Too few events; post-event attrition |

---

## G-R3 (narrowed fallback). Do stated delinquency expectations predict realized delinquency?

**Status: READY-CONDITIONAL** (same pilot as G-R1). Dependable; low upside.

### 1. Research question and mechanism

> At the individual level, does the SCE's headline "probability of missing a minimum debt payment" (Q30) predict later self-reported late payments (CA N15/N16)? How much do labor-income-risk beliefs (Q13, Q22) add beyond Q30 and credit score?

This validates the outcome the original G-P2 used. It also re-asks G-P2's question with a realized outcome.

### 2. Why care

- The NY Fed publishes Q30 monthly as "delinquency expectations", and media report it.
- No published individual-level validation against realized delinquency was found.
- If Q30 is uninformative, the original G-P2 outcome (and any research using it) is undermined. If it is informative, it is a cheap leading indicator.

### 3. Closest competitors

- Fermand et al. (2024) use Q30 as a covariate, not a validated measure.
- BIS WP 1258 (secondary) validates *self-reported* delinquency against records in Chile.
- No direct competitor found. NY Fed staff with access to credit-bureau links could pre-empt this.

### 4. Remaining novelty

A public-data validation of a widely cited expectation series.

### 5. Variables

Core Q30, Q13, Q22; CA N15, N16, N22, N1. Codebook-verified.

### 6. Unit and estimand

- Person × CA wave pair.
- Estimands: the onset probability gradient in Q30 (calibration curve), and the increment from Q13/Q22.
- Predictive metrics: AUC or Brier score with person-held-out folds, benchmarked against score-only and Q30-only models. This avoids the earlier "0.02% RMSE without a benchmark" problem.

### 7. Identification

Predictive; no causal claim. Confounders are irrelevant to validation but matter for interpretation.

### 8. Type

Predictive and measurement.

### 9. New data

As G-R1.

### 10. Feasibility

**High.** About 6–8 weeks of analysis.

### 11. Main referee objection

> "Self-reported delinquency validating self-reported expectations."

Partly answerable: report it as "consistency between two survey reports", with external validity evidence for self-reports.

### 12. Null informative

**Yes.** An uninformative headline expectation series is a substantive finding for its users.

### 13. Paper potential

- Dependable master's thesis.
- Possibly a short paper or policy note.
- Limited signal for PhD applications beyond careful empirical work.

### 14. Cheapest pilot

Same as G-R1: count onsets and tabulate N15 onset rates by Q30 bins (a descriptive table only).

### Publication value

| Question | Answer |
| - | - |
| New knowledge | Whether the delinquency-expectation series is informative about realized delinquency at the person level |
| Who cares | Users of SCE data; macro-financial monitoring; survey methodologists |
| What could make it disappear | Pre-emption by NY Fed staff with bureau-linked data; too few onsets |

---

## Considered and not proposed

| Candidate | Why not |
| - | - |
| Original G-P2 (finding beliefs → Q30) | Answered (null for reported beliefs). Further work is specification search |
| Narrowed G-P2 (previous Claude: bound plus measurement-error analysis) | Dominated by G-R3. It re-describes a null, and the IV route is weak and assumption-dependent |
| Instrumenting Q22 with commuting-zone labor-market conditions | Local conditions affect debt distress through income, house prices and credit supply. The exclusion restriction fails. **Reject as an IV**; local conditions may be used only descriptively (do beliefs track local tightness?) |
| Subgroup search (age, income, education) for a significant Q22 effect | Excluded by design |
| Switching to Labor Market Survey outcomes (search, reservation wages) | Occupied by Mitra (2026) and Faberman et al. (2022); labor, not finance |
