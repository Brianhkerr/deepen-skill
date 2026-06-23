# /deepen

**An Agent Skill that builds genuine, 10,000-hour expertise in any topic — and compounds it across sessions.**

Most "research" tools — Deep Research, generic "be an expert in X" prompts, RAG chatbots — *summarize a field once and hand you prose*. `/deepen` doesn't. Point it at a topic and it **acquires defensible expertise**: it weights sources by **checkable track record** (not fame), takes **falsifiable stances** on the open controversies, **attacks its own conclusions before committing them**, and writes the result as an evergreen knowledge base — a corpus, a synthesis, and a proven playbook — that gets deeper *every time you run it*.

```
/deepen PPC
/deepen sleep apnea
/deepen pickleball paddle physics
```

Works anywhere the [Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) open standard is supported — Claude Code, Claude.ai, the Claude API, and compatible runtimes. Output is plain Markdown with `[[wikilinks]]` and YAML front-matter, so the knowledge base drops straight into an **Obsidian vault** (or any Markdown notes system) and graphs natively.

---

## Who it's for

**Built first for people who build with AI.** If you use Claude Code, Claude.ai, or your own agents, `/deepen` gives you what a chat answer can't: a knowledge base **engineered for an LLM to load and reason over** — front-matter metadata, a one-context index, self-contained chunked notes, a glossary as retrieval bridge. It's drop-in context / RAG substrate for your own agents that gets sharper every run, not a transcript you scroll back through.

It pays off just as well if you're:
- **An operator, researcher, or analyst** staking a decision on the answer — you get cited, falsifiable positions *and the exact evidence that would flip each*, not hedged "experts disagree" summaries.
- **A second-brain / Obsidian user** — evergreen notes with `[[wikilinks]]` and YAML front-matter that graph natively in your vault and **compound** instead of evaporating in chat history.
- **Anyone serious about mastering a field** — it builds toward the depth of someone with 10,000 hours in it, and deepens every time you come back.

