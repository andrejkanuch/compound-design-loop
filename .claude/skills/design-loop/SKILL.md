---
name: design-loop
description: Run the full Compound Design Loop — multi-persona brainstorm + all 19 Impeccable commands through parallel agent teams. Use when you want to take a functional UI from "working" to "production-grade premium."
argument-hint: "<file-path> [--domain=motorcycle|fitness|finance|medical|ecommerce] [--max-iterations=10]"
---

# The Compound Design Loop

**Build fast, then refine through specialized lenses.**

Good design isn't one big decision — it's 15 small ones made through different lenses. Each pass takes 5-10 minutes but compounds into a result that feels intentional and premium.

## Prerequisites

This plugin works best with the [Impeccable](https://impeccable.style) plugin installed for the individual command skills. If Impeccable is not installed, the agents will still run — they just won't have access to the Impeccable skill prompts (the agent prompts below are self-contained).

## Principles

1. **Separate building from designing.** The feature should already work before this runs.
2. **Multi-persona brainstorm before code.** 3-4 specialist agents discuss simultaneously.
3. **One command = one lens.** Each forces you to look through a different filter.
4. **Subtraction before addition.** Always /distill before /delight.
5. **Critique sandwich.** Critique → iterate → critique again to verify.

## Arguments

Parse the arguments from `$ARGUMENTS`:
- **file-path** (required): The HTML/JSX/TSX file to redesign
- **--domain** (optional, default: "default"): Domain expert persona preset
- **--max-iterations** (optional, default: 10): Maximum iteration cap

## Step 0: Setup

1. If `ralph-loop` plugin is available, activate it:
   ```
   /ralph-loop:ralph-loop "finish all Impeccable commands on [FILE]" --max-iterations [MAX] --completion-promise "ALL_COMMANDS_COMPLETE"
   ```
2. Create a `design-review-progress.md` file next to the target file with all 19 commands as unchecked checkboxes, grouped by phase.

## Step 1: DIAGNOSE (Iteration 1)

Launch **3 parallel agents** using the Agent tool:

### Agent 1 — Auditor (/critique + /audit)
```
You are a senior frontend auditor running /critique and /audit on [FILE].

Perform a comprehensive evaluation:
CRITIQUE: Visual hierarchy, information density, emotional resonance, state transitions, discoverability, composition balance, typography communication, color purpose.
AUDIT: WCAG AA contrast ratios, keyboard nav, ARIA labels, focus states, animation performance (GPU-composited?), CSS variable consistency, responsive behavior, browser compatibility.

For each issue: severity (critical/major/minor), exact CSS selector, specific fix code.
Do NOT edit the file. Output findings only.
```

### Agent 2 — Domain Expert (customized per --domain)
```
You are a [DOMAIN DESCRIPTION] who uses this type of app daily. Read [FILE] and evaluate from a REAL USER's perspective.

Evaluate: [DOMAIN-SPECIFIC CRITERIA — see Domain Presets section below]

Be BRUTALLY honest. What would a real user love and what would they complain about? Provide specific design recommendations.
Do NOT edit the file. Output findings only.
```

### Agent 3 — Lead Designer
```
You are a lead product designer at a premium app studio. Read [FILE] and evaluate visual design quality.

Evaluate: visual sophistication (premium or generic?), typography system (hierarchy, pairing, numeric features), color usage (harmony or chaos?), spatial rhythm (consistent grid?), surface treatment (depth or noise?), iconography (professional or placeholder?), state differentiation (distinguishable from blurred screenshot?).

What is the SINGLE most impactful improvement? Provide specific CSS for your top 5 recommendations.
Do NOT edit the file. Output findings only.
```

**→ After all 3 return:** Synthesize findings. Identify consensus issues (flagged by 2+ agents). Prioritize: safety > accessibility > visual > polish. Apply critical fixes. Update progress tracker. Mark `/critique` and `/audit` complete.

## Step 2: SYSTEMATIZE (Iteration 2)

Launch **4 parallel agents**:

### Agent 4 — /normalize
```
You are running /normalize. Read [FILE] and check design system consistency:
1. CSS variable usage — find ALL hardcoded colors/spacing that should use variables
2. Spacing grid — check all values align to 4px base grid, flag off-grid values
3. Border radius tokens — find inline values not using tokens
4. Color system — find hex colors bypassing CSS variables
5. Font weight — flag any weights not loaded in the font import
Output a structured report with current value → recommended value for each.
Do NOT edit the file.
```

### Agent 5 — /typeset
```
You are running /typeset. Read [FILE] and fix typography:
1. Type scale — list all font-sizes, check they follow a modular scale
2. Line heights — headlines tight (1-1.1), body comfortable (1.4-1.6)
3. Letter spacing — uppercase labels need +0.05-0.15em, display text may need negative
4. Font weight distribution — meaningful hierarchy or everything bold?
5. Monospace vs sans — consistent usage for data vs labels?
6. Readability — flag text under 11px that isn't a label
Output specific CSS property changes with rationale.
Do NOT edit the file.
```

### Agent 6 — /arrange
```
You are running /arrange. Read [FILE] and fix layout/spacing:
1. Vertical rhythm — consistent spacing between major sections?
2. Horizontal alignment — elements aligned to same edge grid?
3. Content grouping — Gestalt proximity principle applied?
4. Overflow — will content fit at target viewport width?
5. Safe areas — controls clear of system UI/navigation?
Apply the TOP 10 most impactful layout fixes directly to the file.
```

### Agent 7 — /clarify
```
You are running /clarify. Read [FILE] and improve all UX copy:
1. Labels — clear and unambiguous? Appropriate abbreviation level?
2. Button text — action-oriented?
3. Status indicators — contextually appropriate?
4. Abbreviation consistency — units consistent throughout?
5. Voice/tone — matches the product personality?
For each: current text, recommended text, why, priority.
Do NOT edit the file.
```

**→ Synthesize & apply all fixes.** Update progress. Mark 4 commands complete.

## Step 3: ENHANCE + HARDEN (Iteration 3)

Launch **5 parallel agents**:

### Agent 8 — /animate
```
You are running /animate. Read [FILE] and identify purposeful motion opportunities:
State transitions, value changes, entrance animations, button interactions.
ALL animations MUST be GPU-composited (transform/opacity only).
Provide exact CSS code. Only add motion that serves a purpose — this is a utility app, not Dribbble.
Do NOT edit the file.
```

### Agent 9 — /delight (MAY EDIT)
```
You are running /delight. Read [FILE] and add moments of personality and joy.
Focus on: completion celebrations, anticipation building, satisfying confirmations, ambient life.
Keep suggestions to 5-7 max. Provide exact CSS/JS code.
You MAY edit the file directly to add delight features (new animations, celebration effects).
```

### Agent 10 — /distill
```
You are running /distill. Read [FILE] and strip to ESSENCE.
Identify: elements to remove entirely, visual complexity to simplify, redundant information, decorative noise.
Be ruthless — what would Dieter Rams remove?
Output prioritized list of 8-10 simplifications.
Do NOT edit the file.
```

### Agent 11 — /harden (MAY EDIT)
```
You are running /harden. Read [FILE] and make it RESILIENT.
Check: accidental destructive actions (confirmation needed?), error states, text overflow, edge case values (empty, very long, 3+ digits), loading states, offline handling.
You MAY edit the file directly to add safety features (confirmation dialogs, overflow protection, error states).
```

### Agent 12 — /colorize
```
You are running /colorize. Read [FILE] and evaluate color:
1. Semantic consistency — does each color always mean the same thing?
2. State conflicts — same color used for different semantic meanings?
3. Colorblind safety — can red-green colorblind users distinguish states?
4. Sunlight/high-contrast readability — which colors lose contrast outdoors?
Provide specific CSS variable adjustments. Max 6 changes.
Do NOT edit the file.
```

**→ Synthesize & apply.** Update progress. Mark 5 commands complete.

## Step 4: POLISH + SHIP (Iteration 4)

Launch **5-6 parallel agents**:

### Agent 13 — /adapt
```
You are running /adapt. Read [FILE] and ensure cross-device support:
1. Narrow screens (360px) — overflow?
2. Wide screens (430px) — gaps?
3. Safe areas — env(safe-area-inset-*)?
4. Landscape — lock or support?
5. Color scheme — force dark/light?
Output CSS media queries to add. Max 5 changes.
Do NOT edit the file.
```

### Agent 14 — /onboard
```
You are running /onboard. Read [FILE] and evaluate first-time UX:
1. Empty/first-time states — what shows with no data?
2. Feature discoverability — can users find all features?
3. Label self-explanation — do labels make sense without context?
Provide 3-5 minimal copy/UI tweaks.
Do NOT edit the file.
```

### Agent 15 — /optimize
```
You are running /optimize. Read [FILE] and optimize performance:
1. Font loading — trim unused weights
2. CSS — replace transition:all with specific properties
3. Animations — verify GPU-composited only
4. SVG — simplify paths
5. Unused CSS — remove dead rules
Prioritized list of 5-8 optimizations.
Do NOT edit the file.
```

### Agent 16 — /polish
```
You are running /polish — the FINAL quality pass. Read [FILE]:
1. Pixel-level alignment
2. Visual consistency between similar elements
3. Remaining off-grid spacing values
4. Animation timing consistency (same easing family?)
5. Missing :active states on interactive elements
6. Shadow depth logic
7. Optical centering of hero elements
The last 5% that separates good from great.
Do NOT edit the file.
```

### Agent 17 — /extract
```
You are running /extract. Read [FILE] and catalog design system tokens:
1. Color tokens — all CSS variables + semantic usage
2. Typography — type scale, weight distribution, font features
3. Spacing — grid system, recurring values
4. Components — reusable patterns (anatomy + variants)
5. Animations — easing curves, durations, patterns
6. Surfaces — tier system with opacity/border values
Output as structured design system specification.
Do NOT edit the file.
```

### Agent 18 — /bolder + /overdrive
```
You are running /bolder and /overdrive. Read [FILE]:
BOLDER: Find 3-5 areas that are too safe/timid and suggest targeted amplifications.
OVERDRIVE: Propose ONE technically impressive CSS/SVG/JS effect that serves the user context (not just decoration).
Provide exact code for both.
Do NOT edit the file.
```

**→ Apply final fixes.** Update progress. Mark all remaining commands complete.

## Step 5: Completion

Update the progress tracker with "COMPLETE" status and design team sign-off.

If Ralph Loop is active, output: `<promise>ALL_COMMANDS_COMPLETE</promise>`

Output a final summary: commands completed, total fixes applied, key improvements by category.

---

## Domain Expert Presets

The `--domain` flag customizes Agent 2:

### `--domain=motorcycle`
> You are a motorcyclist with 15 years riding experience. You've used Calimoto, RISER, Ducati Link, BMW Connected Ride. Evaluate: at-speed glanceability (0.3s read time), glove operation (48px+ targets), sunlight readability, vibration blur tolerance, mounting context (RAM mount on handlebars), safety (accidental tap protection), auto-pause, screen lock for rain. Compare to competitor apps.

### `--domain=fitness`
> You are a runner/cyclist who uses Strava, Nike Run Club, and Wahoo daily. Evaluate: mid-workout readability (bouncing phone), split/pace/HR clarity, GPS accuracy indicators, auto-pause reliability, weather/hydration context, post-workout sharing flow, achievement moments. Compare to Strava's UX.

### `--domain=finance`
> You are a day trader using Bloomberg Terminal, Robinhood, and TradingView. Evaluate: data density (can I see enough at a glance?), real-time update clarity, color-coded P&L (red/green cultural sensitivity), order confirmation safety, portfolio overview vs detail balance, error-state urgency for failed trades.

### `--domain=ecommerce`
> You are a power shopper who uses Amazon, Shopify stores, and ASOS daily. Evaluate: product image dominance, price/discount clarity, add-to-cart friction, trust signals, shipping/return info prominence, checkout flow anxiety reducers, size/variant selection ease.

### `--domain=medical`
> You are an ER nurse using Epic and Cerner systems. Evaluate: critical alert hierarchy (life-threatening vs informational), medication dose prominence, patient ID always visible, handoff clarity, color-coded triage levels, error prevention for wrong-patient actions, time-sensitive task urgency.

### `--domain=default`
> You are a power user of this application who has used it daily for 2 years and has tried every competitor. Evaluate: workflow efficiency, feature discoverability, information hierarchy for your most common tasks, edge cases you've hit, what competitors do better, what would make you recommend this to a friend.

---

## Research vs. Edit Agent Rules

**Research-only agents** (output findings, you synthesize):
- /critique, /audit, /normalize, /typeset, /clarify, /animate, /distill, /colorize, /adapt, /onboard, /optimize, /polish, /extract, /bolder, /overdrive

**May edit the file directly** (add new features):
- /arrange (layout restructuring)
- /delight (celebration animations, JS effects)
- /harden (safety features, error states, overflow protection)

This prevents conflicting edits while allowing agents that add genuinely new functionality to operate autonomously.
