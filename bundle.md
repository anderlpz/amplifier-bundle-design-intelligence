---
bundle:
  name: design-intelligence
  version: 2.0.0
  description: Design intelligence that discovers, thinks, and generates

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  - bundle: git+https://github.com/anderlpz/amplifier-bundle-discovery@main
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

## Recipes (Requires recipes bundle)

Automated design research workflows:

| Recipe | Description |
|--------|-------------|
| `recipes/weekly-design-scrape.yaml` | Scrapes Awwwards/Siteinspire, analyzes with vision AI, updates archive |

**To run recipes:** Use a bundle that includes `amplifier-bundle-recipes`, then:

```
execute design-intelligence:recipes/weekly-design-scrape.yaml with year=2026 month=01 month_name=january date=2026-01-13
```

Or via CLI:
```bash
amplifier tool invoke recipes \
  operation=execute \
  recipe_path=design-intelligence:recipes/weekly-design-scrape.yaml \
  context='{"year": "2026", "month": "01", "month_name": "january", "date": "2026-01-13"}'
```

---

## Design Philosophy

@design-intelligence:context/philosophy/DESIGN-PHILOSOPHY.md
@design-intelligence:context/philosophy/DESIGN-PRINCIPLES.md
@design-intelligence:context/philosophy/DESIGN-FRAMEWORK.md

---

@foundation:context/shared/common-system-base.md
