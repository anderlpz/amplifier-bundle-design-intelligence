# Visual Verification Guide

> **Prevent circular fix loops by letting design agents see what they built before presenting to you.**

---

## The Problem

**Without verification:**
```
Agent: "I've centered the cards"
You: *rebuilds and checks*
You: "Still offset"
Agent: "Let me try again..."
[Repeat 7 times over 2 days]
```

**Root cause:** Agents modify CSS/HTML they cannot observe, causing circular fix loops with you as the QA tester.

---

## The Solution

**With verification (v2.1.0):**
```
Agent: "I'll verify this visually first"
[Agent loops internally until passing]
Agent: "✅ Validation PASSED - here's the screenshot"
You: "Perfect!" [Approves immediately]
```

**Impact:**
- ✅ One-shot fixes instead of 7-iteration loops
- ✅ Evidence-based approvals (screenshots, not promises)
- ✅ Trust restored ("When agents say it works, it works")
- ✅ Momentum maintained (no frustration from broken attempts)

---

## Setup

### Prerequisites

1. **Playwright installed:**
   ```bash
   pip install playwright
   playwright install chromium
   ```

2. **Dev server running:**
   ```bash
   cd your-project
   npm run dev  # or yarn dev, vite, etc.
   ```
   Note the URL (e.g., `http://localhost:5173`)

3. **Component implemented:**
   Verification requires a live implementation to capture and analyze.

### When You Need It

✅ **Use verification for:**
- Verifying live implementations
- Component validation
- Layout debugging
- Visual regression testing

❌ **Skip verification for:**
- Discovery and requirements capture
- Research and inspiration gathering
- Creating specs for others to implement
- Token generation without implementation

---

## The Tools

### 1. visual-verify

**What it does:** Captures screenshots and compares against baseline

**Use for:** Seeing what you built, catching visual regressions

```
"Use visual-verify on the card component at .start-recents"
```

**Returns:**
- Screenshot of current state
- Baseline comparison (if exists)
- Pixel diff highlighting changes
- Observations about alignment, layout, appearance

**Performance:** ~7-12 seconds

---

### 2. layout-context

**What it does:** Extracts computed layout information invisible when reading CSS

**Use for:** Understanding why elements don't align, debugging layout issues

```
"Use layout-context on .start-recents to analyze alignment"
```

**Returns:**
- Actual rendered dimensions (not authored CSS)
- Parent/sibling relationships
- Warnings about misalignment
- Actionable recommendations

**Performance:** ~3-5 seconds

---

### 3. design-validate

**What it does:** Systematically validates against specification criteria

**Use for:** Proving implementation meets design specification

```
"Use design-validate to check if the cards meet the spec"
```

**Returns:**
- PASS/FAIL verdict
- Score per criterion
- Blockers preventing approval
- Recommendations for fixes

**Performance:** ~5-10 seconds

**Requires:** Design specification with criteria (see Spec Format below)

---

## The Agent: design-validator

**Orchestrates the complete verification workflow with quality gates.**

### What It Does

1. **Receives design specification** from you
2. **Delegates implementation** to component-designer (if needed)
3. **Runs verification tools:**
   - visual-verify (screenshots)
   - layout-context (alignment analysis)
   - design-validate (spec compliance)
4. **Loops until PASS** - Agents don't present until validation passes
5. **Presents evidence package** - Screenshot + analysis + validation report

### How to Use It

```
"Use design-validator to verify the Recent Cards component"
```

**With a spec file:**
```
"Use design-validator with RECENT_CARDS_SPEC.md to verify the implementation"
```

**The workflow:**
```
You → design-validator
     ↓
     component-designer (implements/fixes)
     ↓
     visual-verify (screenshot)
     ↓
     layout-context (alignment check)
     ↓
     design-validate (spec compliance)
     ↓
     [Loop if FAIL, present if PASS]
     ↓
You ← Evidence package (screenshot + report)
```

---

## Spec Format

Design specifications should use YAML frontmatter with markdown criteria:

```markdown
---
spec:
  component: Recent Cards
  version: 1.0.0
  selector: .start-recents
  url: http://localhost:5173

criteria:
  - name: Centering
    description: Cards container is centered on the page
    type: layout
    
  - name: Gap
    description: 12px gap between cards
    type: spacing
    
  - name: Alignment
    description: Cards are horizontally aligned
    type: layout
---

# Recent Cards Design Specification

[Additional context and details here]
```

**Key fields:**
- `spec.selector` - CSS selector for the component
- `spec.url` - Dev server URL
- `criteria[]` - List of validation criteria

**Criterion types:**
- `layout` - Positioning, alignment, dimensions
- `spacing` - Margins, padding, gaps
- `typography` - Fonts, sizes, weights
- `color` - Colors, contrast
- `interaction` - Hover states, animations

---

## Example Workflows

### Workflow 1: Verify Existing Implementation

```
You: "I need to verify the Recent Cards are properly centered"

Agent: "I'll use design-validator to check"
[Captures screenshot, analyzes layout, validates]

Agent: "✅ Validation PASSED
- Screenshot shows cards centered
- Layout analysis confirms 12px gap
- All criteria met"

You: "Perfect, approved!"
```

### Workflow 2: Fix and Verify

