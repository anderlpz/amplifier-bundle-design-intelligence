---
bundle:
  name: design-intelligence-enhanced
  version: 2.2.0
  description: Creative intelligence system for purpose-driven problem-solving across design, engineering, product, and strategy
  sub_bundles:
    - name: advisory
      path: behaviors/design-intelligence.yaml
      description: 7 specialized design agents (art-director, component-designer, etc.)
    - name: research
      path: behaviors/design-research.yaml
      description: Purpose-driven research and cross-domain pattern discovery
    - name: generation
      path: behaviors/design-generation.yaml
      description: Token generator, spec writer, export packager
    - name: verification
      description: Visual verification tools (visual-verify, layout-context, design-validate, design-validator agent)
    - name: taste
      path: behaviors/taste-awareness.yaml
      description: Personal taste profile awareness and preference learning

includes:
  # Standalone app bundle - includes foundation for full capabilities
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  - bundle: git+https://github.com/anderlpz/amplifier-bundle-discovery@main
  # TEMPORARILY DISABLED - debugging profile_hint error
  # - bundle: git+https://github.com/anderlpz/amplifier-bundle-design-verification@main
  - bundle: design-intelligence-enhanced:behaviors/design-intelligence
  - bundle: design-intelligence-enhanced:behaviors/design-research
  - bundle: design-intelligence-enhanced:behaviors/design-generation
  - bundle: design-intelligence-enhanced:behaviors/taste-awareness
---

# Design Intelligence

> Creative intelligence for breakthrough problem-solving across domains.

## What is Design?

**Design** is purpose, planning, or intention behind any action, fact, or material object. It's the thoughtful shaping of systems, experiences, and solutions.

This bundle works for:
- **Visual design**: Interfaces, graphics, layouts, user experiences
- **Engineering design**: Systems, APIs, architectures, data models
- **Product design**: Features, flows, onboarding, engagement patterns
- **Strategic design**: Processes, organizations, go-to-market approaches

**The core capability**: Purpose-driven research that finds breakthrough solutions by discovering proven patterns from unexpected domains.

---

## Quick Start

| Domain | Example Usage |
|--------|---------------|
| **Visual Design** | `"Help me design a dashboard for monitoring system health"` |
| **Engineering** | `"Design an API rate limiting system that handles bursts gracefully"` |
| **Product** | `"Design an onboarding flow that drives feature adoption"` |
| **Strategy** | `"Design a process for handling customer escalations"` |
| **Research** | `"Find inspiration for [any creative problem]"` |
| **Trend Analysis** | `"Update my research"` (scrapes Awwwards, Siteinspire, The FWA) |

---

## The Innovation: Purpose-Driven Research

### Before (Category-Matching)
```
"Design a healthcare dashboard"
→ Research: Other healthcare dashboards
→ Output: Competent remix of existing work
→ Innovation: Low (inherits category assumptions)
```

### After (Purpose-Driven)
```
"Design a healthcare dashboard"
→ Decompose: What cognitive tasks? (rapid assessment, anomaly detection)
→ Map domains: Where else solved? (medical monitors, trading platforms, gaming HUDs)
→ Research: 20% category + 50% purpose-driven + 30% divergent
→ Extract: Level 3-4 patterns (interaction/cognitive, not just visual)
→ Synthesize: WHY each pattern is relevant
→ Output: Dashboard inspired by proven patterns from unexpected sources
→ Innovation: High (cross-pollinated ideas)
```

**Result**: Solutions that feel fresh and innovative while being grounded in proven patterns from mature domains.

---

## Real Examples Across Domains

### Visual Design: Aerospace Dashboard
- **Cognitive tasks**: Rapid status assessment, anomaly detection, timeline understanding
- **Analogous domains**: Hospital patient monitors, trading platforms, gaming HUDs, security ops
- **Patterns extracted**: Gestalt assessment from medical, confidence indicators from trading, flow state from gaming
- **Result**: Dashboard that breaks aerospace conventions in smart ways

### Engineering: API Rate Limiting
- **Problem decomposition**: Fairness, abuse prevention, resource protection, burst tolerance
- **Analogous domains**: Highway traffic metering, electrical grid balancing, network QoS, OS scheduling
- **Patterns extracted**: Entry-point metering from traffic, load shedding from electrical, priority queuing from OS
- **Result**: Sophisticated rate limiting inspired by proven systems engineering patterns

