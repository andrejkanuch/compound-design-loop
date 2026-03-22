# Changelog

All notable changes to the Compound Design Loop plugin.

## [1.0.0] - 2026-03-22

First public release.

### Core
- 3 skills: design-loop, design-brainstorm, design-status
- 8 specialist agents across 4 iterations (DIAGNOSE, FOUNDATIONS, ENHANCE, SHIP)
- 6 domain presets (motorcycle, fitness, finance, ecommerce, medical, default)
- 4 reference files: agent-roles, domain-experts, critique-framework, accessibility-checklist
- Mandatory context gathering with auto-detection (platform, theme, scope, context, domain)
- All agent prompts parameterized by DESIGN_CONTEXT placeholders
- Auto-apply synthesis protocol between iterations with conflict resolution
- Structured progress file (design-review-progress.md) shared between design-loop and design-status
- Agent failure recovery (timeout, empty output, context exhaustion)
- Input validation with clear error messages
- NEVER section documenting anti-patterns with reasons
- Ralph Loop integration for persistent iteration

### Design Decisions
- All agents are research-only; only the orchestrator edits files during synthesis — prevents concurrent edit collisions
- 2-agent-per-iteration limit matches Claude Code's reliable concurrency
- Brainstorm auto-detects all 5 context signals (no interactive questions) for speed
- Design-loop auto-detects 3 of 5 signals, asks user to confirm — balances speed with accuracy
- Fully standalone — Impeccable plugin is complementary, not a dependency
