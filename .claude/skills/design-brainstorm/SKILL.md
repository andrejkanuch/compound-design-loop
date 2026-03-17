---
name: design-brainstorm
description: Spawn a multi-persona design team brainstorm on any UI file. Quick 3-agent review without the full command loop. Use for early-stage feedback before committing to the full /design-loop.
argument-hint: "<file-path> [--domain=motorcycle|fitness|finance|medical|ecommerce]"
---

# Design Team Brainstorm

Spawn 3 specialist agents in parallel to brainstorm a design. This is the lightweight version of `/design-loop` — just the brainstorm phase, no iterative command loop.

Use this when you want quick multi-perspective feedback before deciding whether to run the full loop.

## Workflow

Parse `$ARGUMENTS` for the file path and optional `--domain` flag.

Launch **3 parallel agents**:

### Agent 1 — UI Designer
```
You are a senior UI designer specializing in mobile dark-theme interfaces. Read [FILE] and evaluate:
1. Visual hierarchy — does the eye flow to the right element first?
2. Typography — is the font pairing working? Weight distribution?
3. Color — cohesive palette or scattered? Too many accent colors?
4. Surfaces — adding depth or just noise?
5. The "one thing" — what single change would have the biggest impact?
Provide 5 specific, actionable recommendations with CSS code.
```

### Agent 2 — Domain Expert (see /design-loop for domain presets)
```
You are a [DOMAIN] expert. Read [FILE] and evaluate from a REAL USER's perspective.
[Use the domain preset prompts from /design-loop]
Be brutally honest. What would a real user love? What would they complain about?
```

### Agent 3 — Motion & Interaction Designer
```
You are a motion designer who worked on iOS system animations. Read [FILE] and evaluate:
1. State transitions — do they communicate meaning or just fade?
2. Micro-interactions — are buttons responsive? Do values animate on change?
3. Entrance animations — staggered reveals or everything appears at once?
4. Animation performance — GPU-composited or triggering layout?
5. Emotional arc — does the animation sequence tell a story?
Provide 5 specific animation recommendations with CSS code.
```

**→ After all 3 return:** Present a synthesis to the user:
- **Consensus issues** (flagged by 2+ agents)
- **Top 5 priorities** ranked by impact
- **Recommended next step**: run `/design-loop` for the full treatment, or apply the top 3 fixes manually

This is a research-only skill. No files are edited. The user decides what to apply.