### Product: Feature Onboarding
- **User needs**: Progressive learning, safe exploration, confidence building, retention
- **Analogous domains**: Video game tutorials, driver's education, cooking classes, museum exhibits
- **Patterns extracted**: Learn-by-doing from gaming, sandbox safety from simulations, scaffolded independence from education
- **Result**: Onboarding far more effective than standard tooltips and tours

See `context/examples/` for full walkthroughs.

---

## Visual Design Research

Vision-analyzed trend research from **Awwwards**, **Siteinspire**, and **The FWA**.

**What you get:** ~35 real projects with full-page screenshots + AI vision analysis

**When to update:**
- Starting a new project (fresh inspiration)
- Weekly design reviews (stay current)
- Before presentations (latest trends)

**How to update:** Just say `"Update my research"` (~105 min to scrape & analyze)

Research updates on **your schedule**, not ours. No guilt about stale data.

---

## The Workflow

```
1. DISCOVER → What are we building and why?
2. RESEARCH → Where else is this problem solved? (cross-domain)
3. DESIGN   → What should it be? (informed by proven patterns)
4. VERIFY   → Does it match the spec? (for visual work)
5. GENERATE → Produce artifacts for implementation
```

### NEW: Visual Verification (v2.1.0)

**For visual design work only** - Prevents circular fix loops by letting design agents see what they built before presenting to you.

- **visual-verify** - Capture screenshots and compare against baseline
- **layout-context** - Extract computed layout information for alignment analysis
- **design-validate** - Systematically validate against specifications
- **design-validator agent** - Orchestrates verification workflow

**Before:** 7 commits over 2 days, you become QA tester  
**After:** One-shot fixes with screenshot evidence, you approve on first presentation

---

@design-intelligence-enhanced:context/design-instructions.md

---

## Recipes

| Recipe | What It Does | Domain |
|--------|--------------|--------|
| `design-to-implementation` | Full pipeline: idea → discovery → design → tokens → export | Visual Design |
| `design-discovery` | Discovery → research → design direction | Any Domain |
| `design-system-export` | Generate tokens + component specs + export package | Visual Design |
| `weekly-design-scrape` | Update trend research (Awwwards, Siteinspire, The FWA) | Visual Design |

**Run a recipe:**
```
Run the design-discovery recipe for [describe your problem in any domain]
```

---

## How This Augments Your Thinking

This isn't just a tool that gives you answers—it teaches you a **meta-cognitive skill** that great practitioners naturally have:

1. **Decompose problems** into fundamental challenges (not just domain specs)
2. **Think across domains** (where else is this solved?)
3. **Abstract patterns** (what's transferable vs. context-specific?)
4. **Reason explicitly** (why is this relevant to our context?)
5. **Challenge assumptions** (does this actually fit our problem?)

**This is the skill that separates great engineers/designers/product people from good ones**—the methodology makes it systematic and teachable.

### Escaping Cargo Cult Thinking

**Before**: "Everyone uses microservices, so we should too"

**After**: 
- "What problem does distribution solve?" (scale, resilience, autonomy)
- "Where is distribution solved best?" (telecommunications, biological systems)
- "What are the trade-offs?" (complexity, latency, consistency)
- "Does our problem actually need this?" (explicit reasoning)

**Result**: Principled decision-making, not fashion-following.

---

## Design Philosophy

@design-intelligence-enhanced:context/philosophy/DESIGN-PHILOSOPHY.md
@design-intelligence-enhanced:context/philosophy/DESIGN-PRINCIPLES.md
@design-intelligence-enhanced:context/philosophy/DESIGN-FRAMEWORK.md
@design-intelligence-enhanced:context/philosophy/WRITING-PRINCIPLES.md

---

## Research Methodology

**NEW in v2.2.0**: Complete purpose-driven research methodology

@design-intelligence-enhanced:context/research-methodology/creative-research-methodology.md
@design-intelligence-enhanced:context/research-methodology/cognitive-task-catalog.md
@design-intelligence-enhanced:context/research-methodology/pattern-abstraction-guide.md
@design-intelligence-enhanced:context/research-methodology/cognitive-discovery-enhancement.md

---

@foundation:context/shared/common-system-base.md
