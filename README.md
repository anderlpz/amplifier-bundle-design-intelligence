# Design Intelligence

> **Design intelligence that discovers, thinks, and generates.**

The missing design layer between your idea and your codebase. Design Intelligence captures intent through structured discovery, applies design thinking with current trends, and produces artifacts that coding agents can implement.

---

## The Problem

AI coding tools build fast, but design results often miss the mark. You describe what you want, the agent builds *something*, but it looks generic or doesn't match your vision.

**The core issue:** We're asking coding agents to figure out *what to design* and *build it* simultaneously. Design decisions get made on the fly, buried in code, impossible to adjust.

---

## The Solution

Design Intelligence provides a complete design pipeline:

```
1. DISCOVER  →  What are we building and why?
2. RESEARCH  →  What's out there? What's current?
3. DESIGN    →  What should it be?
4. VERIFY    →  Does it match the spec? (NEW in v2.1.0)
5. GENERATE  →  Produce artifacts for implementation
```

Each step builds on the previous. You + AI work through structured conversations. The output: design artifacts that any coding agent can implement consistently.

**NEW in v2.1.0:** Visual verification prevents circular fix loops by letting design agents see what they built before presenting to you.

---

## Quick Start

### If You Want To...

| Goal | What to Say |
|------|-------------|
| **Discover requirements** | "Help me discover the design for [project]" |
| **Find inspiration** | "Find design inspiration for [context]" |
| **Analyze a site** | "Look at [URL] and analyze the [aspect]" |
| **Get design direction** | "What aesthetic direction fits [description]?" |
| **Full workflow** | "Run the design-discovery recipe for [project]" |

### Installation

**Add design intelligence to any session** (recommended):

```bash
# Install as an app - layers on top of your current bundle
amplifier bundle add git+https://github.com/anderlpz/amplifier-bundle-design-intelligence@main --app

# All 8 design agents are now available in your session
amplifier
```

**Alternative: Use standalone**

```bash
# Set as your active bundle
amplifier bundle add git+https://github.com/anderlpz/amplifier-bundle-design-intelligence@main
amplifier bundle use design-intelligence
amplifier
```

**Alternative: Include in your bundle**

```yaml
# Your bundle.md
includes:
  - bundle: git+https://github.com/anderlpz/amplifier-bundle-design-intelligence@main
```

### Setup for Verification (Recommended)

Visual verification prevents circular fix loops by letting design agents see what they built before presenting to you.

```bash
# One-time setup (if not already installed)
pip install playwright
playwright install chromium
```

**When you need it:** Verifying live implementations, component validation, layout debugging

**Skip if:** Only doing discovery/research or creating specs for others to implement

**How it works:** Agents capture screenshots, analyze layout, and validate against specifications before presenting results. See [VERIFICATION_GUIDE.md](VERIFICATION_GUIDE.md) for details.



---

## What's Included

### Discovery (via Discovery Bundle)

Structured interviewing that captures:
- Purpose and intent
- Visual/experiential expression
- Context and appropriateness
- Adaptive considerations

**Output:** Discovery Brief

### Research

Continuous design trend monitoring:
- Weekly scrapes of Awwwards, Siteinspire, The FWA
- Vision AI analysis of award-winning sites
- Searchable archive by category, style, technique
- On-demand URL analysis

**Output:** Research Context

### Design Thinking

7 specialized agents applying:
- **Nine Dimensions** - Style, Motion, Voice, Space, Color, Typography, Proportion, Texture, Body
- **Five Pillars** - Purpose, Craft, Constraints, Incompleteness, Humans
- **Current trends** - What's working now, not 3 years ago

**Output:** Design Direction

### Verification (NEW in v2.1.0)

Visual verification tools that prevent circular fix loops:
- **visual-verify** - Screenshot capture and comparison
- **layout-context** - Computed layout extraction and analysis
- **design-validate** - Systematic validation against specifications
- **design-validator agent** - Orchestrates verification workflow

**Output:** Validated designs with screenshot evidence

**How it works:** Before presenting design work, agents verify visually, analyze layout, and validate against specs. You see working solutions on first presentation instead of becoming a QA tester.

### Generation (Coming Soon)

Produce artifacts coding agents understand:
- Design tokens (colors, typography, spacing, motion)
- Component specifications
- Export packages with implementation prompts

**Output:** Design Protocol artifacts

---

## Agents

| Agent | Expertise | Use For |
|-------|-----------|---------|
| **art-director** | Aesthetic strategy, visual coherence | Overall direction, style decisions |
| **design-system-architect** | Tokens, patterns, architecture | System-wide foundations |
| **component-designer** | Individual components, variants | Specific UI elements |
| **layout-architect** | Page structure, grids, IA | Page-level composition |
| **animation-choreographer** | Motion, timing, transitions | Movement and feedback |
| **responsive-strategist** | Breakpoints, adaptation | Multi-device strategy |
| **voice-strategist** | Tone, messaging, microcopy | Content and personality |
| **design-validator** | Visual verification, validation | Verify implementations before delivery (requires Playwright) |

---

## Recipes

| Recipe | What It Does |
|--------|--------------|
| `design-discovery` | Full discovery → research → design direction workflow |
| `weekly-design-scrape` | Automated trend research (Awwwards, Siteinspire) |

**Run a recipe:**
```
"Run the design-discovery recipe for a healthcare dashboard"
```

---

## Who It's For

**Builders with design vision** — You know what you want but need help articulating it, refining it, and turning it into something coding agents can build.

**Developers who aren't designers** — You need design guidance that goes beyond "make it look good" and produces consistent, implementable results.

**Teams without dedicated designers** — You need design intelligence embedded in your development workflow, not a separate handoff process.

---

## Philosophy

Design Intelligence follows Amplifier's principles:

- **Discover before design** — Capture intent, don't assume it
- **Think before generate** — Apply frameworks, not just taste
- **Generate for implementation** — Produce artifacts, not just advice
- **Stay current** — Research what works now, not what worked years ago

---

## Roadmap

| Phase | Status | What |
|-------|--------|------|
| **1. Foundation** | ✅ Complete | Discovery integration, research capability |
| **2. Generation** | 🔄 In Progress | Design Protocol spec, token generation |
| **3. Export** | ⏳ Planned | Handoff packages for coding agents |
| **4. Feedback** | ⏳ Planned | Validation, taste refinement |

See `docs/EVOLUTION-PLAN.md` for details.

---

## Resources

- **[Quick Workflow](docs/WORKFLOW.md)** — Step-by-step guide
- **[Evolution Plan](docs/EVOLUTION-PLAN.md)** — Where we're headed
- **[Design Philosophy](context/philosophy/)** — The thinking behind the design

---

## Contributing

> [!NOTE]
> This project is not currently accepting external contributions, but we're actively working toward opening this up.

Most contributions require a Contributor License Agreement (CLA). For details, visit [Contributor License Agreements](https://cla.opensource.microsoft.com).

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to [Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/legal/intellectualproperty/trademarks/usage/general).
