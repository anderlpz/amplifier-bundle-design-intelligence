# Design Intelligence Evolution Plan

**Status:** Draft  
**Created:** 2026-01-16  
**Goal:** Transform Design Intelligence from advisory-only to a complete design-to-implementation pipeline

---

## Executive Summary

Design Intelligence needs to evolve from **advice** to **artifacts**. This plan integrates:

1. **Discovery Bundle** - General-purpose requirements gathering (already built)
2. **Design Intelligence** - Design-specific thinking, research, and generation
3. **Design Protocol** - Standard artifact format for coding agents (like A2UI for design)
4. **Clear Packaging** - Communication improvements from Design OS

---

## The Vision

```
┌─────────────────────────────────────────────────────────────────────┐
│  1. DISCOVER (discovery bundle)                                      │
│     "What are we building and why?"                                 │
│     General-purpose • 4-layer methodology • Readiness gates         │
│     Output: Discovery Brief                                         │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│  2. RESEARCH (design-intelligence)                                   │
│     "What's out there? What's current?"                             │
│     Trend scraping • URL analysis • Inspiration gathering           │
│     Output: Research Context                                        │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│  3. DESIGN (design-intelligence)                                     │
│     "What should it be?"                                            │
│     Nine Dimensions • Philosophy • Context-aware thinking           │
│     Output: Design Decisions                                        │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│  4. GENERATE (design-intelligence + protocol)                        │
│     "Produce artifacts for implementation"                          │
│     Tokens • Specs • Components • Export packages                   │
│     Output: Design Protocol Artifacts                               │
└─────────────────────────────────────────────────────────────────────┘
                              ↓
┌─────────────────────────────────────────────────────────────────────┐
│  5. IMPLEMENT (coding agents)                                        │
│     Claude Code • Cursor • Copilot • Any agent                      │
│     Consumes protocol artifacts                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Phase 1: Foundation (Week 1-2)

### 1.1 Include Discovery Bundle

**Action:** Add discovery bundle as upstream dependency

```yaml
# design-intelligence/bundle.md
includes:
  - bundle: git+https://github.com/microsoft/amplifier-foundation@main
  - bundle: git+https://github.com/anderlpz/amplifier-bundle-discovery@main
  - bundle: design-intelligence:behaviors/design-core.yaml
  - bundle: design-intelligence:behaviors/design-research.yaml
```

**Why:** Discovery provides the "what are we building" layer. DI should not rebuild this.

### 1.2 Create Design Discovery Recipe

**Action:** Create recipe that connects discovery → design thinking

```yaml
# design-intelligence/recipes/design-discovery.yaml
name: design-discovery
description: Full discovery-to-design workflow

steps:
  - id: discover
    agent: discovery:discovery-interviewer
    prompt: |
      Conduct design discovery for: {{project_description}}
      Focus on visual/experiential aspects.

  - id: research
    agent: design-intelligence:research-runner
    prompt: |
      Based on this discovery brief, find relevant design inspiration:
      {{steps.discover.result}}

  - id: synthesize
    agent: design-intelligence:art-director
    prompt: |
      Synthesize discovery and research into design direction:
      
      Discovery: {{steps.discover.result}}
      Research: {{steps.research.result}}
```

### 1.3 Package Communication (Design OS Lessons)

**Action:** Create clear entry point documentation

| Need | Create |
|------|--------|
| One-liner | "Design intelligence that discovers, thinks, and generates" |
| Simple workflow | 4 numbered steps with clear entry points |
| Quick reference | "If you want X, do Y" table |
| Who it's for | Target user descriptions |

**Files to create:**
- `docs/QUICK-START.md` - 5-minute intro
- `docs/WORKFLOW.md` - Step-by-step guide
- `README.md` update - Clear value proposition

---

## Phase 2: Generation (Week 2-3)

### 2.1 Define Design Protocol Spec

**Action:** Create specification for design artifacts

```
design-intelligence/specs/
├── DESIGN-PROTOCOL.md           # Overall specification
├── schemas/
│   ├── design-brief.schema.json # Discovery output
│   ├── tokens.schema.json       # Design tokens
│   ├── components.schema.json   # Component specs
│   └── system.schema.json       # Full system export
└── examples/
    ├── minimal-tokens.json
    ├── full-system.json
    └── component-spec.json
