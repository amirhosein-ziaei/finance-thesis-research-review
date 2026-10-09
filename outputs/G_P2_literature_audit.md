# G-P2 literature audit: reemployment beliefs and debt distress

Date: 9 October 2026. Companion files: `source_register.csv` (G-, SD- and A- IDs), `critique_of_previous_claude.md`, `G_P2_redesigns.md`.

**Bottom line.**

1. The original question has been answered as well as the public core data allow. Month-to-month changes in an employed person's *reported* hypothetical job-finding belief do not move their *reported* three-month debt-payment expectation.
2. The literature makes this result **unsurprising rather than important**:
   - The closest new paper (Mitra 2026, full text read) finds that job-loss fear, not job-finding beliefs, drives employed workers' precautionary search.
   - Belief-to-action pass-through is known to be weak and attenuated (Giglio et al. 2021; Ameriks et al. 2020).
3. **Two previous claims are wrong or overstated.**
   - The data situation: the public SCE **Credit Access module** is keyed by the same `userid` format. It contains debt holdings, balances, self-reported **late payments (30+ and 90+ days)**, applications, rejections, discouragement, credit score and a liquidity-buffer question. "No debt-holding indicator or realized debt behaviour is available" therefore holds only for the core file.
   - The 2pp benchmark was never mechanism-consistent (§3).
4. A redesign around **credit-market actions and realized delinquency**, with job-loss risk as the main belief and reemployment beliefs as a mechanism-based moderator, is feasible.
5. It faces a direct competitor on the same data (Fermand, Kuhnen, Li and Ben-David, *Management Science* 2024). Its novelty is moderate, not high.

---

## 1. Audit of the G-P2 research materials

### 1.1 What I read

| Document | Source | Read? |
| - | - | - |
| Adjudication, G-P2 sections | ZIP | Yes |
| `preliminary_regressions.md`, `prediction_comparison.md`, `phase2_feasibility_decision.md` | ZIP | Yes |
| `model_specification.md`, `measurement_sensitivity.md` | **Missing from the ZIP.** Read from the public branch `claude/trusting-allen-6o7x90` of `amirhosein-ziaei/reemployment-beliefs-debt-thesis` | Yes |
| `literature_overlap.md`, `data_availability.md`, `preliminary_descriptives.md`, `desc_distributions.csv` | Same branch | Yes (relevant parts) |
| Code (`code/05_phase2_models.py` etc.) and raw SCE files | Code on branch; raw data git-ignored | Code **not audited line by line**; raw data **not re-downloaded** |

**Verification statement.** I did **not** re-run or independently verify any G-P2 estimate. All numbers below are the earlier project's, and its own label applies: "exploratory, pending independent human validation". The 50-history human validation gate (`manual_history_review_done = false`) was never passed.

### 1.2 Exact original research question

> "Among employed households, does perceived difficulty finding another job predict subjective debt payment distress beyond perceived job loss risk, and does this relationship strengthen when income recovery is expected to be difficult?"

Variables:
- `Q22new`: percent chance of finding an acceptable job within 3 months *if the job were lost this month*.
- `Q13new`: 12-month job-loss probability.
- `Q30new`: 3-month probability of missing a minimum debt payment.

### 1.3 Evidence obtained (reported, not re-verified)

- 108,388 employed person-months (15,673 persons), Aug 2013–Oct 2025.
- **Pooled:** +0.30pp of Q30 per 10pp lower job-finding probability [0.22, 0.38].
- **Within person:** −0.05 [−0.10, 0.005].
- **Job-loss belief:** +2.37 pooled, +1.09 within.
- **Interaction:** +0.18pp (Q13 = 50 vs 5) [0.06, 0.29].
- **Prediction:** next-month RMSE gain about 0.02%.
- **Measurement-error IV** (first differences instrumented by t−2 levels; F ≈ 30): +0.83 [−0.58, 2.24].
- 16 of 17 sensitivity checks are "precisely small".

