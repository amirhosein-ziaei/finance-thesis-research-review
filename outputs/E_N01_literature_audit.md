# E-N01 literature audit: mutual fund expense waivers and adviser recoupment

Date: 9 October 2026. Evidence cutoff: material retrievable on 9 October 2026.
Companion files: `source_register.csv` (IDs such as E01 and D02 are used below), `critique_of_previous_claude.md`, `E_N01_redesigns.md`.

**Bottom line.**
1. No paper studies **recoupable versus non-recoupable** expense waivers, and none measures actual adviser recoupment at scale. The novelty claim survives a broader search than the earlier one.
2. The **original expiry-timing question is unidentifiable**. The earlier Phase 3 work showed this correctly; I agree with that part.
3. The narrowed "ledger reconciliation and incidence" thesis is real, but it rests on six hand-picked funds and amounts of tens of thousands of dollars. On its own it is not an important Finance contribution.
4. What changes the assessment is **data the earlier work missed**. Since 2018, SEC **Form N-CEN Item C.8** reports, for every registered fund-year:
   - whether an expense limitation existed;
   - whether expenses were waived;
   - whether the waived fees are **subject to recoupment**;
   - whether previously waived expenses were **actually recouped**.

   The SEC publishes these fields as structured quarterly data sets (D01, D02).
5. With N-CEN, E-N01 can become a universe-level study of **contingent fee subsidies**. Without it, the project should stop.

---

## 1. Audit of the E-N01 research materials

### 1.1 What I read

| Document | Source | Read? |
| - | - | - |
| `Final thesis adjudication October 2026.md` | ZIP (`00_Original_Adjudication`) | Yes, in full (384 lines) |
| `phase3_summary.md`, `phase3_go_no_go.md` | ZIP | Yes |
| `remaining_measurement_problems.md` | **Missing from the ZIP**. Read from the original E-N01 repository branch `claude/hopeful-fermi-3mg764` (`amirhosein-ziaei/fund-fee-recoupment-thesis`), which became accessible in this session | Yes |
| `strict_accounting_ledger.csv`, `conditional_accounting_ledger.csv` | **Missing from the ZIP**. Present on the same branch (27 strict and 32 conditional rows) | Structure and first rows inspected; not re-derived |
| Other branch files (`source_observations.csv`, `zero_derivations.csv`, `schedule_basis.csv`, manifests, `src/`, `tests/`) | Same branch | Listed. Selected files searched (e.g., for N-CEN, XBRL, money market) |
| Primary fund reports (Towpath, Counterpoint, Al Frank, Western Asset) | Git-ignored `data/raw/` on the original machine. **Not in the repository** | **Not inspected by me.** I cannot independently verify any dollar figure |

**Verification statement.** I have **not** independently verified the E-N01 empirical results: the recoveries, balances, lapses and bps incidence. Doing so would require opening the source N-CSR documents. The numbers below are the earlier project's, labeled as such.

### 1.2 Exact original research question

> "Do registered-fund advisers recoup previously waived expenses near contractual expiry, and does this delay the benefit of lower operating costs reaching shareholders?" (adjudication, candidate table)

