---
bundle:
  name: design-intelligence
  version: 1.0.0
  description: Comprehensive design intelligence capability with specialized agents and knowledge base

includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  - bundle: design-intelligence:behaviors/design-intelligence
  - bundle: design-intelligence:behaviors/design-research
---

# Design Intelligence

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
