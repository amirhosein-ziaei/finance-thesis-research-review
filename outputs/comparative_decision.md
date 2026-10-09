# Comparative decision (preliminary)

Date: 9 October 2026. No numerical scores are used. Fatal objections are stated explicitly.

"Pilot-dependent" means the answer depends on a 3–8 hour data check (`next_30_hours.md`) that has **not** been run.

## 1. Options compared

| ID | Option | Source |
| - | - | - |
| O1 | Original E-N01: recoupment timing near expiry, plus incidence | Adjudication |
| O2 | Narrowed E-N01: ledger reconciliation and shareholder incidence (6 funds, expandable to 20) | Phase 3 GO |
| O3 | **Redesigned E-N01 (E-R1, with E-R2 as extension)**: contingent fee subsidies at universe scale using N-CEN C.8, prospectus XBRL and N-PORT, validated on N-CSR | This review |
| O4 | Original G-P2: finding beliefs → Q30 beyond job-loss beliefs | Adjudication |
| O5 | Narrowed G-P2: bound plus measurement-error analysis | Phase 2 |
| O6 | **Redesigned G-P2 (G-R1, with G-R2 as extension)**: precautionary credit, rationing and delinquency under perceived labor-income risk, using SCE core + Credit Access | This review |
| O7 | G-R3: validation of Q30 against realized (self-reported) delinquency | This review |
| — | Adjacent alternatives | **None recommended** (`adjacent_alternatives.md`) |

## 2. Comparison

| Criterion | O1 | O2 | O3 (E-R1) | O4 | O5 | O6 (G-R1) | O7 (G-R3) |
| - | - | - | - | - | - | - | - |
| **Novelty** | High in principle | Low–moderate (descriptive) | **High**: no paper on recoupable vs non-recoupable subsidies; open question flagged by Christoffersen (2001) | Low: occupied by Mitra (2026) | Low | **Moderate**: distinct from Fermand et al. (2024), Braxton et al. (2024) | Moderate-low |
| **Economic significance** | Moderate | Low (2 positive-recovery funds, ~9–11 bps) | **Pilot-dependent**: fee incidence, scale pass-through, shrouded deferred fees; disappears if recoupment is rare | Low | Low | Moderate–high (credit as insurance, rationing, private information) | Moderate (validity of a headline indicator) |
| **Measurement credibility** | Fails (vintages undisclosed) | Good but tiny; 0 of 27 intervals fully reconciled | Good for incidence flags (validation needed: documented misreporting); amounts on subsample only | Weak (hypothetical, noisy Q22) | Same | Moderate: self-reported, 12-month retrospective, 4-monthly; ≤3 waves per person | Moderate (self-report vs self-report) |
| **Identification** | **Fatal**: age = time-to-expiry; headroom confound | Accounting counterfactual only | Descriptive plus associational; mechanical contrast with selected contracts | Associational; answered | Assumption-heavy IV | Associational; need-vs-precaution confound partly testable | Predictive (none needed) |
| **Data availability** | Hand-collected, partial | Hand-collected | **SEC structured data: field names verified; values not yet inspected** | Verified, used | Verified | **Fields verified via codebook; match rate unverified** | Same as O6 |
| **Research risk** | Very high | Low risk, low value | Moderate (prevalence; XBRL parsing) | Done | Low | Moderate (event counts; distinctness from Fermand et al.) | Low |
| **Time to credible results** | Never (causal) | 2–3 months | 3–4 months after pilot | Done | 1–2 months | 2–3 months after pilot | 1–2 months |
| **Thesis completion probability** | Low | High | High if pilot passes (descriptive E1 nearly guaranteed) | Done | Very high | High | Very high |
| **Working-paper potential** | — | Weak | **Credible; field-journal possible if prevalence is material** | Weak | Weak | Credible; field-journal possible | Short paper or note |
| **PhD signaling** | — | Moderate (institutional care) | **Strong**: new data source, contracts, asset management, measurement validation | Weak–moderate | Weak–moderate | Moderate–strong (household finance, careful survey econometrics) | Moderate |
| **Fatal objection** | **Unidentifiable deadline effect** | "Six selected funds; so what?" | "Mechanical and economically small" (fatal **only** if the pilot shows low prevalence) | "Answered null; predictable from Mitra" | "Re-description of a null" | "Proxy for distress or uncertainty; Fermand et al. already did it" (answerable with prespecified tests) | "Survey-validates-survey" (partly answerable) |

## 3. Distinctions requested

| Role | Choice | Reason | Condition |
| - | - | - | - |
| **Best high-upside research opportunity** | **O3: E-R1, with E-R2 if discretion exists** | The only option combining a documented open question, a never-used universe dataset (N-CEN C.8), and a contracting mechanism with policy relevance | N-CEN shows material prevalence and exercise (thresholds in `E_N01_redesigns.md`) |
| **Best dependable master's thesis** | **O6: G-R1, with O7 (G-R3) as built-in fallback** | Data are public, small and partly processed already. Several prespecified outcomes; G-R3 guarantees a finished chapter | Credit Access match rate ≥50% and enough delinquency onsets |
| **Best next empirical feasibility pilot** | **N-CEN C.8 tabulation plus 20-fund validation** (about 8 h). Then the Credit Access merge count (about 4 h) | Both are cheap and objective, and each settles its project's decisive uncertainty | Requires your approval and a SEC contact User-Agent string you supply |

## 4. What to stop

- **Stop O1** (the original E-N01 timing question). It fails on identification, and no further work can fix that with public data.
- **Stop O4** (the original G-P2 question). It is answered.
- **Do not pursue O2 or O5 as the thesis.** Keep O2's ledger protocol as E-R1's validation method. Keep O5's estimates as a short motivating section of G-R1 ("finding beliefs do not move stated distress, so where do labor-risk beliefs act?").
- **Do not start** the 20-fund/8-adviser ledger pilot proposed in Phase 3. The N-CEN pilot supersedes it.

## 5. Preliminary recommendation

1. **Run one bounded pilot pair** before choosing a primary thesis. Do not start a new topic search yet. The two pilots cost about 12 hours and each has a pre-set stop rule.
2. **If E-R1 passes:** make E-R1 the primary thesis, with G-R1 dropped or kept as a fallback only.
   - It offers the strongest novelty and signaling of anything reviewed.
   - Its descriptive core (prevalence, exercise, incidence) is nearly guaranteed once N-CEN values are confirmed. The upside (E2 pass-through, E-R2 discretion) is incremental on top.
3. **If E-R1 fails and G-R1 passes:** make G-R1 the primary thesis, with G-R3 as the guaranteed chapter.
   - Accept that its novelty is moderate.
   - Distinguish it sharply from Fermand et al. (2024) in the first two pages.
4. **If both fail:** begin a new primary-thesis search under the rules in `adjacent_alternatives.md`. Treat the G-P2 narrowed version (O5/O7) only as an emergency completion path.

**Unresolved items** that could change this ranking:
- actual N-CEN C.8 values and misreporting rates;
- the sign convention for recoveries in prospectus XBRL;
- the Credit Access match rate and coverage end;
- whether an unpublished SSRN paper uses N-CEN C.8 or SCE CA × job-loss beliefs (SSRN could not be searched directly in this session).