`docs/research_scope.md` splits it into:
- an **incidence** component (recovery in bps of average net assets; an accounting counterfactual);
- a **timing** component (recovery fraction in a vintage's final eligible interval).

### 1.3 What evidence was actually obtained (as reported, not re-verified)

- 16 primary financial reports; 291 single-coder source observations; 6 funds; 4 advisers (Oelschlager/Towpath, Counterpoint, Kovitz/Al Frank, Franklin Templeton/Western Asset).
- Positive recoupment at **2 funds**:
  - Towpath Focus: $25,501 in FY2023, about 9 bps.
  - Counterpoint Tactical Equity: $118,758 in FY2024 (about 10.9 bps), then $65,408 in the six months to March 2025.
- **One explicit forgiveness**: Towpath Focus, FY2024. The adviser "voluntarily forwent" the recoupment and reversed a $20,583 semiannual accrual.
- **Strict ledger: 0 of 27 intervals fully reconciled.** 7 close with undisclosed flows netting to zero; 3 close only if a vintage lapsed at expiry; 17 are incomplete.
- Schedule formats differ. Towpath lists *original* vintage amounts, so remaining balances and the vintage source of recoveries are undisclosed.
- **Recoveries track cap headroom.** Every vintage's age equals its time to expiry, so a deadline effect cannot be separated from age, growth and headroom (Phase 3 §2-G).

### 1.4 Which conclusions are supported, and which are overstated

| Conclusion in the earlier documents | My assessment |
| - | - |
| Actual recoveries can be separated from eligible balances in annual reports | **Supported** for the cases read (explicit expense lines or zero by arithmetic). Valid only for the selected sample |
| The expiry-timing question cannot be identified ("age = time-to-expiry"; headroom drives recovery) | **Supported**, and it follows from contract structure, not just from small N. I agree the timing component should be dropped as a causal question |
| "GO for a narrowed thesis: adviser fee-recovery accounting and shareholder incidence" | **Overstated as a research contribution.** It is feasible, but nothing shows the narrowed question matters economically. The bps figures come from two selected small funds. Prevalence, aggregate magnitude and the share of funds with recoupment rights were never measured. A cheap universe measure existed (N-CEN C.8) and was not used |
| "No kill condition for the whole project is triggered" | **Partly overstated.** The gate "expansion would consume most of the horizon" passed only "provisionally" and without measured coding time (Phase 3 itself admits this) |
| Novelty "CLEARLY DISTINCT AFTER SEARCH" (adjudication) | **Directionally right** (no direct competitor found), but the competitor matrix was mis-specified. It listed Evans–Fahlenbrach, Scheld et al. and Berk–Green as "direct", which they are not. It missed closer work: E03–E06, E10, E12, E18, and Christoffersen's explicit "option value of waiving" passage |
| "The indispensable observations are manually extracted fields, not a ready-made SEC numeric table" (adjudication, data section) | **Incorrect for the incidence question.** N-CEN C.8 is a ready-made SEC table for recoupment *incidence* (yes/no). Prospectus risk/return XBRL data carry class-level waiver magnitudes. Manual extraction is needed only for *amounts* and *balances* |

### 1.5 Files still missing or unverifiable

- Raw primary documents behind the ledgers (git-ignored). The adviser PDFs cited in the adjudication can be re-downloaded; I did not do so.
- No second human coder. All 291 observations remain "partially verified" (by the project's own admission).

---

## 2. Search method and its limits

- **Tools.** Web search (standard and extended modes); the Crossref API for bibliographic verification (all journal metadata in the register is Crossref-checked unless stated otherwise); publisher and author pages; direct PDF retrieval where legal.
- **Blocked or limited.**
  - SSRN abstract pages returned HTTP 403.
  - OpenAlex and Semantic Scholar APIs returned HTTP 429 (rate-limited), so no citation-network crawl was possible.
  - Some publisher pages redirect to authentication.
  - Consequence: the search is **systematic across query families but not exhaustive**. A recent unpublished SSRN paper on recoupment could exist and not be found.
- **Query families used.**
  - fee waiver / expense reimbursement / expense cap / expense limitation agreement;
  - recoupment / recapture / clawback of waived fees;
  - waivers + flows / performance / salience;
  - money-market waivers + ZLB + recapture;
  - economies of scale / breakpoints / pass-through;
  - N-CEN in academic research;
  - "temporary waivers" / raise fees after waiver expires.
- **Verification labels** (register column `verification_status`):
  - VERIFIED-FULLTEXT: I read the paper's relevant sections.
  - VERIFIED-ABSTRACT: publisher, author or index abstract.
  - VERIFIED-METADATA: Crossref only. Content is from background knowledge (BK) and is flagged as such.
  - SECONDARY-ONLY: a search snippet or secondary listing.

---

## 3. Closest literature, organized by what it already answers

### 3.1 Waivers as flexible pricing: the conceptual ancestor

**Christoffersen (2001, JF), "Why Do Money Fund Managers Voluntarily Waive Their Fees?"** [E01; manuscript full text read]
- Data: Lipper money-fund data 1990–95 and IBC Donoghue quarterly waivers 1993–94.
- More than half of money funds waive fees they are contractually entitled to.
- Retail managers adjust net fees to realized performance and expected flows, so waivers act as a quasi performance-based fee under a nominally flat contract.
- Section C, "The Option Value of Waiving", says high contracted fees with waiving make sense "if funds believe they can recapture higher fees later". It adds that "more research on the option value of waiving is necessary".
- **This is the clearest statement in the literature that the recapture motive is open.** Her setting is voluntary money-fund waivers, not contractual recoupment rights.

Related items:
- Christoffersen's dissertation (1998) and Wharton working paper 97-46 [E02] belong to the same research program. The dissertation is inaccessible (ProQuest preview only). It should be obtained through a library because it may cover non-money funds.
- **Farinella and Jorgensen (2002, JEF)** [E04, snippet level]: waivers keep tax-exempt money-fund yields competitive.
- **Christoffersen and Musto (2002, RFS)** [E03, metadata; content BK]: fees track investor performance-sensitivity. This matters for E-R2: advisers may recoup where investors are inattentive.

### 3.2 Waivers as sponsor subsidies at the zero lower bound

- **Di Maggio and Kacperczyk (2017, JFE)** [E05, abstract level]: at the ZLB, money funds took more risk, exited more and **reduced fees**. The authors treat the reductions as sponsor subsidies and value them.
- Industry sources document that recoupable money-fund waivers existed. Prospectuses from Huntington, Schwab and HighMark had three-year recapture windows (Crane Data 2011) [D06].
- In November 2015, just before Fed liftoff, **Schwab and Vanguard renounced recapture** [D07]. A 2011 press item put Schwab's potentially recoverable amount at $878.2 million (secondary; unverified).
- ICI reports money-fund waivers falling from $8.4bn (2021) to $1.5bn (2024) [D08].
- Answered: money-fund waivers are subsidies, and large sponsors forgave recapture rights. Not studied academically: forgiveness versus exercise.

### 3.3 Waivers as strategic pricing in long-term funds: the most recent competitor

**Black and Kölbel (10 Dec 2024), "The Puzzle of ESG Fund Fees"** [E06; full text read]
- Data: CRSP, Q1 2011–Q2 2024, plus the **SEC Mutual Fund Prospectus Risk/Return data** for gross fees and waivers (about 364,000 fund-quarter observations: 355,873 non-ESG and 8,000 ESG).
- U.S. ESG funds charge 9.5–12.7 bp lower net expense ratios, driven by more frequent and larger waivers. Cross-selling is the favoured explanation.
- **Directly relevant test:** funds that discontinue waivers show no higher subsequent fee changes at t+4 and t+8, so they find no "waive now, raise later" pattern.
- Not studied: recoupment rights, actual recoupment, N-CEN, or the difference between recoupable and non-recoupable subsidies.
- **Threat.** A referee will cite this paper to say "waivers do not lead to later fee increases". E-R1 must answer it. Recoupment raises *net* fees without discontinuing the waiver line, through the *recovery* line, so a "waiver discontinued" test like theirs may not capture it.

### 3.4 Fee competition, pass-through and scale economies

| Paper | What it establishes | Connection |
| - | - | - |
| Wahal and Wang (2011, JFE) [E07] | Entry by overlapping funds cuts incumbents' management fees while distribution fees rise. Pass-through to investors is incomplete | The general "lower costs need not reach investors" claim is owned. Not about waivers |
| Deli (2002, JF) [E10]; Freeman and Brown (2001) [E19] | Advisory contracts pass scale economies through partly (breakpoints), more in administrative than advisory fees (secondary summaries) | E-R1 asks whether **recoupment rights delay** scale pass-through for small, growing funds. That margin is not studied |
| Gil-Bazo and Ruiz-Verdú (2009, JF) [E13]; Cooper, Halling and Yang (2021, RoF) [E14]; Khorana, Servaes and Tufano (2009, RFS) [E16] | Strategic fee setting, persistent dispersion, scale and investor-protection determinants (BK) | Background |
| Berk and Green (2004, JPE) [E17] | Theory of rents and scale | Background, not empirical competition |

### 3.5 Investor attention, shrouding and incentive-fee law

- **Barber, Odean and Zheng (2005, JB)** [E12]: flows respond little to operating expenses. That makes a contingent future fee such as recoupment a plausibly shrouded cost.
- **Gabaix and Laibson (2006, QJE)** [E18]: shrouded add-on prices survive competition.
- **Elton, Gruber and Blake (2003, JF)** [E11] study incentive fees. Advisers Act §205(b)(2) allows registered-fund performance fees only in symmetric "fulcrum" form [D09, secondary]. This underpins E-R2: discretionary recoupment after good outcomes, plus forgiveness after bad ones, could act as an asymmetric performance fee. **No paper tests this.**

### 3.6 Fund launch and incubation

- **Evans (2010, JF)** [E15]: families incubate funds and publicize the survivors (BK). Expense caps for new funds are the fee side of launch strategy.
- Whether recoupment rights shift launch costs onto later shareholders is not studied.

### 3.7 Recent academic use of N-CEN

- **Chen, Tran and Wang (2024 WP)** [E21] use N-CEN and N-PORT to study securities-lending revenue splits.
- So N-CEN fund-level fields are accepted in current academic work. No paper using N-CEN **Item C.8** was found.

### 3.8 Papers the previous adjudication called "direct competitors"

- Evans and Fahlenbrach (2012) [E08] and Scheld, Stolper, Fernandes and Heyden (2026, *Financial Management*, "Affiliated Mutual Funds: Beyond the Reach of the Invisible Hand?") [E09; title and date Crossref-verified, content not re-read].
- They are governance and distribution papers. They are **not** competitors on waivers or recoupment.
- They are reasonable examples of what a publishable fee/contracting paper looks like.

---

## 4. What is answered and what remains open

| Question | Status | Key sources |
| - | - | - |
| Do managers waive fees strategically, in response to performance or flows? | **Answered** for money funds (1990s) | E01, E04 |
| Do waivers explain cross-sectional net-fee gaps (e.g., ESG)? | **Answered** (2011–2024) | E06 |
| Do funds raise fees after discontinuing waivers? | **Partly answered: no average effect** (ESG versus non-ESG comparison) | E06 |
| Do sponsors subsidize money funds at the ZLB? | **Answered** | E05, D08 |
| Is fee pass-through from competition or scale incomplete? | **Answered** in general | E07, E10, E19 |
| How prevalent are *recoupable* waivers, and how often are they exercised, in the fund universe? | **Open.** No paper found. N-CEN C.8 measures it | D01, D02 |
| Do recoupment rights delay the decline in net fees as funds grow (scale pass-through)? | **Open** | — |
| When recoupment is contractually feasible, do advisers exercise it or forgo it, and does performance or competition predict which? | **Open.** Only anecdotes: Towpath FY2024; Schwab and Vanguard 2015 | D07 |
| Do investors respond to recoupable waivers as they respond to permanent fee cuts? | **Open but hard to identify** | E12, E18 |
| Do advisers time recoupment to vintage expiry? | **Open but not identifiable** with public data (age = time-to-expiry; headroom confound) | Phase 3 |

---

## 5. What public SEC data can and cannot identify

| Object | N-CEN C.8 (2018–) | Prospectus risk/return XBRL (2011–) | N-PORT (2019–) | N-CSR notes (hand) |
| - | - | - | - | - |
| ELA exists / any waiver in year | **Yes** (C.8.a, C.8.b) | Waiver line present (class) | — | Yes |
| Waived fees *subject to recoupment* | **Yes** (C.8.c, yes/no) | Footnote text (to be parsed) | — | Yes |
| Recoupment *exercised* in year | **Yes** (C.8.d, yes/no) | Possibly as negative waiver ("…or (Recovery)") — **to verify** | — | Yes, amount |
| Recoupment **amount** ($, bps) | No | Possibly (bps, prior fiscal year) — to verify | — | **Yes** |
| Remaining eligible **balance** | No | No | — | Yes, if remaining-balance format |
| **Vintage**, expiry, forgiveness | No | No | — | Sometimes; often undisclosed (Phase 3) |
| Gross vs net expense ratio, cap level | — | **Yes** (class) | — | Yes |
| Size, flows, returns | Average net assets (C.19) | — | **Yes**: monthly net assets, flows, class returns | Yes |
| Adviser identity | **Yes** (adviser table, C.9) | Via series | Via series | Yes |

**Implications.**
1. *Actual recovery* incidence is measurable at universe scale (C.8.d). Amounts need prospectus XBRL (if recoveries are tagged) or hand collection from a stratified subsample.
2. *Balances, vintages, expired versus forgiven rights* stay hand-collected and partial. Any design that **requires** vintage-level reconstruction for most funds should be **rejected**. Phase 3 showed the original-amount schedule format makes it impossible.
3. **Data-quality risks.**
   - SEC staff comment letters show N-CEN C.8 misreporting [D05]: Impact Shares Trust I reported no ELA despite waivers.
   - Another registrant read C.8.b as asking only about contractual waivers.
   - Any study must validate C.8 against N-CSR for a random subsample.

---

## 6. Answer to the main question

> *Can E-N01 become a serious and novel empirical Finance paper rather than a descriptive accounting exercise?*

**Conditionally yes, but not in either of its current forms.**
- The original expiry-timing question fails on identification.
- The narrowed six-fund ledger fails on economic importance and scale.

**What survives is a question about contingent fee subsidies.** Advisers who cap expenses can make the subsidy a *contingent loan*, repaid by later shareholders if the fund grows. Who repays, how often, and does this delay the pass-through of scale economies? The question is:
- novel: no paper on recoupable versus non-recoupable waivers was found, and Christoffersen explicitly flags the recapture motive as open;
- measurable at universe scale (N-CEN C.8, prospectus XBRL, N-PORT);
- tied to an established literature on fee pass-through, shrouding and incentive-fee regulation.

**It is still largely descriptive and associational.** Its importance depends on a fact nobody has measured: how prevalent and material recoupment is. That fact can be obtained cheaply. If N-CEN shows recoupment is exercised in very few fund-years, or only by a handful of series trusts, the contribution disappears and E-N01 should stop. See `E_N01_redesigns.md` and `next_30_hours.md`.