### 1.4 Supported versus overstated conclusions

| Earlier conclusion | Assessment |
| - | - |
| Within-person association for *reported* beliefs is near zero and precisely estimated | **Supported**, conditional on the unvalidated pipeline |
| Pooled association is between-person (stable pessimism or financial position) | **Plausible but not shown.** Person FE also absorb *real* persistent differences in reemployment prospects (occupation, local labor market, skills), so "pessimism" is one of several readings |
| Predictive gain is "negligible" (0.02% RMSE) | **Correct as computed, weak as evidence.** No benchmark increment was reported, e.g., what Q13 adds to the same baseline. With persistence 0.73 and a noisy target, RMSE gains from any single belief are small. The 1% threshold is arbitrary |
| "Precisely small" relative to 2pp | **Benchmark not mechanism-consistent** (see §3). The precise null is informative against *any plausible* mechanism size only because the within CI upper bound is ~0, not because it rules out 2pp |
| "No realised debt behaviour or debt-holding indicator is available" (Phase 2 publication outlook) | **True for the core file; false for public SCE microdata.** The Credit Access module has both (§4) |
| "The result agrees with the closest existing paper" (Phase 2) | **Not established at the time.** `literature_overlap.md` states that Mitra and Hartmann–Leth-Petersen full texts could not be opened. Having now read Mitra: her finding concerns search, not finance, so "agreement" is an analogy, not replication |
| Publication outlook "weak" | **Agree** for the original and narrowed versions |

---

## 2. Closest literature

### 2.1 Labor-market beliefs of the employed and unemployed

- **Mitra (draft June 2026, FRB)** [G03; full text read, 69 pp.]
  - Data: SCE core merged with the SCE Labor Market Module (4,226 employed worker-months, 2014–2023) and the ECB CES.
  - Macro pessimism raises perceived job-loss risk and on-the-job search (about 24 extra minutes per week per SD).
  - The search response is driven by **fear of job loss, not job-finding expectations**. She uses separation beliefs, conditional finding beliefs (the same Q22 item) and their interaction.
  - Results are explicitly associational. No debt or finance outcome appears; "expected household financial conditions" is only a control.
  - **Implications.** (i) The separation/finding distinction and its interaction are occupied. (ii) Merging SCE modules to the core by respondent is standard practice. (iii) Her result predicts G-P2's null: job-finding beliefs of the employed carry little behaviourally relevant variation.
- **Mueller, Spinnewijn and Topa (2021, AER)** [G01; abstract]: for **unemployed** job seekers, finding beliefs strongly predict finding but are optimistically biased, sticky with duration and underreactive. This validates finding beliefs for the unemployed. It does **not** validate the hypothetical conditional belief of the employed. A three-month finding probability is not an expected duration.
- **Koşar and van der Klaauw (2025, JOLE)** [G18; abstract snippet]: SCE workers' job-exit and earnings expectations are heterogeneous and largely consistent with realized outcomes.
- **Faberman, Mueller, Şahin and Topa (2022, Econometrica)** [G17], **Balleer et al. (2026, JME)** [G20], **Kuchler and Zafar (2019, JF)** [G19]: background on SCE labor modules, belief bias, and pessimism from personal experience (metadata or BK).

### 2.2 Job-loss expectations and household financial behaviour

- **Hartmann and Leth-Petersen (2024, Labour Economics)** [G02; Nov 2023 WP full text read]
  - Data: Danish annual surveys 2010–2016 linked to administrative income, liquid savings and UI data.
  - Expectations predict unemployment but are upward-biased.
  - +10pp expectation → +0.3pp UI membership; higher subjective income risk → higher liquid-savings rate (+2.36pp).
  - **Uses job-loss expectations only. No job-finding beliefs, no debt outcome.**