```

**Design Protocol Principles (from A2UI):**
- Declarative, not executable
- Framework-agnostic
- LLM-friendly (flat, streaming-capable)
- Progressively renderable

### 2.2 Token Generation

**Schema: `tokens.schema.json`**

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "title": "Design Tokens",
  "type": "object",
  "properties": {
    "meta": {
      "type": "object",
      "properties": {
        "name": { "type": "string" },
        "version": { "type": "string" },
        "generated": { "type": "string", "format": "date-time" },
        "source": { "type": "string", "description": "discovery brief reference" }
      }
    },
    "color": {
      "type": "object",
      "properties": {
        "primary": { "$ref": "#/$defs/colorToken" },
        "secondary": { "$ref": "#/$defs/colorToken" },
        "neutral": { "$ref": "#/$defs/colorScale" },
        "semantic": {
          "type": "object",
          "properties": {
            "success": { "$ref": "#/$defs/colorToken" },
            "warning": { "$ref": "#/$defs/colorToken" },
            "error": { "$ref": "#/$defs/colorToken" },
            "info": { "$ref": "#/$defs/colorToken" }
          }
        }
      }
    },
    "typography": {
      "type": "object",
      "properties": {
        "families": {
          "type": "object",
          "properties": {
            "heading": { "$ref": "#/$defs/fontFamily" },
            "body": { "$ref": "#/$defs/fontFamily" },
            "mono": { "$ref": "#/$defs/fontFamily" }
          }
        },
        "scale": { "$ref": "#/$defs/typeScale" }
      }
    },
    "spacing": {
      "type": "object",
      "properties": {
        "base": { "type": "string" },
        "scale": { "type": "array", "items": { "type": "string" } }
      }
    },
    "motion": {
      "type": "object",
      "properties": {
        "duration": { "$ref": "#/$defs/durationScale" },
        "easing": { "$ref": "#/$defs/easingTokens" }
      }
    }
  }
}
```

### 2.3 Add Generation Agent

**Action:** Create `token-generator` agent

```markdown
# design-intelligence/agents/token-generator.md
---
meta:
  name: token-generator
  description: Generates design tokens from discovery context
---

You generate Design Protocol-compliant token files from discovery briefs
and design decisions.

## Inputs
- Discovery brief (from discovery:discovery-interviewer)
- Design direction (from art-director)
- Research context (from research-runner) [optional]

## Outputs
- `tokens.json` - Design Protocol compliant
- `tokens.css` - CSS custom properties
- `tokens.tailwind.js` - Tailwind config
- `tokens.scss` - SCSS variables

## Generation Rules
[Rules for translating design decisions to tokens]
```

### 2.4 Add Spec Writer Agent

**Action:** Create `spec-writer` agent

```markdown
# design-intelligence/agents/spec-writer.md
---
meta:
  name: spec-writer
  description: Writes component specifications from design decisions
---

You write Design Protocol-compliant component specifications.

## Output Format
Each component spec includes:
- Purpose and usage
- Variants and states
- Props/API
- Accessibility requirements
- Behavior specifications
- Visual specifications (referencing tokens)
```

---

## Phase 3: Export & Handoff (Week 3-4)

### 3.1 Create Export Package Generator

**Action:** Recipe that produces complete handoff

```yaml
# design-intelligence/recipes/design-system-export.yaml
name: design-system-export
description: Generate complete design system export package

steps:
  - id: tokens
    agent: design-intelligence:token-generator
    prompt: "Generate tokens from: {{design_context}}"

  - id: components
    agent: design-intelligence:spec-writer
    prompt: "Write component specs for: {{component_list}}"

  - id: package
    agent: design-intelligence:export-packager
    prompt: |
      Create export package:
      - tokens: {{steps.tokens.result}}
      - components: {{steps.components.result}}
      - format: {{export_format}}
```

### 3.2 Export Formats

| Format | Output | Use Case |
|--------|--------|----------|
| **Tailwind** | `tailwind.config.js` + components | Tailwind projects |
| **CSS Variables** | `tokens.css` + component CSS | Vanilla/any framework |
| **Style Dictionary** | SD config + transforms | Design tooling |
| **Figma Tokens** | JSON for Figma plugins | Designer handoff |
| **Coding Agent** | Prompts + instructions | Claude Code, Cursor |

### 3.3 Coding Agent Handoff

**Action:** Generate prompts for coding agents (like Design OS)

```markdown
# Export: product-design/prompts/implementation-prompt.md

## Design System Implementation

Use these artifacts to implement the design system:

### Tokens
[Link to tokens.json]

### Components to Build
1. Button - [link to spec]
2. Card - [link to spec]
3. Form inputs - [link to spec]

### Implementation Order
1. Set up token infrastructure
2. Build primitive components
3. Build composite components
4. Apply to pages

### Constraints
- All colors must use token references
- Typography must follow the scale
- Spacing must use the spacing scale
- Motion must use defined easings
```

---

## Phase 4: Feedback Loop (Week 4+)

### 4.1 Validation Agent

**Action:** Create agent that validates implementation against protocol

