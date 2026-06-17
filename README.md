# /deepen

**An Agent Skill that builds genuine expertise in any topic — and compounds it across sessions.**

Most "learn a domain" skills *summarize a field*. `/deepen` doesn't. Point it at a topic and it acquires defensible expertise: it weights sources by **checkable track record** (not fame), takes **falsifiable stances** on the open controversies, **attacks its own conclusions before committing them**, and writes the result as an evergreen knowledge base that gets deeper every time you run it.

```
/deepen PPC
/deepen sleep apnea
/deepen pickleball paddle physics
```

Works anywhere the [Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) open standard is supported — Claude Code, Claude.ai, the Claude API, and compatible runtimes.

---

## Why it's different

| Typical "domain expert" skill | `/deepen` |
|---|---|
| Ranks sources by **authority** (official docs → blogs) | Ranks by **checkable track record** — a famous source with bad calls loses to an independent one with good ones |
| Reports "both sides have merit" | **Takes a stance** with calibrated confidence + the explicit evidence that would flip it |
| States conclusions as fact | **Cite-or-flag**: every claim cites a source or is tagged `[inference]`/`[convention]` — no confident hallucination |
| Simulates a fictional "expert persona" | Synthesizes the **real published record** — never fabricates experts, credentials, or quotes |
| One-shot report | **Compounds**: a living knowledge base that deepens on every re-run, with a changelog and supersede rules |

> A competent literature summary tells you what people say. **Expertise tells you what's true, what's contested, what *you* judge correct, and what would change your mind.**

## Grounded in real method, not vibes

The workflow is built on a verified research synthesis:

- **Cooke's Classical Model / structured expert judgment** (Colson & Cooke 2018) — weight experts by demonstrated accuracy; across 33 studies, <1/3 of credentialed experts were statistically accurate.
- **Systematic overconfidence** (Morgan 2014, PNAS) — experts' stated uncertainty is consistently too narrow, so confidence intervals get widened on purpose.
- **CFAR Double Crux** — a procedure for finding the load-bearing belief under a disagreement and taking a falsifiable position.
- **Andy Matuschak's evergreen notes** — atomic, concept-oriented, densely-linked notes designed to accrete.
- **Anthropic's orchestrator-worker pattern** — decompose, fan out parallel researchers, synthesize (~+90% over single-agent on breadth-first research).

Where a step rests on practitioner convention rather than verified evidence (e.g. ICE/RICE tactic ranking), the skill says so — and so does its output.

## What it produces

A folder per topic under your knowledge-base root (`./knowledge/<topic>/` by default, or set `DEEPEN_KB`):

```
knowledge/ppc/
  _map.md            # index + depth-calibration dashboard (what's solid vs. thin)
  principles.md      # durable first-principles, each with a "common misconceptions" line
  experts.md         # the expert map, weighted by track-record proxy ladder
  disagreements.md   # live debates: crux, my stance, confidence, falsifier, survived-refutation
  tactics.md         # ranked A+ playbook, tuned to YOUR context
  changelog.md       # one line per run — accretion stays auditable
```

Every run ends with a tight brief: what I now know (with confidence), where I took a stance (and what would flip it), the ranked tactics, and the thin spots worth a deeper pass.

## Install

```bash
# with the skills CLI (replace with this repo's URL once published)
npx skills add <your-repo-url> --skill deepen
```

Or copy `skills/deepen/SKILL.md` into your agent's skills directory (e.g. `~/.claude/skills/deepen/` for Claude Code).

## Usage

```
/deepen <topic>
```

- **Light pass (default):** a fast, mostly-from-knowledge map — good for low-stakes topics or a first sketch.
- **Deep pass:** full parallel-research fan-out with the adversarial self-falsification gate — for high-value topics you want to actually master.

Re-run it on the same topic any time; it deepens the existing knowledge base instead of starting over, targeting whatever's still below your target depth.

## Design principles

1. **Track record over credentials.** Authority is a weak prior, never the ranking.
2. **Take falsifiable stances.** A wrong-but-falsifiable position is recoverable; a mushy non-answer isn't.
3. **Red-team yourself.** Stances must survive an adversarial refutation, a teach-back, and a prediction test before they're "earned."
4. **Honesty about evidence strength.** Cite-or-flag everything; never fabricate.
5. **Compound, don't restart.** The knowledge base is the product.

## License

MIT — see [LICENSE](LICENSE).
