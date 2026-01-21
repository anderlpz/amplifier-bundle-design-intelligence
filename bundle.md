---
bundle:
  name: design-intelligence
  version: 2.0.0
  description: Design intelligence that discovers, thinks, and generates
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

includes:
  # Note: This bundle is designed to be included BY foundation (which provides discovery)
  # Do not add foundation or discovery here - it creates circular dependencies
  - bundle: design-intelligence:behaviors/design-intelligence
  - bundle: design-intelligence:behaviors/design-research
  - bundle: design-intelligence:behaviors/design-generation
---

# Design Intelligence

> Design intelligence that discovers, thinks, and generates.

**What it does:** A complete design-to-implementation pipeline that captures intent, applies design thinking, and produces artifacts coding agents can consume.

## Quick Start

| Goal | Command |
|------|---------|
| **Discover requirements** | `"Help me discover the design for [project]"` |
| **Research inspiration** | `"Find design inspiration for [context]"` |
| **Analyze a site** | `"Look at [URL] and analyze [aspect]"` |
| **Full workflow** | Run `design-discovery` recipe |

## The Workflow

```
1. DISCOVER → What are we building and why?
2. RESEARCH → What's out there? What's current?
3. DESIGN   → What should it be?
4. GENERATE → Produce artifacts for implementation
```

---

@design-intelligence:context/design-instructions.md

---

## Recipes

| Recipe | What It Does |
|--------|--------------|
| `design-to-implementation` | **Full pipeline:** idea → discovery → design → tokens → export |
| `design-discovery` | Discovery → research → design direction |
| `design-system-export` | Generate tokens + component specs + export package |
| `weekly-design-scrape` | Automated trend research from Awwwards/Siteinspire |

**Run a recipe:**
```
Run the design-to-implementation recipe for [describe your project]
```

---

## Design Philosophy

@design-intelligence:context/philosophy/DESIGN-PHILOSOPHY.md
@design-intelligence:context/philosophy/DESIGN-PRINCIPLES.md
@design-intelligence:context/philosophy/DESIGN-FRAMEWORK.md

---

@foundation:context/shared/common-system-base.md
