---
name: "deepen"
description: "Point it at any topic to build genuine mastery into a compounding knowledge base: weights experts by checkable track record, takes falsifiable self-tested stances, ships ranked tactics tuned to your context."
license: "MIT-0"
---

# /deepen — build genuine domain mastery into an accreting knowledge base

Point this skill at any topic (`/deepen PPC`, `/deepen sleep apnea`, `/deepen pickleball paddle physics`). It does not summarize a field — it *acquires expertise* in it: mines the real experts (past canon + current frontier), takes defensible, falsifiable stances where they disagree, **attacks its own conclusions before committing them**, and writes the result as evergreen notes that **compound across sessions**. Run it again on the same topic later and it deepens the existing knowledge base rather than starting over.

The method below is grounded in a verified research synthesis (Cooke's structured expert judgment, CFAR Double Crux, Matuschak evergreen notes, Anthropic orchestrator-worker). Where a step rests on practitioner convention rather than verified evidence, it says so — match that honesty in the output.

## Core principle (read first)
**Expertise is measured track record, not credentials.** Across 33 structured-judgment studies, <1/3 of credentialed experts were statistically accurate, and experts are *systematically overconfident* — their stated uncertainty is far too narrow. So: never rank a source by fame, title, or follower count. Rank it by demonstrated, checkable accuracy. And widen your own confidence intervals — the honest answer is less certain than it feels.

A competent literature summary tells you what people say. **Expertise tells you what's true, what's contested, what *you* judge correct, and what would change your mind.** The deliverable must do the latter.

> **Source authority ≠ source accuracy.** Some field guides rank sources by authority (official docs → standards → blogs). This skill explicitly does **not** — a high-authority source with a poor track record ranks below an independent one with checkable calls. Authority is a weak prior, never the ranking.

### How to actually weight a source when no Brier score exists (proxy ladder)
Most practitioner domains (SEM, PPC, materials design) publish no calibration record. Do **not** silently fall back to fame. Use this ranked proxy ladder and record which rung each source earned:
1. **Checkable past calls** — did their specific, dated public predictions/recommendations age well? (Strongest signal. Look for falsified-or-confirmed claims, not vibes.)
2. **Shows work** — do they cite data, name mechanisms, and reason transparently, vs. assert conclusions? Reproducible > authoritative.
3. **Calibration behavior** — do they state uncertainty, distinguish what they know from what they guess, and visibly update when wrong?
4. **Peer recognition by other high-track-record sources** — weak, and explicitly flagged as weak. Fame/followers/title alone is **rung zero — not evidence.**
A source can be famous and rank low. Say so when it happens — naming a loud-but-unsubstantiated consensus is part of the value.

## Knowledge base location & structure
Each topic gets a folder under your knowledge-base root: `<KB_ROOT>/<topic-kebab>/`. **`KB_ROOT` defaults to `./knowledge/`** (relative to where you invoke the skill); override it by setting the `DEEPEN_KB` environment variable, or point it at wherever your durable notes already live. If any of the knowledge base is sensitive, keep it out of public repos. Files:

- **`_map.md`** — the index / map-of-content. Topic scope, the depth-calibration dashboard (format below), last-updated date, mode of last run (light/deep), and links into every other note. Read this *first* on any re-run.
- **`principles.md`** — DURABLE first-principles knowledge. The timeless core: mechanisms, models, why-it-works. Atomic, densely cross-linked `[[notes]]`. **Each concept carries a `misconceptions:` line** — what practitioners commonly get wrong and why (see below). This is the part that must never rot. Slow to change.
- **`experts.md`** — the expert map. Canon (foundational) + frontier (current). Each entry: who, their actual track record / what they got right or wrong, the **proxy-ladder rung** that justifies the weight, and a credibility weight (high/med/low). Fame is not a reason.
- **`disagreements.md`** — live debates. One entry per contested question, each with: the **crux**, **my stance**, **calibrated confidence**, **the explicit falsifier** (what evidence would flip me), and a **survived-refutation** note (see step 4.5). This is the highest-value file — it's where judgment lives.
- **`tactics.md`** — the A+ execution playbook, **tuned to your context** (see step 6). Concrete, prioritized tactics ranked by leverage. Each tactic dated + decay-flagged (see Pillar 4).
- **`changelog.md`** — append one line per session: date + what was added/changed/**superseded** (see supersede rule). This is how accretion stays auditable.

Keep it lean. Atomic does not mean a hundred fragments — one idea per note, but no note that doesn't earn its place. Flag stale/duplicate content; supersede in place, don't append-and-bloat.

### Cite-or-flag (anti-hallucination, hard rule)
Every claim in `principles.md`, `experts.md`, and `disagreements.md` must **either cite a specific fetched source or be tagged `[inference]`** (your own reasoning) or `[convention]` (practitioner norm, not verified). No bare unsourced assertion is allowed to read as fact. If you can't source it and can't justify it as inference, it doesn't go in the KB. This is the difference between expertise and confident hallucination.

### Common misconceptions slot
For each core concept, record the **strongest wrong belief** people hold about it and why it's wrong. This is high-signal (it's where most field "advice" fails) and pairs with the proxy ladder — misconceptions are usually loud-but-unsubstantiated consensus. One line per misconception, sourced or `[inference]`.

### Depth-calibration dashboard (in `_map.md`)
Don't research everything to the same depth — set a **target depth per sub-area tied to your actual goal**, and stop when it's hit. This is both the map of what's solid and the run's stopping rule / cost control. Depth scale:

- **L1 Aware** — know it exists, can recognize it
- **L2 Familiar** — understand the basics, can discuss
- **L3 Competent** — know how to apply it
- **L4 Proficient** — know when/why, can optimize
- **L5 Expert** — deep model, can innovate / make novel calls

One row per sub-area:

| Sub-area | Target depth | Current depth | Confidence (H/M/L) | Last-verified | Thinness / what's missing |
|---|---|---|---|---|---|

Set targets from the goal (e.g. for PPC: bid strategy → L4, attribution → L2). A sub-area at or above target is **done** — don't over-mine it. Re-runs target the largest target-minus-current gaps first.

### Topic canonicalization (avoid fragmented KBs)
Before creating a folder, check whether the topic is an alias of an existing one (`PPC` / `paid-search` / `SEM` overlap heavily). Pick **one canonical kebab name**, and in `_map.md` list known aliases under an `aliases:` line so future runs route to the same KB instead of forking a parallel silo.

## Workflow when pointed at a topic

### 0. Orient & reconcile
- If `<KB_ROOT>/<topic>/` exists, read `_map.md` + `changelog.md` first — you are *deepening*, not restarting. Target the largest target-vs-current depth gaps from the dashboard.
- **Reconcile with existing knowledge.** Search your existing notes/repos for related material before building anything new — if you already keep notes touching this topic, read them, build on them, and cross-link. Never silo a parallel duplicate. If findings contradict an existing note, flag it for supersede, don't quietly fork.
- If it's new, canonicalize the topic name, create the folder and `_map.md` scaffold, and **set target depths per sub-area from your goal**.

### Effort tiering — pick the mode first
Scale cost to the topic's importance and the depth targets. State which mode you ran.
- **Light pass (default):** single agent, lean on existing knowledge + a handful of targeted searches. Produces/updates `_map.md`, a first-cut `principles.md`, and top tactics. Use for a fast map, low-stakes topic, or sub-areas whose target is only L1–L2.
- **Deep pass (on request, or when targets are L4–L5 or the dashboard shows a big gap):** full orchestrator-worker fan-out (steps 1–6) with the adversarial pass. Reserve large parallel-subagent research scale for genuinely hard, high-value topics — not every run.

### 1. Decompose (orchestrator)
Break the topic into 4–6 sub-questions spanning: foundational mechanisms, current best practice, the open controversies, and the execution surface. This mirrors the orchestrator-worker pattern (validated +90% over single-agent on breadth-first research). Map each sub-question to a dashboard sub-area + its target depth, so effort tracks the target.

### 2. Research fan-out (parallel subagents)
Spawn one research subagent per sub-question (use your runtime's subagent / task / deep-research harness for deep-pass topics). Each mines BOTH:
- **Canon** — the foundational texts/experts the field is built on.
- **Frontier** — who's actually pushing it *now* (recent, dated sources).

Do the empirical research *first*. Reserve "expert opinion" for genuinely frontier-of-the-unknowable questions where data runs out — that's the only place elicitation belongs.

> **Honesty note on "polling experts":** this skill synthesizes experts' *published record* — papers, talks, dated public calls. It does **not** interview live people, and it does **not** fabricate expert personas or invented credentials. If you frame a "what would expert X say" view, it must be grounded in that person's actual sourced positions. Frame outputs that way; don't imply primary elicitation that didn't happen.

### 3. Map & weight the experts → `experts.md`
For every significant source/expert, record demonstrated track record and assign a credibility weight using the **proxy ladder** above (record the rung). Explicitly separate genuine signal from popular-but-wrong consensus — note where the loud majority view lacks an empirical basis. Correct every confidence estimate for known expert overconfidence (assume intervals are too narrow).

### 4. Adjudicate disagreements → `disagreements.md`
For each live disagreement, run an adapted **Double Crux** procedure:
1. State the disagreement concretely.
2. Operationalize it — what specific, testable thing do the sides actually differ on?
3. Find the **crux**: the load-bearing belief B such that if B were false, the conclusion flips. Find a *double crux* where possible (one statement decisive for both sides).
4. **Take a stance.** State your position, calibrated confidence (high/med/low + *why*), and the **explicit falsifier** — the evidence that would change your mind. Refusing to take a position is a failure of this skill; a wrong-but-falsifiable stance is recoverable, a mushy "both sides have merit" is not.
5. Be **method-pluralistic** on aggregation — there is no proven single-best way to combine conflicting experts, so don't pretend one rule settles it. Hold weightings humbly.

> **Adaptation note:** Double Crux is a *two-person* technique for people who disagree with each other. Here a single agent adjudicates *other people's* disagreement — a legitimate adaptation, but not the textbook method. Don't present it as live dialectic.

### 4.5. Stress-test before committing (red-team + validation gates)
Before any stance is written to `disagreements.md`, and before a `principles.md` note is treated as solid, put it through three gates:
- **Adversarial self-falsification.** For each stance, spawn (or role-play, on a light pass) a **skeptic whose only job is to refute it** using the strongest available counter-evidence. Survives strong refutation → keep, note "survived: <best counter-argument and why it failed>." Survives only weakly → **downgrade confidence** and say why. Skeptic wins → flip or retract.
- **Teach-back.** Can the claim be explained simply, from mechanism, without jargon hand-waving? If it can't be explained, it isn't understood — mark it thin.
- **Prediction.** Does the model correctly predict a *known* outcome in the domain (a documented case, benchmark, or historical result)? A model that can't retrodict a known result is not yet expertise — flag the gap.
A stance/principle that passes all three is earned; one that was never tested is not.

### 5. Knowledge-base write (evergreen notes)
Write durable findings into `principles.md` as **atomic** (one idea), **concept-oriented** (organized by idea, not by source), **densely-linked** notes built to evolve and accrete — each with its `misconceptions:` line and cite-or-flag tags. Update the `_map.md` depth-calibration dashboard (bump current depth, confidence, last-verified). Append to `changelog.md`.

**Supersede rule (re-runs):** when new evidence contradicts an existing note, *replace the claim in place* and log it in `changelog.md` as `superseded: <old> → <new> (why)`. Never leave two conflicting claims live, and never silently delete the old one without a changelog trace. The KB must not accrete contradictions.

### 6. Translate to execution → `tactics.md` (context-tuned)
Convert strategy into a prioritized A+ tactic playbook **applied to your actual context** — pull the relevant specifics of your product, market, constraints, or personal situation so tactics are concrete to your case, not generic field advice. Rank by leverage using **ICE** (Impact × Confidence × Ease) or **RICE** (Reach × Impact × Confidence ÷ Effort) — *convention, not verified evidence; use as a forcing function for prioritization, not a precise score.* Each tactic: concrete action, expected leverage, effort, and the metric that proves it worked. Top tactics first.

## Pillar 4 — staying current without rotting the core (convention)
Split knowledge by decay rate:
- **Durable** (`principles.md`) — mechanisms, first principles. Rarely changes. No decay flag.
- **Fast-moving** (`tactics.md` + platform-specific notes) — algorithm changes, platform rules, current benchmarks. Each such note carries a **`last-verified: YYYY-MM-DD`** line and a decay flag (e.g. `decays: fast` for ad-platform mechanics, `decays: slow` for buyer psychology). On any re-run, re-verify anything `decays: fast` older than ~90 days before relying on it; refresh the tactical note without touching the durable core. This keeps fresh tactics from corrupting timeless knowledge.

## Output to the user (every run)
A tight brief, not a document dump:
1. **What I now know** — the 3–5 load-bearing truths, with confidence.
2. **Where I took a stance** — each contested call, my position, what would flip it, and whether it survived refutation.
3. **A+ tactics** — the ranked playbook, top items first, applied to *your* context.
4. **Thin spots** — sub-areas still below target depth, what's weak/unverified, worth a deeper pass.
5. Mode run (light/deep) + KB path so it's findable.

Lead with the point. Numbers over adjectives. State confidence out loud and flag thin evidence — don't launder convention as proof.

## Guardrails
- The knowledge base is yours. Keep sensitive specifics out of any repo you publish.
- This skill produces *theses and tactics*, never actions. It does not send, post, publish, or take irreversible steps on your behalf.
- Apply findings to your real context, but keep the method domain-agnostic.
- Distinguish verified findings from practitioner convention in the output (cite-or-flag). Honesty about evidence strength is part of the deliverable.
- Never fabricate experts, credentials, sources, or quotes. Synthesize the real published record only.