- **Stephens (2004, REStat)** [G04, BK] and **Hendren (2017, AER)** [G05, abstract]: job-loss expectations predict job loss; consumption falls before anticipated loss. Hendren adds that workers hold **private information** that would unravel private UI markets.
- **Dias da Silva, Rusinova and Weißler (2023, ECB WP 2817)** [G21; full text read]
  - Data: ECB CES, 2020–2023.
  - Consumption falls after *unexpected* job loss, muted when expected. Stronger for workers with worse local-labor-market perceptions and low liquid wealth.
  - **This occupies the "anticipated vs unanticipated job loss" design for consumption.**
- **Pettinicchi and Vellekoop (2019, SAFE WP 249)** [G22; abstract]: higher job-loss expectations lead to cheaper cars, more saving and fewer risky assets. A discussant calls the effects small and mainly descriptive.

### 2.3 Unemployment, credit and default (realized shocks)

- **Keys (2018, REStat)** [G08], **Gerardi, Herkenhoff, Ohanian and Willen (2018, RFS)** [G07], **Ganong and Noel (2019, AER)** [G06]: realized job loss raises delinquency and default, and spending falls at job loss and at UI exhaustion (BK).
- **Braxton, Herkenhoff and Phillips (2024, JPE)** [G09; search summary]: lenders extend credit before and after job loss despite adverse selection, because of registries and non-contingent revolving lines. Unconstrained job losers borrow; constrained ones delever or default. **This implies that acquiring non-contingent credit lines *before* job loss is valuable.** That is the mechanism the best G-P2 redesign tests with beliefs.
- **Hundtofte, Olafsson and Pagel (2019, NBER WP)** [G10]: individuals do not increase credit when unemployed (a "credit smoothing" puzzle).
- **Sullivan (2008, JHR)** [G11]: only asset-holding households borrow unsecured during unemployment.
- **Druedahl and Jørgensen (2018, QE)** [G12]: the risk of losing access to new credit (higher in unemployment) motivates precautionary behaviour.
- **Exler, Livshits, MacGee and Tertilt (Philadelphia Fed WP 21-42, rev. 2026)** [G23]: over-optimistic borrowers (with SCE-based motivation) borrow too much and default too little.

### 2.4 SCE beliefs and credit behaviour: the main threat to a redesign

**Fermand, Kuhnen, Li and Ben-David (2024, Management Science)**, "Extrapolative Uncertainty and Household Economic Behavior"; WP title "Expectations Uncertainty and Household Economic Behavior" (NBER w25336) [G13; WP full text read]
- Data: SCE core (2013–2017) merged with the **Credit Access** and **Household Finance** modules.
- More *uncertain* respondents (wider subjective densities) act more cautiously, including seeking credit-line increases (Credit Access item N17a).
- The published version narrows to macro (inflation, home-price) uncertainty.
- Text search of the WP finds job loss only in literature discussion. **Not used:** job-loss probabilities, job-finding probabilities, realized delinquency (N15/N16).
- A redesign must be clearly distinct: *labor-income-risk levels* versus *uncertainty*, and *delinquency and rationing* versus *intentions*.

### 2.5 Belief–action attenuation and measurement error

- **Giglio, Maggiori, Stroebel and Utkus (2021, AER)** [G15] and **Ameriks, Kézdi, Lee and Shapiro (2020, JBES)** [G14]: belief-to-portfolio sensitivities are low; correcting measurement error raises them (BK).
- **Drerup, Enke and von Gaudecker (2017, JoE)** [G16]: models fit much better for respondents with precise subjective data (BK).
- **Implication.** The G-P2 null belongs to a known class of "weak pass-through from stated beliefs" results. A precise null is only informative if the paper explains why this belief should matter more than others and shows that measurement error cannot account for the gap. G-P2's IV attempt was inconclusive.

---

## 3. Why is the within-person result near zero? Eight candidate explanations

The near-zero result could come from several sources. I assess each against the evidence; none is assumed correct.

