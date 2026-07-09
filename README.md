# claude-code-econ-starter

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
![Tested with Claude Code v2.1.205](https://img.shields.io/badge/Tested%20with-Claude%20Code%20v2.1.205-5A67D8.svg)

**1 CLAUDE.md template, 1 verification checklist, 3 starter skills, 1 week-one glossary, and a printable desk reference, for economists starting Claude Code.**

Copy the files into a project and start working. Each file stands alone; take one or take all of them.

## Install

**Option A, no shell required.** Paste this sentence into Claude Code inside your project:

> Clone https://github.com/dphdame/claude-code-econ-starter into a temporary folder, copy templates/CLAUDE.md into the root of my current project as CLAUDE.md (ask me first if a CLAUDE.md already exists), copy checklist/verification-checklist.md into my project, copy each folder inside skills/ into ~/.claude/skills/, then list everything you installed and delete the temporary clone.

**Option B, plain git:**

```bash
git clone https://github.com/dphdame/claude-code-econ-starter.git
cd claude-code-econ-starter
cp templates/CLAUDE.md /path/to/your-project/CLAUDE.md
cp checklist/verification-checklist.md /path/to/your-project/
cp -r skills/session-notes skills/validate-estimator skills/first-skill-template ~/.claude/skills/
```

The kit's practices come from standard software engineering and the econometrics simulation tradition; the design rationale for each file is in the linked articles below. For a lecture-length introduction to working this way, [Paul Goldsmith-Pinkham's Claude Code for empirical research series](https://paulgp.substack.com/) (Markus Academy) is worth watching alongside the setup. Not affiliated with Anthropic; Claude Code is Anthropic's tool, and this is an independent starter kit for it.

## What's inside

| File | What it does | Grab it alone | Design rationale |
|------|--------------|---------------|------------------|
| [templates/CLAUDE.md](templates/CLAUDE.md) | Project context file the agent reads every session: data conventions, file organization, current focus, known pitfalls | [raw](https://raw.githubusercontent.com/dphdame/claude-code-econ-starter/main/templates/CLAUDE.md) | [Why these sections](https://tooearlytosay.com/research/methodology/claude-md-research-context/) |
| [checklist/verification-checklist.md](checklist/verification-checklist.md) | 13 pass/fail checks across citations, estimator code, and empirical claims; the agent satisfies them before a human reads the output | [raw](https://raw.githubusercontent.com/dphdame/claude-code-econ-starter/main/checklist/verification-checklist.md) | [Why these items](https://tooearlytosay.com/research/methodology/verification-tax/) |
| [skills/session-notes](skills/session-notes/SKILL.md) | End-of-session capture: what changed, why, what comes next, what failed, into a dated note | [raw](https://raw.githubusercontent.com/dphdame/claude-code-econ-starter/main/skills/session-notes/SKILL.md) | [Why capture](https://tooearlytosay.com/research/methodology/end-of-session-hygiene/) |
| [skills/validate-estimator](skills/validate-estimator/SKILL.md) | Planted-truth routine for estimator code: plant a known effect, require the implementation to recover it | [raw](https://raw.githubusercontent.com/dphdame/claude-code-econ-starter/main/skills/validate-estimator/SKILL.md) | [Why this routine](https://tooearlytosay.com/research/methodology/validate-ai-econometric-code/) |
| [skills/first-skill-template](skills/first-skill-template/SKILL.md) | Guided creation of a first custom skill from a task that keeps getting re-explained | [raw](https://raw.githubusercontent.com/dphdame/claude-code-econ-starter/main/skills/first-skill-template/SKILL.md) | [Why this structure](https://tooearlytosay.com/research/methodology/creating-skills/) |
| [GLOSSARY.md](GLOSSARY.md) | 10 week-one terms, from commit to compaction, each with why it matters for research | [raw](https://raw.githubusercontent.com/dphdame/claude-code-econ-starter/main/GLOSSARY.md) | [Why a token budget](https://tooearlytosay.com/research/methodology/context-window-budgeting/) |
| [printables/desk-reference.html](printables/desk-reference.html) | Two printed pages for the desk: the checklist with checkboxes and an end-of-session capture box, plus the glossary. Open in a browser, print | [raw](https://raw.githubusercontent.com/dphdame/claude-code-econ-starter/main/printables/desk-reference.html) | Same items as the checklist and glossary above |

## What this is not

This is a starter kit, deliberately small: not a full research pipeline, not a skills library, and not a prose setup guide. It is the smallest set of files that makes a second session better than the first.

## What's next

When these starters feel small, [tets-claude-skills](https://github.com/dphdame/tets-claude-skills) has single-purpose skills for applied economists: paper summaries, replication-package analytics, and citation-network audits.

## New to all of this?

Start with the first-session walkthrough at [tooearlytosay.com/research/methodology/first-session-claude-code/](https://tooearlytosay.com/research/methodology/first-session-claude-code/) and keep [GLOSSARY.md](GLOSSARY.md) open beside it.

---

MIT License · Tested with Claude Code v2.1.205 · Victoria Cholette · [tooearlytosay.com](https://tooearlytosay.com/)
