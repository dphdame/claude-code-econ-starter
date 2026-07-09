---
name: first-skill-template
description: Turn a repeated research task into the user's first custom Claude Code skill. Use when the user says "create a skill", "make my first skill", or wants to stop re-explaining the same workflow every session.
---

# First Skill Template

A skill is saved instructions for a task that repeats: a recipe card the agent follows the same way every time. Write the steps once, save them in a file, and the workflow survives context resets. This skill walks the user from a repeated task to a working skill file, using the bracketed template below.

Why this structure: https://tooearlytosay.com/research/methodology/creating-skills/

## Workflow

1. **Identify the repeated task.** Ask the user: which task gets explained to the agent at least once a week? Which process has steps that are sometimes forgotten? The best candidate encodes something already done manually.
2. **Document the task as it is done.** Have the user list every step of the real workflow, including the checks they regret skipping. The real version, never the idealized one: if sample sizes always get checked before a regression, that goes in; if clustering sometimes gets forgotten, the reminder goes in too.
3. **Fill in the template below** with those steps. Make every workflow step explicit and verifiable; the agent will follow them literally.
4. **Choose where the skill lives:**
   - Project-local, at `<project>/.claude/skills/<skill-name>/SKILL.md`, when the workflow depends on project specifics: variable names, data structure, identification strategy, sample definitions.
   - Global, at `~/.claude/skills/<skill-name>/SKILL.md`, when the workflow is the same in every project: citation checks, table formatting standards, writing conventions. A project-local skill overrides a global one with the same name.
5. **Save and test on a real task.** Ask the user to run it on genuine work, then note what the skill missed, what step was unclear, and what output surprised them.
6. **Refine after each of the next three uses.** A skill is never finished on the first draft; each refinement persists, so a gap fixed once benefits every future run.

## The template

Copy this block into `SKILL.md` inside a folder named after the skill, and replace every bracket.

```markdown
---
name: [skill-name, lowercase with hyphens]
description: [What this skill does and when to run it. Include the phrases a user would say, such as "run robustness checks".]
---

# [Skill Title]

## Purpose

[What this skill accomplishes, in one or two sentences.]

## Prerequisites

- [What must be true before running. Example: main specification estimated and saved.]
- [Another precondition, or delete this line.]

## Workflow

1. [An explicit, verifiable step. Example: load the baseline estimates from data/output/.]
2. [The next step.]
3. [Present the result for review before any irreversible action.]

## Success criteria

- [How success is known. Make each item checkable: "all variables documented" is checkable; "documentation is complete" is not.]
- [Another criterion, or delete this line.]
```

## Design rules worth keeping

- **Single purpose.** One skill does one thing well; a skill that reviews literature and runs regressions and formats tables is three skills pretending to be one.
- **Clear success criteria.** Define explicitly how completion is known.
- **Documented prerequisites.** Naming what must be true before the run prevents wasted runs.
- **Checkpoint confirmations.** Any step that changes files or is hard to reverse gets a "proceed?" pause.

## Success criteria

- A `SKILL.md` exists in the chosen location with every bracket replaced
- The frontmatter has a hyphenated name and a description that includes trigger phrases
- The user ran the new skill once on real work and recorded at least one refinement