| # | Explanation | Evidence for | Evidence against | Verdict |
| - | - | - | - | - |
| 1 | **Genuinely weak economic connection** | The employed rarely lose jobs within the Q30 horizon. Mitra finds finding beliefs do not drive search either | Realized unemployment duration clearly matters for default ex post (G06–G08) | **Likely, for the *ex ante* mapping among the employed** |
| 2 | **Mis-specified mechanism** | Q22 is *conditional on job loss this month*, so it can matter for Q30 only in proportion to the near-term loss probability. Mean Q13 = 13.7% over 12 months implies about 3.6% over 3 months. Even a conditional effect of +10pp of Q30 per 10pp lower finding probability yields only about **0.36pp** unconditionally. The 2pp benchmark would need about 55pp per 10pp, which is impossible | The within CI upper bound (~0.005) still excludes 0.36, and the Q13 = 50 interaction CI upper bound (0.22) is below the mechanism-implied size | **Correct critique of the benchmark.** Even against a mechanism-consistent benchmark, the reported-belief null holds |
| 3 | **Measurement error in Q22** | Hypothetical conditional probabilities are hard to answer. 51% of consecutive-month changes are ≥10pp (mean absolute change 14.8pp), plausibly mostly noise. The pooled IV rises by about a quarter. The within IV is +0.83 [−0.58, 2.24] | Q13 changes, presumably also noisy, still co-move with Q30 within person (+1.09) | **Plausible, unresolved.** Data cannot separate a small true effect from noise (the earlier conclusion was correctly hedged) |
| 4 | **Finding probability ≠ expected duration** | A 3-month conditional probability truncates the duration distribution. Long-duration fears may not appear in a 3-month item | No SCE core item measures expected duration for the employed. The ECB topical module does, and Mitra finds no heterogeneity there | **Real conceptual limitation; untestable with core data** |
| 5 | **Missing debt ownership/exposure** | Q30 is asked of everyone. The S1 proxy (Q30 = 0 every month) is crude | S1 left the estimate unchanged. Non-borrowers add no within variation | **Not the main cause, but now fixable** (Credit Access N1/N2) |
| 6 | **Short panels/attrition** | ≤12 months; attrition rises with Q30 (+0.69pp per 10pp) | S5/S6 sensitivity unchanged | **Unlikely to explain the null**; it does limit G-R2 event counts |
| 7 | **Overly broad pooling** | Effects should concentrate among liquidity-constrained, indebted, high-loss-risk workers | The one prespecified interaction (with Q13) was tiny | **Possible, but searching subgroups now would be specification search.** Only mechanism-based heterogeneity (liquidity buffer, debt service), prespecified, is defensible |
| 8 | **Outcome misses the adjustment margin** | Households adjust to income risk through savings, UI, search, credit lines and consumption (G02, G03, G21, G13), not through their *stated* probability of missing a payment | Q30 does respond to Q13 within person | **Likely.** This is the strongest argument for changing the outcome, on mechanism grounds, *not* to chase significance |

**Synthesis.** The most defensible reading combines 1, 2, 3 and 8:
- Among the employed, a hypothetical, noisy, 3-month conditional finding belief should barely move a 3-month payment-distress expectation.
- The economically relevant margins are credit access, liquidity and realized delinquency, and they are observed elsewhere in the SCE.

This justifies a **new, prespecified question** rather than more specifications of the old one.

---

## 4. Data reassessment

Verified this session by reading only the headers and codebook sheets of the public files through HTTP range requests. No microdata files were downloaded in full.

