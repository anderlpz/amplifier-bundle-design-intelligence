# Design Research Capability - Usage Instructions

This document explains how to use the design research capability for automated trend analysis.

## Overview

The design research capability provides:

1. **Automated scraping** of Awwwards and Siteinspire
2. **Visual analysis** of design screenshots using AI
3. **Trend summarization** with actionable insights
4. **Conversational queries** about design patterns and trends

## Components

### Agents

**research-runner** - Technical execution agent
- Executes scraping workflows
- Analyzes screenshots with vision AI
- Generates summaries and updates archive
- Used via recipes or direct invocation

**research-analyst** - User-facing conversational agent
- Answers questions about design trends
- Provides examples and inspiration
- Analyzes patterns across projects
- Has archive-index.md always loaded

### Recipe

**weekly-design-scrape** - Automated research workflow
- Scrapes both Awwwards and Siteinspire
- Analyzes all captured screenshots
- Generates monthly summary
- Updates 30-day archive index
- Takes 15-20 minutes to complete

### Skills Required

**playwright** - Browser automation for scraping
- Loaded by the research-runner agent at the start of a run
- See: `~/.amplifier/skills/robotdad/playwright/SKILL.md`

**image-vision** - Visual analysis of design screenshots
- Loaded by the research-runner agent before any screenshot analysis
- See: `~/.amplifier/skills/robotdad/image-vision/SKILL.md`

## Usage Patterns

### Running Periodic Scrapes

#### Prerequisites

**The recipes tool requires the `amplifier-bundle-recipes` bundle.** Either:
- Use a bundle that includes it (foundation does)
- Or combine bundles: your bundle + recipes

#### Option 1: Using the Recipe (Recommended)

**Conversational (in a session with recipes bundle):**
```
execute design-intelligence:recipes/weekly-design-scrape.yaml with year=2026 month=01 month_name=january date=2026-01-13
```

**CLI (direct tool invocation):**
```bash
amplifier tool invoke recipes \
  operation=execute \
  recipe_path=design-intelligence:recipes/weekly-design-scrape.yaml \
  context='{"year": "2026", "month": "01", "month_name": "january", "date": "2026-01-13"}'
```

The recipe automatically:
- Creates directory structure
- Scrapes both sources
- Analyzes images with vision AI
- Generates summaries
- Updates archive index

**When to run:** Weekly or bi-weekly to maintain current trend data

#### Option 2: Manual Execution

Use the task tool to invoke research-runner for custom workflows:

```
# In a session, delegate to research-runner:
Use the research-runner agent to scrape Awwwards for today's featured projects
Use the research-runner agent to analyze the screenshots from today's scrape
Use the research-runner agent to generate the monthly summary
```

### Querying Trends and Insights

Use research-analyst for conversational queries. In a design-intelligence session:

```
# Example queries (ask directly in session):
> What are the current trends in web animation?
> Show me examples of dark mode with vibrant accents
> How have grid layouts evolved in the last 3 months?
> I'm designing a portfolio site - show me best practices
```

The analyst has archive-index.md always loaded for quick answers, and can load monthly summaries on demand for deeper analysis.

### Example Workflows

#### Workflow 1: Weekly Research Update

```bash
# 1. Run automated scrape (takes 15-20 min)
amplifier tool invoke recipes \
  operation=execute \
  recipe_path=design-intelligence:recipes/weekly-design-scrape.yaml \
  context='{"year": "2026", "month": "01", "month_name": "january", "date": "2026-01-13"}'

# 2. Review results (check session status)
amplifier tool invoke recipes operation=list

# 3. Query insights with analyst (in a session)
# Start design-intelligence session and ask:
> What trends emerged from this week's scrape?
```

#### Workflow 2: Design Inspiration Research

In a design-intelligence session, have a conversation with the research-analyst:

```
# Example conversation:
> I'm designing a SaaS dashboard. Show me current trends in data visualization
> [Analyst provides examples from archive]
> Can you show me more examples of dark mode implementations?
> [Analyst loads relevant monthly summaries and provides detailed examples]
> What colors are trending for accent highlights?
> [Analyst synthesizes color trend data]
```

#### Workflow 3: Competitive Analysis

In a design-intelligence session:

```
> Show me all e-commerce sites from the last 2 months
> [Analyst searches archive]
> How do they handle product galleries?
> [Analyst provides pattern analysis]
> What's the most common navigation pattern?
> [Analyst synthesizes navigation trends]
```

## Archive Structure

All research data is stored in the archive directory:

```
archive/
├── 2026/
│   ├── 01-january/
│   │   ├── raw/
│   │   │   ├── awwwards-2026-01-12.json
│   │   │   └── siteinspire-2026-01-12.json
│   │   ├── images/
│   │   │   ├── project-alpha-screenshot.png
│   │   │   └── project-beta-screenshot.png
│   │   ├── visual-analysis.json
│   │   └── summary.md
│   └── 02-february/
│       └── ...
└── archive-index.md
```

### File Descriptions

