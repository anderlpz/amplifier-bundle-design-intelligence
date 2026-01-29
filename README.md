# Design Intelligence Enhanced

> **Creative intelligence for purposeful problem-solving across design, engineering, product, and strategy.**

When you need to make intentional decisions about how things should work—whether designing an API, building a dashboard, architecting a system, or optimizing a process—this bundle helps you think deeper, research broader, and solve better.

---

## The Core Problem

You're building something important. You know it should be **purposeful**, not arbitrary. But how do you:

- **Discover** what actually matters (not what you assume)
- **Research** proven patterns across domains (not just your silo)
- **Extract** principles that apply to your specific problem
- **Synthesize** solutions that are both novel and grounded

AI can generate code fast. But **design**—the purpose, planning, and intention behind what you build—requires a different approach.

---

## The Solution: Creative Research Methodology

This bundle embodies a universal methodology for purposeful problem-solving:

```
1. DECOMPOSE    → Break problems into cognitive tasks, system challenges, or coordination needs
2. MAP DOMAINS  → Find analogous problems in unexpected places
3. RESEARCH     → Study how other domains solved similar challenges (L3-4 principles)
4. SYNTHESIZE   → Apply extracted patterns to your specific context
```

**Works across domains:**
- **Visual/Product**: Dashboard design, user flows, interface patterns
- **Engineering**: API design, database migrations, distributed systems
- **Strategy**: Process optimization, resource allocation, organizational design

**The key insight:** Every domain has solved problems similar to yours. Cross-domain research reveals principles (L3-4 understanding) you can adapt.

---

## Version 2.2.0: Universal Applicability

**NEW**: Explicitly supports engineering, product, and strategy work—not just visual design.

**What changed:**
- Domain detection (visual/engineering/strategy) with adapted approaches
- Engineering examples: API rate limiting, database migrations, distributed coordination
- Cognitive task catalog expanded: fairness under load, failure isolation, habit formation
- Research analyst adapts questions based on detected domain

**Core philosophy:**
> Design is purpose, planning, and intention behind any action, system, or process. This methodology works wherever you need to make thoughtful decisions.

---

## Quick Start

### Installation

```bash
# Add to Amplifier (works with any bundle)
amplifier bundle add git+https://github.com/anderlpz/amplifier-bundle-design-intelligence-enhanced@main --app

# Set as active bundle (optional)
amplifier bundle use design-intelligence-enhanced

# Start session
amplifier
```

### Your First Creative Research Session

**For visual/product work:**
```
"I need to design a dashboard showing system health. 
Help me research how other domains handle rapid anomaly detection."
```

**For engineering work:**
```
"I'm designing a rate limiting system for our API.
Research analogous fairness problems in other domains."
```

**For strategy work:**
```
"We need to optimize our deployment process.
Find patterns from how other domains handle coordination under constraints."
```

The agents will:
1. Detect your domain (visual/engineering/strategy)
2. Decompose the problem into core challenges
3. Research analogous solutions across domains
4. Extract L3-4 principles (not just surface patterns)
5. Help you synthesize a purposeful solution

---

## What's Included

### Discovery (Structured Interviewing)

Captures what matters through systematic questioning:
- **Visual/Product**: Cognitive tasks, decision points, emotional context
- **Engineering**: System guarantees, failure modes, trade-offs
- **Strategy**: Coordination needs, resource constraints, optimization targets

**Output:** Problem decomposition with clear understanding of what you're solving

### Research (Cross-Domain Intelligence)

On-demand research using creative methodology:
- **Analogous domain mapping**: Find similar problems in unexpected fields
- **Pattern extraction**: Identify L3-4 principles (why solutions work)
- **Trend awareness**: Current best practices (weekly scrapes of Awwwards, Siteinspire, The FWA for visual design)

**Output:** Research context with cross-domain patterns and principles

### Design Agents (Specialized Expertise)

8 specialized agents applying rigorous frameworks:

| Agent | Domain Focus | Use For |
|-------|--------------|---------|
| **research-analyst** | Cross-domain research | Problem decomposition, analogous domain research |
| **art-director** | Visual strategy | Aesthetic direction, visual coherence |
| **design-system-architect** | System architecture | Tokens, patterns, foundations |
| **component-designer** | Component design | Individual UI elements, variants |
| **layout-architect** | Spatial composition | Page structure, grids, IA |
| **animation-choreographer** | Motion design | Timing, transitions, feedback |
| **responsive-strategist** | Adaptation strategy | Breakpoints, multi-device patterns |
| **voice-strategist** | Communication strategy | Tone, messaging, microcopy |

**Frameworks applied:**
- **Nine Dimensions** (visual work): Style, Motion, Voice, Space, Color, Typography, Proportion, Texture, Body
- **Five Pillars** (all domains): Purpose, Craft, Constraints, Incompleteness, Humans

### Verification (Visual Validation)

Prevent circular fix loops with visual verification:
- **visual-verify**: Screenshot capture and comparison
- **layout-context**: Computed layout extraction
- **design-validate**: Systematic validation against specs
- **design-validator agent**: Orchestrates verification workflow