Just want one fast report you'll never revisit? Use Deep Research — and here's [why that's a different job](#why-it-matters).

## Why it matters

You get **decision-grade expertise that compounds into an asset you own** — cited, stress-tested positions, written as a knowledge base your future self *and your agents* can load, instead of prose you read once and lose. The more you run it on a topic, the sharper that asset gets.

Deep Research and friends are excellent at one job: producing a **single, well-cited report on demand**. That's also their ceiling. `/deepen` is built for a different job — *accumulating mastery you keep* — and differs on five axes that matter when you'll actually build on the answer:

| | Deep Research / one-shot tools | `/deepen` |
|---|---|---|
| **Output** | A prose report you read once and lose in chat history | A **structured knowledge base on disk** (corpus → synthesis → playbook) you own, query, and re-load |
| **Memory** | Stateless — every run starts from zero | **Compounds** — re-running deepens the *same* KB, with a changelog and supersede rules; an auditable accretion |
| **Source weighting** | Ranks by authority/recency/relevance (a famous bad-call source still ranks high) | Ranks by **checkable track record** via an explicit proxy ladder — fame is rung zero |
| **Stance** | Hedges: "experts disagree / both sides have merit" | **Takes a falsifiable position** with calibrated confidence *and the exact evidence that would flip it* |
| **Verification** | Cites sources, but doesn't try to *break* its own claims | **Red-teams every stance** with an adversarial skeptic (re-searching external counter-evidence) before it's written — intrinsic self-correction is known to be unreliable, so it uses an independent refuter |
| **Built for** | A human to read | **A future LLM to load and reason over** — one-context index, front-matter metadata, self-contained chunked notes, a glossary as retrieval bridge |

The one-liner: **a literature summary tells you what people *say*. `/deepen` tells you what's *true*, what's *contested*, what to *do*, what *goes wrong*, and where the field is *moving* — and keeps a defensible trail of how it decided.**

> It is *not* a replacement for Deep Research when you genuinely want one fast report. It's what you run when the topic is worth mastering, the answer will be staked on a decision, or you want expertise that gets sharper every month instead of evaporating after one query.

## The three layers (what makes it a compendium, not a summary)

Every KB is built in three layers plus a discoverability spine — never collapsed together:

1. **Corpus** — high-fidelity digests of the actual sources (each linked back). The recall layer: verdicts stay auditable and future runs dig deeper without re-scraping.
2. **Synthesis** — principles, the expert map, and reconciled disagreements, all citing *into* the corpus. Where judgment lives.
3. **Mastery** — the domain-general playbook, failure modes, benchmarks, and worked cases. The proof-filtered long tail an operator runs on.

The corpus is high-recall (capture the material); the mastery layer is proof-filtered (only what survives the adversarial gate). Keeping them as separate files is how `/deepen` holds both "preserve everything" and "trust only what's earned" without contradiction.

## Grounded in real method, not vibes

The workflow is built on a verified research synthesis:

- **Cooke's Classical Model / structured expert judgment** (Colson & Cooke 2018) — weight experts by demonstrated accuracy; across 33 studies, <1/3 of credentialed experts were statistically accurate.
- **Systematic overconfidence** (Morgan 2014, PNAS) — experts' stated uncertainty is consistently too narrow, so confidence intervals get widened on purpose.
- **CFAR Double Crux** — a procedure for finding the load-bearing belief under a disagreement and taking a falsifiable position.
- **Andy Matuschak's evergreen notes** — atomic, concept-oriented, densely-linked notes designed to accrete.
- **Anthropic's orchestrator-worker pattern** — decompose, fan out parallel researchers across distinct source pools, synthesize (~+90% over single-agent on breadth-first research).

It's also tuned to the AI-research evidence on **retrieval** (hybrid/semantic search beats one index), **context engineering** (progressive disclosure, self-contained chunks), the **limits of intrinsic self-correction** (use an external refuter, not "let me reconsider"), and **LLM-judge bias** (randomize order; keep the final judge on a frontier model). Where a step rests on practitioner convention rather than verified evidence (e.g. ICE/RICE ranking), the skill says so — and so does its output.

## What it produces

A folder per topic under your knowledge-base root (`./knowledge/<topic>/` by default, or set `DEEPEN_KB` — point it at an Obsidian vault and it just works). Files scale to the domain; thin topics collapse slots, deep ones split them:

```
knowledge/ppc/
  _index.md          # the loadable map: scope, depth dashboard, and a "to do X, read these files" router — fits one context window
  sources/           # the corpus — one high-fidelity digest per source, each linked back
  principles.md      # durable first-principles, each with a "common misconceptions" line + cite-or-flag tags
  experts.md         # the expert map, weighted by track-record proxy ladder (links into sources/)
  disagreements.md   # live debates: crux · stance · confidence · falsifier · survived-refutation (claim-IDs)
  playbook.md        # the proof-filtered, domain-general execution playbook + diagnostic decision trees
  failure-modes.md   # anti-patterns and expensive mistakes — the errors experts are defined by NOT making
  benchmarks.md      # the reference numbers an expert carries in their head (decay-flagged)
  frontier.md        # open unknowns + where the field is moving — also the loop's fuel
  glossary.md        # ontology + jargon map, doubling as a retrieval bridge
  cases.md           # canonical worked examples with numbers and outcomes
  changelog.md       # one line per run — accretion stays auditable
```

Every run ends with a tight brief: what I now know (with confidence), where I took a stance (and what would flip it), the mastery added this pass, and the frontier still worth a deeper pass.

## See a real run

[`examples/deliberate-practice/`](examples/deliberate-practice/) is a genuine `/deepen` run, committed verbatim — real citations, falsifiable stances on a live expert disagreement (Ericsson vs. the Macnamara/Hambrick meta-analyses), and one debate deliberately held at LOW confidence and flagged as thin. Start with [`disagreements.md`](examples/deliberate-practice/disagreements.md).

> The example predates the current (v2) file schema — it shows the core method under the earlier `_map.md` / `tactics.md` layout. The skill now expands the file set (`_index.md`, `sources/`, `playbook.md`, `failure-modes.md`, `benchmarks.md`, `frontier.md`, `glossary.md`, `cases.md`); the *method* it demonstrates is unchanged.

## Quickstart

1. **Install it** — one line below (Claude Code, ClawHub, Claude.ai, or API).
2. **Run it** — `/deepen <topic>`, e.g. `/deepen sleep apnea`.
3. **Find your KB** — in `./knowledge/<topic>/` (or wherever you set `DEEPEN_KB`). Re-run any time to deepen it.

No API keys or extra tools required — a web-search-capable agent is enough. Everything below is just detail.

## Install

A skill is just a folder with a `SKILL.md` (plus an optional `CONNECTORS.md`). Any Agent Skills runtime picks it up once it's in the right place.

**Claude Code** — copy the folder into a skills directory:

```bash
git clone https://github.com/Brianhkerr/deepen-skill.git
cp -r deepen-skill/skills/deepen ~/.claude/skills/deepen      # personal — all projects
# or:  cp -r deepen-skill/skills/deepen .claude/skills/deepen  # this repo only — shareable with a team
```

**ClawHub** (OpenClaw and compatible agents):

```bash
clawhub install deepen
```

**Claude.ai / Claude API** — `/deepen` is a standard Agent Skill, so add it as a custom Skill the way your surface supports: upload the `skills/deepen` folder in Claude.ai's Skill settings, or register it through the Claude API / Agent SDK. Anthropic's [Agent Skills guide](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) has the current path for each.

After installing, start a fresh session and type `/deepen` — if it autocompletes or responds, it's loaded.

## Requirements

**None beyond a capable agent with web search.** `/deepen` runs on any Agent Skills–compatible runtime — Claude Code, Claude.ai, the Claude API, or a compatible agent. A web search + fetch tool is the only hard dependency; everything else is optional and purely additive:

- **Parallel subagents + model tiering** (e.g. Claude Code's sub-agents) — used for the deep-pass orchestrator-worker fan-out *if your runtime has them*; if it's single-agent, the skill runs the same structure sequentially. Either way it works.
- **Extra research pools** — academic APIs (arXiv, Semantic Scholar, PubMed), Reddit/HN, `yt-dlp` for talks/podcasts, and semantic-search keys (Exa/Tavily/Brave). Each non-overlapping index widens recall. Copy-paste recipes are bundled in [`skills/deepen/CONNECTORS.md`](skills/deepen/CONNECTORS.md) — the keyless ones need no signup.

The skill **never blocks because a pool or feature is missing** — it uses what your runtime has and notes in the KB what it couldn't reach, so a later run can widen there.

## Usage

```
/deepen <topic>
```

- **Light pass (default):** a fast, mostly-from-knowledge map — good for low-stakes topics or a first sketch.
- **Deep pass:** full parallel-research fan-out across distinct source pools, with the adversarial self-falsification gate — for high-value topics you want to actually master.
- **On a loop** (`/loop … /deepen <topic>`): each pass deepens the thinnest sub-areas, then *branches* into adjacent frontier topics, and pauses only when the widened frontier goes dry — not at an arbitrary count.

Re-run it on the same topic any time; it deepens the existing knowledge base instead of starting over, targeting whatever's still below your target depth.

### Configuration

| Variable | Default | Purpose |
|---|---|---|
| `DEEPEN_KB` | `./knowledge/` | Root folder for all topic KBs. Point it at an Obsidian vault or wherever your durable notes live. |

The skill resolves the knowledge-base root in this order: an explicit location you name in the request → `DEEPEN_KB` → the `./knowledge/` default, and it states the resolved path on the first line of every run so you can redirect it. **No shell to set an env var** (e.g. a hosted chat)? Just say where to write in your message ("put the KB in `<path>`"), or let it use the default and save the notes it returns.

The skill adapts to your runtime: if it can spawn parallel subagents and select per-worker models, it runs the tiered orchestrator-worker flow (cheap workers for fetch/extract, a frontier model for judgment); if it's single-agent, it runs the same structure sequentially.

## Design principles

1. **Track record over credentials.** Authority is a weak prior, never the ranking.
2. **Take falsifiable stances.** A wrong-but-falsifiable position is recoverable; a mushy non-answer isn't.
3. **Red-team yourself.** Stances must survive an adversarial refutation, a teach-back, and a prediction test before they're "earned."
4. **Honesty about evidence strength.** Cite-or-flag everything; never fabricate.
5. **Compound, don't restart.** The knowledge base is the product.
6. **Build for the next agent.** Structure the KB so a future LLM loads the right slice without reading the whole thing.

## License

MIT-0 (MIT No Attribution) — see [LICENSE](LICENSE). Free to use, modify, and redistribute, no attribution required.
