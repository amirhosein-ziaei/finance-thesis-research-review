# Critique of the previous Claude feasibility work

Scope: the October 2026 adjudication report, E-N01 Phases 1–3 (ZIP plus the `claude/hopeful-fermi-3mg764` branch) and G-P2 Phases 1–2 (ZIP plus the public `claude/trusting-allen-6o7x90` branch).

I have not re-run either pipeline. My critique concerns reasoning, framing, literature coverage and data coverage. It is not a re-estimation.

Severity scale: **High** (changes a recommendation), **Medium** (changes interpretation or scope), **Low** (presentation or process).

## Overall verdict

The earlier work was careful about **measurement honesty**:
- strict versus conditional ledgers;
- no FIFO assumptions;
- prespecified models;
- explicit "exploratory" labels;
- no causal claims.

That deserves credit. Its main weaknesses are elsewhere:
1. **Data search was too narrow.** It missed SEC N-CEN Item C.8 and the SCE Credit Access module. Both bear directly on the decisive limitations each project cited.
2. **Competitor matrices were mis-specified.** Several "direct competitors" are not direct, and closer papers were missed.
3. **Benchmarks were not derived from the economic mechanism** (G-P2's 2pp).
4. **Feasibility was confused with importance.** The E-N01 "GO for a narrowed thesis" was declared without evidence that the narrowed question matters economically.

---

## A. The October 2026 adjudication report

| # | Claim or reasoning | Problem | Evidence | Severity |
| - | - | - | - | - |
| A1 | E-N01 data: "The indispensable observations are manually extracted fields, not a ready-made SEC numeric table" | **Incorrect for incidence.** Since 2018, Form N-CEN Item C.8 reports per fund-year whether waivers are subject to recoupment and whether recoupment occurred, published as structured SEC data sets. Prospectus risk/return XBRL data carry class-level waiver magnitudes (2011–) | `formn-cen.pdf` Item C.8; `ncen_readme.pdf` fields `HAS_EXP_SUBJ_RECOUP`, `HAS_EXP_RECOUPED` (register D01–D02); Black & Kölbel use the RR waiver data (E06) | **High.** It sent the project toward expensive hand ledgers before measuring prevalence |
| A2 | E-N01 "direct competitor matrix": Christoffersen 2001, Wahal–Wang 2011, Evans–Fahlenbrach 2012, Scheld et al. 2026, Berk–Green 2004 | Three of five are not competitors on waivers (governance, distribution, theory). It **missed**: Christoffersen's own "option value of waiving / recapture" passage, which explicitly marks recapture as open; Christoffersen & Musto 2002; Farinella & Jorgensen 2002; Di Maggio & Kacperczyk 2017 (money-fund waivers as sponsor subsidies); Black & Kölbel 2024 (the closest recent paper, which tests "raise fees after waiver"); Barber–Odean–Zheng 2005; Deli 2002 | `E_N01_literature_audit.md` §3 | **Medium.** The novelty conclusion survives, but the referee-relevant threat (Black & Kölbel) was not identified |
| A3 | E-N01 "Novelty: CLEARLY DISTINCT AFTER SEARCH" for the expiry question | Distinct, but **novelty without identifiability**. The report's own kill rule ("age equals time-to-expiry") is triggered by contract design (common 3-year windows), not merely by small samples. That was foreseeable before the pilot | Phase 3 §1, §2-G | Medium |
| A4 | E-N01 planning target "80–150 funds across 25–30 advisers" built from hand-reconciled ledgers | It set no prevalence or materiality gate *before* hand collection. A one-day N-CEN tabulation would have shown whether recoupment is common enough to matter | — | **High** (resource allocation) |
| A5 | G-P2 benchmark "2pp per 10pp" adopted provisionally | Not derived from the mechanism. Q22 matters only conditional on job loss. Mean Q13 = 13.7% over 12 months implies about 3.6% over 3 months, so 2pp would require a conditional effect of about 55pp per 10pp. The project kept the benchmark "exactly as the adjudication proposed" | `model_specification.md` §6; `desc_distributions.csv` | Medium. The verdict "precisely small vs 2pp" was uninformative, though the within CI happens to exclude plausible sizes too |
| A6 | G-P2: "No realized default … verified in the core file … A supplementary module may add fields only after checking common IDs" | The caution was correct, but the check was never done. The Credit Access module (public, `userid`-keyed) has debt holdings, balances, late payments 30+/90+ days, rejections, discouragement and credit score | Header and codebook inspected (register SD1) | **High** for the G-P2 redesign question |
| A7 | G-P2 competitor matrix | Missed the most relevant SCE paper on beliefs and credit behaviour (Fermand, Kuhnen, Li & Ben-David, MS 2024, core + Credit Access), the ECB anticipated-job-loss paper (WP 2817), Braxton–Herkenhoff–Phillips (JPE 2024), Hendren (2017) and the belief-attenuation literature | `G_P2_literature_audit.md` §2 | Medium |
| A8 | Report calls Hartmann–Leth-Petersen and Mitra "full manuscript inspected" | Consistent with what I found in both papers. The later G-P2 sessions could not open them, yet still asserted agreement with "the closest existing paper" (see C4) | — | Low |

## B. E-N01 Phases 1–3

| # | Claim | Problem | Severity |
| - | - | - | - |
| B1 | "GO for a narrowed thesis: adviser fee-recovery accounting and shareholder incidence" | Feasibility is shown for **six purposively chosen funds**. Importance is not. Positive recoveries occurred at **two** funds, of about $25k–$119k a year (about 9–11 bps). No prevalence, aggregate magnitude or population share was measured. The adjudication itself required re-adjudicating the narrowed contribution "before committing", and Phase 3 recommends it before that re-adjudication | **High** |
| B2 | Sampling | Funds came from keyword hits (as Phase 3 acknowledges). Two of four advisers share an administrator template (Northern Lights/Ultimus), so independence is overstated. Fine for feasibility; any incidence statistic from this sample has no population meaning | Medium |
| B3 | "No kill condition for the whole project is triggered" | The horizon gate passed "provisionally" with no measured human time per history. The deadline component's kill rule *was* triggered, so the project's main novelty is gone. "No kill" is therefore technically true but substantively misleading | Medium |
| B4 | Incidence in bps from "advisory fee ÷ rate" | A reasonable approximation (±1 bp), but N-CEN reports monthly and daily average net assets (C.19). The approximation was unnecessary for N-CEN filers | Low |
| B5 | Strict ledger: 0 of 27 intervals fully reconciled | Correctly reported. The implication was under-drawn: if a fully disclosed reconciliation is never observed, a ledger-based paper cannot defend vintage-level claims at scale. That is another reason to move to incidence flags plus amounts, not balances | Medium |
| B6 | Process: SEC access | The manifest records an EDGAR retrieval "with a User-Agent that included the project owner's email address (not authorised; disclosed to the owner)". Later retrievals were authorised. Future SEC bulk retrieval should use a contact string the owner explicitly provides | Low (process/ethics) |
| B7 | Strengths worth keeping | Strict/conditional separation; refusal to assume FIFO; "semiannual flows can be reversed by year end"; the format typology (remaining-balance vs original-amount schedules). These become the **validation protocol** for a universe-level redesign | — |

## C. G-P2 Phases 1–2

| # | Claim | Problem | Severity |
| - | - | - | - |
| C1 | "The null within estimate is **not** the result of too little variation" | True for *reported* variation. But 51% of consecutive Q22 changes are ≥10pp (mean absolute change 14.8pp) in a hypothetical question. Much of that within variation is plausibly noise, and noise is "variation" that attenuates. Phase 2 acknowledges this in S3c but still headlines "precise null" | Medium |
| C2 | Pooled association attributed to "stable pessimism, financial position, response style" | Person FE also remove **true** persistent differences in reemployment prospects (occupation, region, skills), the economically meaningful variation. The FE null shows that monthly fluctuations do not co-move, not that reemployment prospects are irrelevant to financial fragility | Medium |
| C3 | Prediction exercise: "0.02% RMSE, negligible" | No reference increment (e.g., the gain from Q13 or from Q30 lags alone). The target is the next-month *stated* probability with persistence 0.73, so almost any single regressor yields tiny RMSE gains. The 1% "material" threshold has no stated basis | Medium |
| C4 | "Position the result as consistent with Mitra's finding … it agrees with the closest existing paper" | At the time the full texts had **not** been opened (`literature_overlap.md` says so). Mitra studies search, not finance. Agreement is an analogy | Medium |
| C5 | "No realised debt behaviour or debt-holding indicator is available" (Phase 2 publication outlook) | True for core; false for the public Credit Access module (N1, N2, N15, N16). This was the stated main reason for the weak outlook | **High** for redesign |
| C6 | S1 proxy for non-borrowers (Q30 = 0 in every month) | Crude. The Credit Access N1_7 ("possess no credit products") measures it directly for module respondents | Low |
| C7 | IV S3c (Δbelief instrumented by t−2 level) | Exclusion is doubtful (mean-reverting pessimism episodes), and the IV is weak-ish (F ≈ 30). Correctly labeled inconclusive. The plan to "search no further instruments" is right | Low |
| C8 | Recommendation "narrow the question" | Reasonable as a completion path. But the narrowed contribution ("bound on incremental content … decomposition … measurement-error analysis") is mostly a re-description of a null. Its scientific value depends on implications that were not argued, e.g., for models that use job-loss beliefs as sufficient statistics for income risk | Medium |

## D. Cross-cutting issues

1. **Data before importance.** Both projects measured the hardest objects first (vintage ledgers; within-person belief co-movement) before establishing whether the phenomenon is common or material. A cheap prevalence or validation check should come first (`next_30_hours.md`).
2. **Benchmarks.** Thresholds (5 bps; 2pp; 1% RMSE) were set as round numbers, not derived from mechanism or literature. Future gates should be justified: a mechanism-implied effect size, or the distribution of comparable effects in the closest papers.
3. **"Precise null" rhetoric.** A precise null on a subjective outcome is not automatically a contribution. It needs a theory under which the effect should have been large, and the earlier work did not supply one (see A5).
4. **Unverified human validation.** Neither project passed its own human-validation gate (E-N01 second coder; G-P2 50 histories). Every number remains provisional.