**Requires:** Playwright (`pip install playwright && playwright install chromium`)

**Use when:** Verifying live implementations, validating against specifications

---

## Example Workflows

### Engineering: API Rate Limiting

```
> "I'm designing rate limiting for our API. It needs to be fair, prevent abuse, 
   but not block legitimate heavy users."

→ Research analyst detects engineering domain
→ Decomposes into: fairness under load, abuse prevention, graceful degradation
→ Maps to analogous domains: highway traffic management, electrical grid load balancing, 
  network QoS
→ Extracts L3-4 principles: token buckets, priority queues, backpressure signals
→ Synthesizes: Adaptive rate limiting with client reputation scoring
```

### Visual: Dashboard Design

```
> "Design a monitoring dashboard for DevOps teams. They need to spot anomalies 
   fast during incidents."

→ Research analyst detects visual/product domain
→ Decomposes cognitive tasks: rapid gestalt assessment, anomaly detection, 
  drill-down investigation
→ Maps to analogous domains: air traffic control, medical monitoring, financial trading
→ Extracts L3-4 principles: alert hierarchy, gestalt patterns, progressive disclosure
→ Art director + layout architect synthesize: Dashboard with alert-driven hierarchy 
  and contextual drill-down
```

### Strategy: Process Optimization

```
> "We need to optimize our code review process. Reviews are slow and creating 
   bottlenecks."

→ Research analyst detects strategy/operations domain
→ Decomposes: coordination challenge, resource allocation, quality vs speed trade-off
→ Maps to analogous domains: manufacturing flow, emergency triage, agile sprints
→ Extracts L3-4 principles: WIP limits, priority systems, parallel paths
→ Synthesizes: Tiered review system with automated pre-checks and fast-path for 
  low-risk changes
```

---

## Recipes

| Recipe | What It Does |
|--------|--------------|
| `design-discovery` | Full discovery → research → design direction workflow |
| `weekly-design-scrape` | Automated visual trend research (Awwwards, Siteinspire, The FWA) |

**Run a recipe:**
```
"Run the design-discovery recipe for a healthcare monitoring system"
```

---

## Philosophy

This bundle follows Amplifier's principles and adds creative research methodology:

- **Decompose before design** — Understand the problem deeply first
- **Research cross-domain** — Analogous solutions reveal universal principles
- **Extract L3-4 principles** — Not what works, but WHY it works
- **Synthesize with reasoning** — Apply patterns thoughtfully to your context
- **Design is universal** — Purpose and intention matter in every domain

**Design is not decoration.** It's the thoughtful consideration of purpose, constraints, and humans that makes systems work well.

---

## Who It's For

**Engineers who think deeply** — You want your systems to be purposeful, not just functional. You research before building.

**Builders with vision** — You know what you want but need help articulating it, researching proven patterns, and refining your approach.

**Teams making critical decisions** — You need a structured way to explore options, research best practices, and make informed choices.

**Anyone solving novel problems** — You need to synthesize solutions from proven patterns across domains, not reinvent from scratch.

---

## Documentation

- **[Creative Research Methodology](context/research-methodology/creative-research-methodology.md)** — The full methodology with examples
- **[Cognitive Task Catalog](context/research-methodology/cognitive-task-catalog.md)** — Library of decomposed problems
- **[Engineering Examples](context/examples/engineering-examples.md)** — Complete engineering walkthroughs
- **[Verification Guide](VERIFICATION_GUIDE.md)** — Visual verification setup and usage
- **[Quick Workflow](docs/WORKFLOW.md)** — Step-by-step guide

---

## Roadmap

| Phase | Status | What |
|-------|--------|------|
| **2.0 Foundation** | ✅ Complete | Discovery integration, research capability, design agents |
| **2.1 Verification** | ✅ Complete | Visual verification tools, validation workflow |
| **2.2 Universalization** | ✅ Complete | Engineering/product/strategy support, domain detection |
| **2.3 Generation** | 🔄 In Progress | Design Protocol spec, token generation, artifact export |
| **3.0 Feedback** | ⏳ Planned | Validation loops, taste refinement, continuous improvement |

---

## Naming Note

This bundle is named **design-intelligence-enhanced** to distinguish it from Microsoft's official `design-intelligence` bundle.

**Why "enhanced"?**
- Includes all design-intelligence capabilities
- Adds visual verification tools (v2.1.0)
- Expands to universal applicability (v2.2.0)
- Community-maintained enhancements

**Installation uses the enhanced name:**
```bash
amplifier bundle add git+https://github.com/anderlpz/amplifier-bundle-design-intelligence-enhanced@main --app
amplifier bundle use design-intelligence-enhanced
```

---

## Contributing

This project is an enhanced fork maintained independently. For the official Microsoft design-intelligence bundle, see [microsoft/amplifier-bundle-design-intelligence](https://github.com/microsoft/amplifier-bundle-design-intelligence).

**Philosophy contributions welcome:** If you discover new cross-domain patterns, L3-4 principles, or cognitive task decompositions, we'd love to learn from your research.

---

## License

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).

**Note:** This is an enhanced community fork. See LICENSE for details.
