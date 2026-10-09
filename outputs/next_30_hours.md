# Next 30 research hours: plan, stop rules, minimum evidence

Date: 9 October 2026. **Nothing below has been started.** Data downloads and pilots require your explicit approval (per the brief).

**Before Block 1, supply a SEC contact string** for the EDGAR/DERA User-Agent (the SEC returns HTTP 403 without one). Use your own name and an address you authorize. The earlier E-N01 project once used the owner's email without authorization; avoid repeating that.

No regressions are planned in these 30 hours. The pilots are **counts, tabulations and source checks**.

## Block 0 — Reading (6 h, can start immediately)

Read the full texts that decide novelty. Take one page of notes each, recording the exact design, data and the claim that most threatens the redesign.

| Hours | Paper | Why |
| - | - | - |
| 1.5 | Black & Kölbel (Dec 2024), *The Puzzle of ESG Fund Fees* (PDF linked in register E06) | Closest recent waiver paper; their "discontinued waiver" test |
| 1.0 | Christoffersen (2001 JF; June 2000 manuscript), esp. §C "The Option Value of Waiving" | The open question E-R1 answers |
| 1.0 | Fermand, Kuhnen, Li & Ben-David (MS 2024; NBER w25336) | Main threat to G-R1 |
| 1.5 | Braxton, Herkenhoff & Phillips (JPE 2024) | Mechanism for G-R1 H1–H3 |
| 1.0 | Dias da Silva, Rusinova & Weißler (ECB WP 2817) | Main threat to G-R2 |

**Also:** try to obtain Christoffersen's 1998 dissertation via a library, and SSRN searches for "N-CEN" + "expense limitation/recoup" and for "Credit Access" + "job loss". SSRN was blocked in this session; record the results.

## Block 1 — E-R1 decisive pilot: N-CEN prevalence (8 h; approval needed)

| Step | Hours | Output |
| - | - | - |
| 1.1 Download all N-CEN quarterly ZIPs (2018q3–2026q3) and hash them into a manifest | 1 | `ncen_manifest.csv` |
| 1.2 Parse FUND_REPORTED_INFO, ADVISER and SUBMISSION. Keep the latest amendment per series × fiscal period. Flag money-market funds, ETFs and index funds | 2 | Clean series-year file (keep local; do not commit raw data) |
| 1.3 Tabulate C.8.a–d by fiscal year: counts, % of funds with waivers, AUM-weighted shares (C.19). Count distinct advisers with C.8.d = Y and adviser concentration | 1.5 | `ncen_c8_prevalence.md` (aggregate tables only) |
| 1.4 Construct the E-R2 feasible set (C.8.c = Y with recent C.8.b = Y, C.8.b = N in t) and its exercise rate | 0.5 | Same file |
| 1.5 **Validation:** random 10 fund-years with C.8.d = Y and 10 with C.8.c = Y & C.8.d = N. Open N-CSR notes and record agreement, recoupment amount, average net assets, schedule format, minutes per case | 3 | `ncen_validation.csv` with page citations |

**Stop rules** (fixed now):

| Outcome | Decision |
| - | - |
| Continue E-R1 | ≥150 series-years with C.8.d = Y (FY2018–25), from ≥40 advisers, no adviser >25%; **and** ≥500 series per year with C.8.c = Y; **and** ≤4 of 20 validation contradictions |
| Stop E-N01 entirely | <75 recouped series-years, **or** >50% in ≤5 advisers, **or** ≥8 of 20 validation contradictions |
| E-R2 viable | ≥300 feasible series-years with exercise rate in [20%, 80%] |
| Otherwise | Re-adjudicate (likely descriptive-only) |

**Minimum evidence to claim E-R1 is viable:**
- the prevalence table;
- the adviser-concentration statistic;
- 20 validated cases with citations;
- measured minutes per N-CSR case.

## Block 2 — E-R1 data-structure check: prospectus XBRL (3 h; approval needed)

| Step | Hours | Output |
| - | - | - |
| 2.1 Download one recent risk/return quarterly ZIP. Locate the waiver, gross and net elements and their class contexts | 1.5 | Field note |
| 2.2 Check whether recoveries appear as positive add-backs (sign convention) for 5 funds from Block 1.5 with known recoupment | 1 | Yes/no plus examples |
| 2.3 Search footnote text for "recoup", "recapture" and "reimburse … three years" | 0.5 | Count of matching classes |

**Stop rule:** if recoveries are not identifiable in the XBRL, drop the planned universe-level bps estimate. Rely on N-CEN incidence plus N-CSR amounts (still viable).

## Block 3 — G-R1/G-R3 decisive pilot: Credit Access merge (5 h; approval needed)

| Step | Hours | Output |
| - | - | - |
| 3.1 Download the CA complete microdata and questionnaire. Record hash, licence and coverage end month | 0.5 | Manifest |
| 3.2 Merge to the existing core panel (`reemployment-beliefs-debt-thesis` pipeline) on `userid` × `date` | 1.5 | Match-rate table |
| 3.3 Counts: employed person-waves; persons with ≥2 waves; base rates of N4_1/N4_4, discouragement (N5_5/N6), N15; N15 0→1 onsets among the employed; within-person SD of Q13 across waves; routing of N15/N4 from the questionnaire | 2 | `ca_merge_pilot.md` (aggregates only) |
| 3.4 G-R2 event count: E→U transitions with Q30 on both sides; subset with CA waves on both sides | 1 | Same file |

**Stop rules:**

| Outcome | Decision |
| - | - |
| Continue G-R1 | Match rate ≥50%; ≥10,000 employed person-waves; ≥3,000 persons with ≥2 waves; ≥150 onsets; coverage ≥2023 |
| G-R1 without H4 (re-adjudicate) | <75 onsets |
| Continue G-R2 | ≥600 events with Q30 both sides and ≥150 with CA both sides |
| Stop G-R1 | Match rate <50% or no N4/N15 routing to employed borrowers |

## Block 4 — Prespecification and decision (5 h)

| Step | Hours | Output |
| - | - | - |
| 4.1 For whichever project passes, write a pre-analysis plan before any regression: estimands, outcomes, the single heterogeneity dimension, benchmark effect sizes derived from mechanism or literature (not round numbers), inference | 3 | `pre_analysis_plan.md`, committed before estimation |
| 4.2 Two-page decision memo for the supervisor (Abedifar for E-R1; Sepahsalari for G-R1, per the adjudication's fit notes): pilot tables, threats, timeline to April–May 2027 | 2 | `decision_memo.md` |

## Budget summary

| Block | Hours | Approval needed |
| - | -: | - |
| 0 Reading | 6 | No |
| 1 N-CEN pilot | 8 | **Yes** |
| 2 XBRL check | 3 | **Yes** |
| 3 Credit Access pilot | 5 | **Yes** |
| 4 Pre-analysis plan + memo | 5 | No |
| Buffer (failed downloads, SSRN checks) | 3 | — |
| **Total** | **30** | |

## Order of operations

1. Block 0 (any time).
2. Block 1. If E-R1 passes, run Block 2. If E-R1 fails, skip Block 2.
3. Block 3 runs regardless: it is cheap and gives the fallback.
4. Block 4 for the winner.

**Do not:**
- build the 20-fund vintage ledger;
- re-estimate G-P2 Q22 models;
- download N-PORT holdings files;
- add new outcomes after seeing pilot counts.