| Item | Status |
| - | - |
| **SCE Credit Access module** (every 4 months: Feb/Jun/Oct; data rows from 201310) | `userid`, `date`, `weight`, plus: N1 debt products held (card, mortgage, student, home-equity, auto, other, none); N2 balances by product; N3 maxed-out card; N4 applications and limit-increase requests (12m); N5–N7 reasons for not applying, incl. "would not be approved"; N9–N11 granted; N14 lender closed accounts or cut limits; **N15 late >30 days (12m); N16 late >90 days (12m)**; N17 application likelihood (next 12m); N21 expected approval; N22 credit score; N24/N25 needing/being able to raise $2,000 next month [SD1] |
| **SCE Household Finance module** (from 201408; questionnaire listed as 2019) | `userid`, `date`; savings and investments excluding retirement (d16new); housing debt and 3-months-late housing payment (f17–f20new); non-housing debt and composition (g1) [SD2] |
| **SCE core** | `_STATE` and `_COMMUTING_ZONE` present in the public file, besides Q13new, Q22new, Q30new, Q17new/Q18new (unemployed finding) [SD3] |
| Linkage | `userid` has the same 8-digit `7000xxxx` format in core, Credit Access and Household Finance. Mitra (core + Labor Market) and Fermand et al. (core + Credit Access + Household Finance) merge modules to the core. **The actual match rate in the public files is not verified (pilot item).** |
| Timing | Core and Credit Access released with a 9-month lag; other modules 18 months [SD4]. First-month respondents get no modules, so each person has **at most about 3 Credit Access waves**. N15/N16 are 12-month retrospective, so new-delinquency onset is identified only between waves |
| Codebook caveat | The Credit Access codebook's date-range line says "201310–201710", likely stale. The coverage end of the public file must be checked |

---

## 5. What is answered and what remains open

| Question | Status |
| - | - |
| Do job-loss expectations predict job loss and self-insurance (savings, UI)? | **Answered** (Denmark: G02; Netherlands: G22; U.S. consumption: G04, G05) |
| Do employed workers' finding beliefs drive search? | **Answered: weakly or not; job-loss fear dominates** (G03) |
| Do finding beliefs predict *subjective* payment distress within person? | **Answered (this project): no, for reported beliefs** |
| Does realized job loss raise delinquency? | **Answered** (G06–G09) |
| Do expected vs unexpected job losses differ in their consumption effect? | **Answered for the euro area** (G21) |
| Does belief *uncertainty* predict credit-seeking intentions? | **Answered** (G13) |
| Do U.S. workers who perceive higher job-loss risk **acquire or lose credit access before the shock**, and does this differ with expected reemployment difficulty? | **Open.** No paper found |
| Do labor-risk beliefs predict **realized delinquency** beyond self-reported credit score and current distress expectations? | **Open** in public U.S. data. NY Fed insiders may hold SCE–credit-bureau links; no such paper was found |
| Does Q30, the NY Fed's headline "delinquency expectations" series, predict realized delinquency at the individual level? | **Open** in published work (none found) |
| Do ex ante reemployment beliefs moderate the debt-distress consequences of a realized job loss in the U.S.? | **Open, but power-limited** (event counts unknown) |

---

## 6. Answer to the main question

> *Can G-P2 be redesigned around a genuinely important and novel household Finance mechanism, or should it remain only a safe thesis fallback?*

**As framed, G-P2 should remain only a fallback.** Its contribution, a bounded null on a subjective outcome, is predictable from Mitra (2026) and the belief-attenuation literature, and its publication outlook is weak.

**A redesign is possible and better than the narrowed version, but its novelty is moderate.**
- The verified Credit Access linkage allows a credit-market question: precautionary credit acquisition, rationing and realized delinquency as functions of perceived labor-income risk.
- This connects to a live literature (Braxton–Herkenhoff–Phillips; Hundtofte–Olafsson–Pagel; Hendren).
- It sits close to Fermand et al. (2024).
- It relies on self-reported, 4-monthly, 12-month-retrospective items with at most three waves per person.

The redesign is a stronger master's thesis and a possible field-journal working paper. It is not a high-upside project unless the pilot shows enough within-person variation and enough delinquency events. See `G_P2_redesigns.md`.
