# /deepen — Eval: skill-ON vs skill-OFF

**Date:** 2026-06-17
**Question:** Does running `/deepen` (the master/autoresearch skill) produce materially better research output than a strong baseline agent with no skill?
**Design:** Same prompt, two arms — **OFF** (baseline agent, no skill) and **ON** (`/deepen` deep pass: orchestrator + multi-way research fan-out + adversarial refutation gate). EVAL runs wrote no KB files; the replies *were* the content. Compared head-to-head.

## Headline finding

**The skill did not change the answers. It changed how defensible they are.** Both arms independently converged on the same load-bearing conclusions for every topic. The skill's value is process, not verdict: falsifiable stances, active self-refutation, track-record-weighted experts, calibrated confidence, cite-or-flag — plus a compounding KB artifact. Baseline is the better one-off *deliverable* (faster, tighter, leads with the point); the skill earns its ~2–3× cost when the output will be built on or staked on a decision.

## Pairs

### Standing desks — COMPLETE
- **Convergence (both arms):** ~0.15 kcal/min extra standing (trivial); no CVD benefit from standing; 2024 UK Biobank (n=83,013, device-measured) is the decisive evidence; over-standing carries its own orthostatic risk; productivity net-neutral; real lever is breaking up stationary time with movement.
- **ON added:** explicit falsifiers + "survived refutation" on each stance (re-searched for strongest counter-evidence — e.g. Bodker 2021 vascular pilot — and reported why it loses on n/design); expert track-record ladder anchored on Cochrane's own "low-quality evidence" honesty.

### Spaced repetition — COMPLETE
- **Convergence (both arms):** spacing is among the best-replicated findings in learning science *for discrete retrievable items*, but NOT universal — degrades on conceptual/transfer/complex material; optimal gap scales with retention horizon (~10–20%); real-world limiter is adherence + card quality, not the algorithm (SM-2 vs FSRS is a rounding error).
- **ON added:** named the loud-but-overclaimed consensus ("works for basically everything") as a red flag; downgraded an overreaching expert (van Gog & Sweller) for a failed strong empirical claim while keeping their valid mechanism; calibrated confidence per claim.

### Pomodoro — PENDING
- OFF baseline complete: principles well-supported but the specific 25/5 protocol has thin/mixed direct evidence; Biwer 2023 (BJEP) found Pomodoro breaks raised fatigue/dropped motivation *faster* than self-regulated breaks with no productivity difference; value is behavioral scaffolding, not a neural cycle; 25 min is arbitrary.
- ON twin: **in flight as of filing (2026-06-17).** Append result here to close the third pair.

## Verdict

1. **Skill works as designed** — the adversarial gate and cite-or-flag discipline are real and visible in output; no fabricated experts or citations observed.
2. **It doesn't find a better truth on well-trodden topics** — convergence with baseline suggests the marginal answer-quality gain is small where the literature is mature. Expect larger separation on contested/frontier topics where baseline would hedge or overclaim.
3. **Its durable value is the KB that compounds** (`knowledge/<topic>/`) and the auditability of *how* each stance was reached — not prose readability.

**Recommendation:** For "just tell me," baseline wins on signal-per-second. For anything decision-grade or that you'll build on, run `/deepen`. The skill's killer feature is the refute-before-committing gate, which is exactly what baseline lacks.

## Open
- Append Pomodoro ON result and finalize the third-pair comparison.
- Consider a contested/frontier topic as a 4th pair to test where ON should separate most from OFF.

---

## Addendum — consensus-buster upgrade (2026-06-19)

**Brian's critique (correct):** an LLM regresses to the *volume-weighted consensus*; the best answer is often seldom-written/tacit/closely-held and outperforms. So "answers don't change, evidence grows" was a weak result — and partly an **artifact of the test topics** (standing desks, spaced repetition = settled-science, consensus-is-right). The skill's real job is to **beat consensus where it's beatable**.

**Upgrade applied** to both `/deepen` and `/master`: (1) a "beat the consensus" core principle (volume ≠ evidence; divergence is the deliverable; honest corpus ceiling); (2) a **§3.5 consensus-buster** step (name the modal answer → hunt highest-track-record dissent + seldom-written frontier → adversarially test if the challenger wins); (3) a **tacit-frontier** note (mine the rawest primary record; name what's unwritten; hand off to /apply + the operator's own data).

**Re-run pending on a CONTESTED topic — Amazon PPC** (consensus advice there is genuinely mediocre; operator alpha is real). Success criterion shifts from "more defensible" to **"did it diverge from consensus toward a better, defensible answer?"** — i.e. did the consensus-buster produce ≥1 load-bearing call a vanilla-consensus answer would *not*, that survives the refutation gate.
