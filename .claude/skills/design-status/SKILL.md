---
name: design-status
description: Check the progress of a running Compound Design Loop. Shows which commands have been completed, which are pending, and the current iteration.
---

# Design Loop Status

Check the progress of the current design loop.

## Workflow

1. Look for a `design-review-progress.md` file in the current directory or project root
2. If found, read it and display:
   - Commands completed vs total (e.g., "14/19")
   - Current iteration number
   - Which phase we're in (Diagnose / Systematize / Enhance / Polish)
   - List of remaining commands
   - Design team sign-off status
3. If not found, say "No active design loop found. Run `/compound-design-loop:design-loop <file>` to start one."
