# Design Research Archive - Last 30 Days

**Generated:** 2026-01-12  
**Period:** Last 30 days of design trend observations  
**Status:** Initial template - awaiting first research scrape

---

## Quick Trends

> **Note:** This index will be populated after running the first design research scrape.
> Run: `amplifier recipe execute @design-intelligence:recipes/weekly-design-scrape.yaml`

### Animation & Interaction
*Awaiting data from first scrape*

### Color & Visual Style
*Awaiting data from first scrape*

### Layout & Typography
*Awaiting data from first scrape*

### Notable Techniques
*Awaiting data from first scrape*

---

## Recent Summaries

*No summaries available yet. Run the weekly-design-scrape recipe to begin collecting data.*

---

## Getting Started

This archive index is automatically populated by the **research-runner** agent when you execute the **weekly-design-scrape** recipe.

### First-Time Setup

1. **Run your first scrape:**
   ```bash
   amplifier recipe execute @design-intelligence:recipes/weekly-design-scrape.yaml
   ```

2. **Wait for completion** (15-20 minutes)
   - Scrapes Awwwards and Siteinspire
   - Analyzes screenshots with vision AI
   - Generates monthly summary
   - Updates this index

3. **Query trends with the analyst:**
   ```bash
   amplifier chat -a @design-intelligence:agents/research-analyst.md
   ```

### What Gets Populated

After your first scrape, this index will contain:

- **Top 3-5 trends** per category from the last 30 days
- **Links** to detailed monthly summaries
- **Quick references** to notable projects
- **Pattern highlights** for rapid trend understanding

### Update Frequency

- **Recommended:** Run weekly scrapes to maintain current data
- **Automatic:** This index updates at the end of each scrape workflow
- **Rolling window:** Always shows last 30 days of observations

---

## Archive Structure

```
archive/
├── YYYY/
│   ├── MM-month/
│   │   ├── raw/
│   │   │   ├── awwwards-YYYY-MM-DD.json
│   │   │   └── siteinspire-YYYY-MM-DD.json
│   │   ├── images/
│   │   │   └── *.png (design screenshots)
│   │   ├── visual-analysis.json
│   │   └── summary.md (monthly trend summary)
│   └── ...
└── archive-index.md (this file - 30-day rolling summary)
```

### Data Storage Pattern

- **JSON** - Structured data for programmatic access
- **Markdown** - LLM-optimized summaries for analysis
- **Images** - Visual references for analysis
- **Hybrid approach** - Best of both worlds

### Context Optimization

This index is kept **under 500 tokens** for efficient LLM context loading:
- Eagerly loaded by **research-analyst** agent
- Monthly summaries loaded on demand for deep dives
- Raw JSON accessed only for specific project queries

---

## Usage Patterns

### Quick Trend Queries (No Load Required)
The research-analyst has this index pre-loaded for instant answers:
- "What's trending right now?"
- "Show me current animation patterns"
- "What colors are popular?"

### Deep Dive Queries (Load Monthly Summaries)
For detailed analysis, the analyst loads monthly summaries:
- "How have layouts evolved over 3 months?"
- "Show me all e-commerce examples from December"
- "Compare animation trends: Nov vs Jan"

### Inspiration Requests (Load Projects + Images)
For specific examples, the analyst can reference raw data:
- "I need portfolio site examples"
- "Show me dark mode implementations"
- "Find projects using asymmetric grids"

---

## Maintenance

### Automated
- ✅ Updated by research-runner after each scrape
- ✅ Always reflects last 30 days
- ✅ Links updated automatically

### Manual (Optional)
- Archive old months (>6 months) to compressed storage
- Clean up failed image analyses
- Backup archive directory periodically

---

## Resources

- **Usage Guide:** `@design-intelligence:context/research-instructions.md`
- **Run Scrape:** `@design-intelligence:recipes/weekly-design-scrape.yaml`
- **Query Trends:** `@design-intelligence:agents/research-analyst.md`
- **Technical Agent:** `@design-intelligence:agents/research-runner.md`

---

*This is a living document, automatically regenerated after each research scrape to reflect the latest 30 days of design trend observations.*