**raw/*.json** - Structured project data
- Project titles, URLs, categories, tags
- Scrape metadata (date, duration, source)
- Screenshot references

**images/*.png** - Design screenshots
- Project cards from Awwwards/Siteinspire
- Used for visual analysis

**visual-analysis.json** - Vision AI analysis results
- Color palettes identified
- Layout styles observed
- Visual elements detected
- Error details for failed analyses

**summary.md** - Monthly trend summary
- Trend highlights by category
- Notable projects with links
- Visual insights from analysis
- LLM-optimized for analyst queries

**archive-index.md** - 30-day rolling summary
- Quick overview of recent trends
- Top patterns per category
- Links to detailed monthly summaries
- Kept under 500 tokens for efficiency

## Best Practices

### For Running Scrapes

1. **Run weekly** to maintain current data
2. **Check logs** after each scrape for failures
3. **Review visual-analysis.json** to see which images were successfully analyzed
4. **Monitor archive size** - consider archiving old months after 6 months
5. **Validate outputs** before relying on summaries

### For Querying Insights

1. **Start with archive-index.md** for quick trends (analyst has this loaded)
2. **Ask specific questions** for better responses
3. **Request examples** to see real implementations
4. **Compare across time** to understand evolution
5. **Load monthly summaries** only when needed for deep dives

### For Maintenance

1. **Archive old data** after 6+ months to compressed storage
2. **Backup archive/** directory periodically
3. **Review and clean** failed image analyses
4. **Update scraping scripts** if website structures change
5. **Monitor API costs** for vision analysis

## Troubleshooting

### Scrape Failures

**Problem:** JSON file not created or empty
- Check Playwright logs for navigation errors
- Verify website structure hasn't changed
- Check network connectivity

**Problem:** Few projects captured (< 10)
- Website may have changed structure
- Selector patterns may need updating
- Check research-runner agent logs

### Vision Analysis Issues

**Problem:** Many images failed analysis
- Check API keys are set (ANTHROPIC_API_KEY, GOOGLE_API_KEY, etc.)
- Verify image files aren't corrupted
- Check image sizes (resize if > 5MB)
- Review timeout settings (increase if needed)

**Problem:** Analysis results seem fabricated
- Check exit codes in visual-analysis.json
- Verify actual API responses were received
- Don't trust analysis if marked with errors
- Re-run failed images individually

### Archive Issues

**Problem:** archive-index.md not updating
- Check last stage of recipe completed
- Verify summary.md files exist for recent months
- Manually run update-archive-index stage

**Problem:** Analyst can't find recent data
- Verify archive-index.md exists and has recent date
- Check monthly summary.md files are readable
- Try loading specific month manually

## Configuration

### Scrape Settings

Edit the recipe or research-runner prompts to adjust:
- **Project count:** Default 15 per source (max ~30 recommended)
- **Rate limiting:** 2-3 seconds between pages (avoid rate limits)
- **Timeout:** 30 seconds per page load
- **Retry attempts:** 3 max per failed operation

### Vision Analysis Settings

Default providers (in order of fallback):
1. **Gemini Flash** - Fastest (3-10s), good quality
2. **Anthropic Claude** - Balanced (5-15s)
3. **OpenAI GPT-4** - Slowest (8-20s), highest quality

To change provider priority, edit the vision analysis section in research-runner.

### Archive Retention

Default: Keep all data indefinitely
Recommended: Archive months older than 6 months to compressed storage

## Integration with Other Tools

### Export to Reports

```bash
# Convert summary.md to other formats
pandoc archive/2026/01-january/summary.md -o report.pdf
pandoc archive/2026/01-january/summary.md -o report.docx
```

### API Integration

```python
# Read archive data programmatically
import json

with open('archive/2026/01-january/raw/awwwards-2026-01-12.json') as f:
    projects = json.load(f)['projects']
    
for project in projects:
    print(f"{project['title']}: {project['url']}")
```

### Presentation Building

Use research-analyst to generate talking points, then reference screenshots from archive/images/ in your slides.

## Tips for Effective Use

### Getting Better Trend Insights

1. **Run scrapes consistently** (same day each week)
2. **Let data accumulate** (trends emerge over 2-3 months)
3. **Ask comparative questions** ("How has X changed?")
4. **Request specific examples** ("Show me 3 examples of...")

### Leveraging Visual Analysis

1. **Trust high-level observations** (layouts, colors)
2. **Verify typography details** (vision AI struggles with fonts)
3. **Use for triage** (identify areas to investigate further)
4. **Cross-reference** with actual website visits for details

### Working with the Analyst

1. **Be specific in queries** (better results than vague questions)
2. **Follow up** (analyst offers deeper exploration)
3. **Request comparisons** across time periods
4. **Ask for recommendations** based on your design goals

## Additional Resources

- **Playwright Skill:** `~/.amplifier/skills/robotdad/playwright/SKILL.md`
- **Image-Vision Skill:** `~/.amplifier/skills/robotdad/image-vision/SKILL.md`
- **Research Runner Agent:** `@design-intelligence:agents/research-runner.md`
- **Research Analyst Agent:** `@design-intelligence:agents/research-analyst.md`
- **Weekly Scrape Recipe:** `@design-intelligence:recipes/weekly-design-scrape.yaml`
- **Archive Index:** `@design-intelligence:context/archive-index.md`

---

**Questions or issues?** Check the agent documentation or review the recipe logs for detailed error information.
