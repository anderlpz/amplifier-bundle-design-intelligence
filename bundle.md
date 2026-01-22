---
bundle:
  name: design-studio
  version: 2.1.0
  description: Design intelligence that discovers, thinks, and generates with visual verification
  sub_bundles:
    - name: advisory
      path: behaviors/design-intelligence.yaml
      description: 7 specialized design agents (art-director, component-designer, etc.)
    - name: research
      path: behaviors/design-research.yaml
      description: Design trend research and analysis capabilities
    - name: generation
      path: behaviors/design-generation.yaml
      description: Token generator, spec writer, export packager
    - name: verification
      description: Visual verification tools (visual-verify, layout-context, design-validate, design-validator agent)

includes:
  # Standalone app bundle - includes foundation for full capabilities
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  - bundle: git+https://github.com/anderlpz/amplifier-bundle-discovery@main
  - bundle: git+https://github.com/anderlpz/amplifier-bundle-design-verification@main
  - bundle: design-studio:behaviors/design-intelligence
  - bundle: design-studio:behaviors/design-research
  - bundle: design-studio:behaviors/design-generation
---

# Design Intelligence

> Design intelligence that discovers, thinks, and generates.

**What it does:** A complete design-to-implementation pipeline that captures intent, applies design thinking, and produces artifacts coding agents can consume.

## Quick Start

| Goal | Command |
|------|---------|
| **Discover requirements** | `"Help me discover the design for [project]"` |
| **Research inspiration** | `"Find design inspiration for [context]"` |
| **Update trend research** | `"Update my research"` (takes ~2 hours) |
| **Analyze a site** | `"Look at [URL] and analyze [aspect]"` |
| **Verify design work** | `"Use design-validator to verify [component]"` |
| **Full workflow** | Run `design-discovery` recipe |

## Design Research

Vision-analyzed trend research from **Awwwards**, **Siteinspire**, and **The FWA**.

**What you get:** ~35 real projects with full-page screenshots + AI vision analysis

**When to update:**
- Starting a new project (fresh inspiration)
- Weekly design reviews (stay current)
- Before presentations (latest trends)

**How to update:** Just say `"Update my research"` (~105 min to scrape & analyze)

Research updates on **your schedule**, not ours. No guilt about stale data.

## The Workflow

```
1. DISCOVER → What are we building and why?
2. RESEARCH → What's out there? What's current?
3. DESIGN   → What should it be?
4. VERIFY   → Does it match the spec? (NEW in 2.1.0)
5. GENERATE → Produce artifacts for implementation
```

### NEW: Visual Verification (v2.1.0)

**Prevents circular fix loops** by letting design agents see what they built before presenting to you.

- **visual-verify** - Capture screenshots and compare against baseline
- **layout-context** - Extract computed layout information for alignment analysis
- **design-validate** - Systematically validate against specifications
- **design-validator agent** - Orchestrates verification workflow

**Before:** 7 commits over 2 days, you become QA tester  
**After:** One-shot fixes with screenshot evidence, you approve on first presentation

---

@design-studio:context/design-instructions.md

---

## Recipes

| Recipe | What It Does |
|--------|--------------|
| `design-to-implementation` | **Full pipeline:** idea → discovery → design → tokens → export |
| `design-discovery` | Discovery → research → design direction |
| `design-system-export` | Generate tokens + component specs + export package |
| `weekly-design-scrape` | Update trend research (Awwwards, Siteinspire, The FWA) |

**Run a recipe:**
```
Run the design-to-implementation recipe for [describe your project]
```

---

## Design Philosophy

@design-studio:context/philosophy/DESIGN-PHILOSOPHY.md
@design-studio:context/philosophy/DESIGN-PRINCIPLES.md
@design-studio:context/philosophy/DESIGN-FRAMEWORK.md

---

@foundation:context/shared/common-system-base.md
