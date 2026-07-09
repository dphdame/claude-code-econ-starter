---
name: session-notes
description: Capture end-of-session context before it resets. Use when the user says "wrap up", "end session", "session notes", or is closing a working session. Writes a dated note recording what changed, why it changed, what comes next, and what failed.
---

# Session Notes

Five minutes of capture at the end of a session saves twenty minutes of reconstruction tomorrow. This skill produces a dated capture note and refreshes the project's context file, so the next session warm-starts instead of beginning with "what were we working on yesterday?"

Why these steps: https://tooearlytosay.com/research/methodology/end-of-session-hygiene/

## When to run

At the end of any productive session, while still inside the work, before the mental shift to "done". Also on request: "wrap up", "session notes", "capture before we close".

## Workflow

1. Review the session and draft the four capture categories:
   - **What changed:** files touched, functions added or refactored, results produced.
   - **Why it changed:** the reasons behind non-obvious choices, plus the constraints and trade-offs that shaped them.
   - **What comes next:** the concrete next tasks, written down while they are still clear.
   - **What failed:** approaches tried and rejected, each with its reason, so nobody re-explores a dead end.
2. Append the note to `docs/session-log.md` (create the file if absent) under a dated heading: `## Session: YYYY-MM-DD`.
3. If the project has a CLAUDE.md with a "Current analysis focus" or "Current work" section, update that section to match the new state. Different context belongs in different places: the agent reads CLAUDE.md next session; the session log is the human record.
4. Show the drafted note to the user for a one-minute review before finishing. The agent has full recall of the session and drafts faster than the user can; the user edits, never reconstructs.

## What not to capture

- Changes self-evident from the diff
- Decisions already documented in code comments
- Standard patterns that need no explanation

The test: reading only the code, would a stranger understand this? If yes, skip it. If no, capture it.

## Success criteria

- A dated entry exists in `docs/session-log.md` covering all four categories
- The CLAUDE.md current-state section reflects the session (when that file exists)
- Total capture time stays near five minutes; longer means over-documenting