```
You: "The cards are misaligned, please fix"

Agent: "I'll write a spec first, then fix and verify"
[Creates RECENT_CARDS_SPEC.md with criteria]

Agent: "Does this spec match your vision?"
You: "Yes"

Agent: "I'll delegate to design-validator with this spec"
[design-validator loops internally:]
  1. component-designer fixes alignment
  2. visual-verify captures screenshot
  3. layout-context checks alignment
  4. design-validate runs criteria
  5. [FAIL - gap is 8px not 12px]
  6. component-designer fixes gap
  7. [Verification repeats]
  8. [PASS - all criteria met]

Agent: "✅ Validation PASSED - here's the evidence package"
[Shows screenshot, layout analysis, validation report]

You: "Great! Exactly what I wanted"
```

### Workflow 3: Iterative Refinement

```
You: "Start implementing the dashboard"

Agent: [Implements, verifies internally, presents]

You: "Close, but the spacing needs adjustment"

Agent: [Fixes, verifies internally, presents]

You: "Perfect!"
```

**Key:** You only see results that have passed verification. No more QA loops.

---

## Troubleshooting

### "Cannot connect to dev server"

**Cause:** Dev server not running or wrong URL

**Fix:**
```bash
# Start your dev server
npm run dev

# Note the URL (e.g., http://localhost:5173)
# Tell agent: "The dev server is at http://localhost:5173"
```

### "Selector not found"

**Cause:** CSS selector doesn't match any elements

**Fix:**
```
# Inspect the page to find the correct selector
# Tell agent: "The component selector is .actual-class-name"
```

### "Playwright not installed"

**Cause:** Playwright browsers not installed

**Fix:**
```bash
playwright install chromium
```

### "Verification taking too long"

**Expected:** 15-20 seconds per verification cycle

**If longer:** Check if dev server is responding, try refreshing the page

### "False failures"

**Cause:** Criteria too strict or ambiguous

**Fix:** Refine spec criteria to be more specific and measurable

---

## Performance Expectations

**Per verification cycle:**
- visual-verify: ~7-12 seconds
- layout-context: ~3-5 seconds
- design-validate: ~5-10 seconds
- **Total:** ~15-20 seconds

**Typical session:**
- First attempt: 20 seconds (usually fails)
- Second attempt: 20 seconds (may fail)
- Third attempt: 20 seconds (usually passes)
- **Total:** ~1 minute for verified design

**ROI:**
- Without verification: 7 iterations × 2 minutes = 14 minutes + your QA time
- With verification: 1 minute agent time, 0 your QA time
- **Savings:** 13+ minutes per design task

**The overhead is worth it** - prevents circular loops that waste hours.

---

## Philosophy

> **"The chef must taste before serving."**

Agents should verify their work before presenting it to you. This is professional practice, not optional overhead.

> **"The user's time is their most valuable resource."**

When you're trying to express your creative vision, you can't be mired in small revisions. Verification lets you stay in the design mindset, not the QA mindset.

> **"Trust is built on evidence, not promises."**

"I think it's fixed" ≠ proof. Screenshots and analysis build trust that "when agents say it works, it works."

---

## Advanced Usage

### Custom Baselines

```
"Capture a baseline screenshot of .component for future comparisons"
```

Then future verifications will show pixel diffs against this baseline.

### Layout Context with Siblings

```
"Analyze layout-context for .card including siblings"
```

Gets computed styles for siblings to understand relative positioning.

### Validation Without Spec

```
"Use visual-verify and layout-context to analyze the component"
```

Manual inspection without formal spec validation.

---

## Success Metrics

Track these to measure verification impact:

| Metric | Before | After (Target) |
|--------|--------|----------------|
| **Iterations per task** | 7 | 1-2 |
| **Time to approval** | 2 days | 1 hour |
| **User QA loops** | Every iteration | Zero |
| **Agent trust score** | "Often broken" | "Usually works" |

---

## FAQ

**Q: Do I always need to write a spec?**  
A: No - design-validator can work without a formal spec for basic visual/layout checks. Specs are needed for systematic validation against criteria.

**Q: Can I use this for non-web projects?**  
A: Currently requires web dev server and browser automation. Could be extended to other visual artifacts (mobile apps, PDFs, etc.) in the future.

**Q: Does this work with component libraries (React, Vue, etc.)?**  
A: Yes - as long as there's a dev server and rendered HTML/CSS to capture.

**Q: What if I don't have Playwright installed?**  
A: The verification tools won't work, but you can still use the other 7 design agents for discovery, research, and spec creation.

**Q: Can I disable verification?**  
A: Yes - simply don't use the design-validator agent or verification tools. The rest of design-intelligence works independently.

---

## Related Resources

- **Quick Start:** [README.md](README.md)
- **Verification Bundle:** [amplifier-bundle-design-verification](https://github.com/anderlpz/amplifier-bundle-design-verification)
- **Integration Guide:** See design-verification bundle's INTEGRATION_GUIDE.md

---

## Summary

**Visual verification prevents circular fix loops by:**
1. Giving agents eyes to see what they built
2. Validating against specifications before presenting
3. Providing evidence (screenshots + analysis) with results

**Setup:** Install Playwright, start dev server, use design-validator

**Impact:** One-shot fixes instead of 7-iteration loops. Users approve on first presentation instead of becoming QA testers.

**Philosophy:** Professional agents verify before presenting. Your time is too valuable to waste on QA loops.
