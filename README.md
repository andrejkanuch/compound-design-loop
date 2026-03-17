# Compound Design Loop

**Build fast, then refine through specialized lenses.**

A Claude Code plugin that runs all 19 [Impeccable](https://impeccable.style) design commands through parallel agent teams — each playing a specialist role (UI designer, domain expert, motion designer, accessibility auditor).

Good design isn't one big decision — it's 15 small ones made through different lenses.

## Install

```bash
claude plugin install compound-design-loop
```

Or test locally:

```bash
claude --plugin-dir /path/to/compound-design-loop
```

## Commands

### `/compound-design-loop:design-loop <file> [--domain=X]`

The full loop. Runs all 19 Impeccable commands in 4 iterations through 18 parallel agents:

```
Iteration 1: DIAGNOSE    → /critique, /audit + domain expert + lead designer
Iteration 2: SYSTEMATIZE → /normalize, /typeset, /arrange, /clarify
Iteration 3: ENHANCE     → /animate, /delight, /distill, /harden, /colorize
Iteration 4: POLISH      → /adapt, /onboard, /optimize, /polish, /extract, /bolder, /overdrive
```

### `/compound-design-loop:design-brainstorm <file> [--domain=X]`

Quick 3-agent brainstorm without the full loop. Use for early-stage feedback.

### `/compound-design-loop:design-status`

Check progress of a running design loop.

## Domain Presets

The `--domain` flag customizes the domain expert agent:

| Domain | Expert Persona |
|--------|---------------|
| `motorcycle` | 15-year rider, Calimoto/RISER user. Glanceability, glove targets, sunlight, vibration. |
| `fitness` | Daily Strava user. Mid-workout readability, GPS accuracy, splits/pace. |
| `finance` | Day trader. Data density, real-time updates, P&L color coding. |
| `ecommerce` | Power shopper. Product images, price clarity, checkout friction. |
| `medical` | ER nurse. Alert hierarchy, medication safety, patient ID prominence. |
| `default` | Power user of the app's domain. |

## How It Works

```
Build (functional) → Brainstorm (team) → Command Loop → Ship

                                            ↓
                                ┌─ /critique (identify problems)
                                ├─ /audit (accessibility + perf)
                                ├─ /normalize (design system)
                                ├─ /typeset (typography)
                                ├─ /arrange (layout)
                                ├─ /clarify (UX copy)
                                ├─ /animate (motion)
                                ├─ /delight (personality)
                                ├─ /distill (strip excess)
                                ├─ /harden (edge cases)
                                ├─ /colorize (color strategy)
                                ├─ /adapt (responsive)
                                ├─ /onboard (first-time UX)
                                ├─ /optimize (performance)
                                ├─ /polish (final 5%)
                                ├─ /extract (design system spec)
                                ├─ /bolder (amplify)
                                ├─ /overdrive (wow effect)
                                └─ /critique (verify) → done
```

## Principles

1. **Separate building from designing.** Feature works first, then redesign.
2. **Multi-persona brainstorm.** One person can't hold all perspectives.
3. **One command = one lens.** Opposing forces balance each other.
4. **Subtraction before addition.** /distill before /delight.
5. **Critique sandwich.** Critique → iterate → critique to verify.

## Works With

- [Impeccable](https://impeccable.style) — design vocabulary plugin (recommended)
- [Ralph Loop](https://github.com/nichochar/ralph-loop) — persistent iteration loop (optional)
- [Compound Engineering](https://github.com/compound-engineering/compound-engineering) — engineering workflow (optional)

## License

MIT