```markdown
# design-intelligence/agents/design-validator.md
---
meta:
  name: design-validator
  description: Validates implementations against Design Protocol specs
---

You validate that implementations match the design system specification.

## Checks
- Token usage (are all colors from tokens?)
- Typography compliance (following scale?)
- Spacing compliance (using spacing scale?)
- Component structure (matching specs?)
- Accessibility (meeting requirements?)

## Output
- Compliance score
- Specific violations
- Remediation suggestions
```

### 4.2 Taste Refinement (from Embody)

**Action:** Add feedback-based generation tuning

```yaml
# design-intelligence/recipes/taste-refinement.yaml
name: taste-refinement
description: Refine design direction through feedback

steps:
  - id: generate-variations
    agent: design-intelligence:variation-generator
    prompt: "Generate 4 design directions for: {{context}}"

  - id: gather-feedback
    approval: true
    prompt: |
      Review these 4 directions:
      {{steps.generate-variations.result}}
      
      Rate each: 👍 (more like this) / 👎 (not this direction) / 👁️ (interesting)

  - id: refine
    agent: design-intelligence:art-director
    prompt: |
      Based on feedback, refine the direction:
      Liked: {{feedback.liked}}
      Disliked: {{feedback.disliked}}
      Interesting: {{feedback.interesting}}
```

---

## File Structure (Target State)

```
amplifier-bundle-design-intelligence/
├── bundle.md                           # Main bundle (includes discovery)
├── README.md                           # Clear value prop, quick start
│
├── docs/
│   ├── QUICK-START.md                  # 5-minute intro
│   ├── WORKFLOW.md                     # Step-by-step guide
│   ├── DESIGN-PROTOCOL.md              # Protocol specification
│   └── EVOLUTION-PLAN.md               # This document
│
├── specs/
│   └── schemas/
│       ├── tokens.schema.json
│       ├── components.schema.json
│       └── system.schema.json
│
├── agents/
│   ├── [existing 7 advisory agents]
│   ├── token-generator.md              # NEW: Generates tokens
│   ├── spec-writer.md                  # NEW: Writes component specs
│   ├── export-packager.md              # NEW: Creates export packages
│   ├── design-validator.md             # NEW: Validates implementations
│   └── variation-generator.md          # NEW: Generates variations for feedback
│
├── behaviors/
│   ├── design-core.yaml                # Core design philosophy
│   ├── design-research.yaml            # Research capability
│   └── design-generation.yaml          # NEW: Generation capability
│
├── recipes/
│   ├── weekly-design-scrape.yaml       # Existing
│   ├── design-discovery.yaml           # NEW: Discovery → Design
│   ├── design-system-export.yaml       # NEW: Full export workflow
│   └── taste-refinement.yaml           # NEW: Feedback-based refinement
│
├── context/
│   ├── [existing context files]
│   ├── generation-protocols.md         # NEW: How to generate artifacts
│   └── design-protocol-guide.md        # NEW: Protocol usage guide
│
└── archive/                            # Research archive (existing)
```

---

## Success Metrics

### Quantitative
- Discovery → Tokens in <10 exchanges
- Export package generation in <5 minutes
- Implementation compliance score >90%

### Qualitative
- "I got a complete design system, not just advice"
- "The tokens worked directly in my codebase"
- "Coding agents understood the specs perfectly"

---

## Dependencies

| Dependency | Status | Action |
|------------|--------|--------|
| Discovery bundle | ✅ Built | Include as upstream |
| Research capability | ✅ Built | Enhance with context capture |
| Advisory agents | ✅ Built | Keep as-is |
| Generation agents | ❌ Missing | Build (Phase 2) |
| Design Protocol spec | ❌ Missing | Define (Phase 2) |
| Export capability | ❌ Missing | Build (Phase 3) |
| Validation | ❌ Missing | Build (Phase 4) |

---

## Risk Mitigation

| Risk | Mitigation |
|------|------------|
| Protocol too complex | Start minimal, iterate based on usage |
| Generation quality | Use existing knowledge bases, add examples |
| Framework compatibility | Test with Tailwind, CSS, and one other |
| Scope creep | Ship Phase 1-2, validate, then Phase 3-4 |

---

## Next Steps

1. **Immediate:** Include discovery bundle in DI
2. **This week:** Create design-discovery recipe
3. **Next week:** Define Design Protocol spec (minimal)
4. **Week 3:** Build token-generator agent
5. **Week 4:** Create export package recipe

---

## References

- [Discovery Bundle](https://github.com/anderlpz/amplifier-bundle-discovery)
- [Design OS](https://github.com/buildermethods/design-os) - Inspiration for packaging
- [A2UI Protocol](https://a2ui.org) - Inspiration for protocol design
- [Embody](../../../amplifier-embody/) - Taste/generator philosophy
- [Studious](../../../amplifier-studious/) - Multimodal discovery vision
