# Design Research Capability - Community Notes

**Status:** Foundational implementation - significant opportunities for community improvement

This document outlines the current state of the design research capability and identifies areas where community contributions would be especially valuable.

---

## Current Implementation

### What's Working

- **Research agents** (research-runner, research-analyst) for scraping and analysis
- **Archive structure** for storing observations by date
- **Research-aware design agents** that can load archive-index.md on demand
- **Weekly scrape recipe** for automated observation collection
- **Observed-expression directory** for metacognitive design knowledge

### What's Foundational

This is a v1 implementation focused on establishing the pattern. Many aspects are intentionally simple to allow community enhancement.

---

## Community Improvement Opportunities

### 1. Scraping Infrastructure

**Current:** Recipe-based scraping with Playwright instructions

**Opportunities:**
- [ ] **Robust scrapers** - Dedicated scraper modules for Awwwards, Siteinspire, Behance, Dribbble
- [ ] **Rate limiting** - Respectful scraping with configurable delays
- [ ] **Change detection** - Alert when site structure changes break scrapers
- [ ] **Additional sources** - Landbook, SiteInspire categories, CSS Design Awards
- [ ] **RSS/API integration** - Use APIs where available instead of scraping

### 2. Vision Analysis

**Current:** Basic vision prompts for analyzing screenshots

**Opportunities:**
- [ ] **Structured output** - Consistent JSON schema for visual analysis
- [ ] **Color extraction** - Automated palette extraction from images
- [ ] **Typography detection** - Font identification (if technically feasible)
- [ ] **Layout classification** - Automated categorization of layout patterns
- [ ] **Comparison analysis** - Track how specific design patterns evolve over time

### 3. Archive Management

**Current:** Manual archive structure with monthly summaries

**Opportunities:**
- [ ] **Automated indexing** - Better search across historical observations
- [ ] **Deduplication** - Detect when same site appears across sources
- [ ] **Tagging system** - Consistent taxonomy for categorizing observations
- [ ] **Archive rotation** - Automated cleanup of old data while preserving summaries
- [ ] **Export formats** - Generate reports in various formats (PDF, HTML, etc.)

### 4. Trend Analysis

**Current:** LLM-generated summaries from raw observations

**Opportunities:**
- [ ] **Quantitative tracking** - Count occurrences of specific patterns over time
- [ ] **Trend visualization** - Charts showing pattern evolution
- [ ] **Predictive insights** - Identify emerging vs. fading trends
- [ ] **Industry segmentation** - Track trends by industry vertical
- [ ] **Geographic analysis** - Regional design preference patterns

### 5. Knowledge Base Enhancement

**Current:** typography-personalities.md as initial observed-expression document

**Opportunities:**
- [ ] **Color psychology** - What colors communicate in different contexts
- [ ] **Spacing expression** - How whitespace conveys meaning
- [ ] **Motion vocabulary** - Animation styles and their emotional impact
- [ ] **Layout narratives** - How structure tells stories
- [ ] **Research validation** - Cross-reference knowledge base with actual observations

### 6. Integration Improvements

**Current:** Agents load archive-index.md on demand

**Opportunities:**
- [ ] **Semantic search** - Query archive with natural language
- [ ] **Example retrieval** - "Show me sites like X" from archive
- [ ] **Automatic suggestions** - Surface relevant examples during design work
- [ ] **Reference linking** - Connect observations to knowledge base concepts
- [ ] **Export to Figma/design tools** - Bridge between research and implementation

### 7. Recipe Enhancement

**Current:** Basic weekly-design-scrape.yaml recipe

**Opportunities:**
- [ ] **Parallel scraping** - Scrape multiple sources simultaneously
- [ ] **Incremental updates** - Only process new content since last run
- [ ] **Quality gates** - Validation steps before archiving
- [ ] **Notification hooks** - Alert on interesting findings
- [ ] **Scheduled execution** - Integration with cron/scheduling systems

---

## Technical Debt / Known Limitations

### Things That Need Improvement

1. **No actual scraper code** - Recipe relies on agent executing Playwright commands; dedicated scrapers would be more reliable
2. **Vision analysis is prompt-only** - No structured parsing of vision outputs
3. **Archive index is static** - Needs manual regeneration; could be dynamic
4. **Single-threaded processing** - Large archives could benefit from parallel processing
5. **No error recovery** - Failed scrapes don't have retry logic

### Architectural Decisions Open for Discussion

1. **Archive format** - Currently flat files; database might scale better
2. **Image storage** - Currently local; CDN/cloud storage for larger archives
3. **Research freshness** - 30-day rolling window; configurable retention?
4. **Agent boundaries** - research-runner vs research-analyst split could be refined

---

## Contributing

### Quick Wins (Good First Issues)

- Add additional inspiration site URLs to the scraping workflow
- Improve vision analysis prompts for better structured output
- Add more typography personalities to observed-expression
- Create templates for monthly summary format
- Add validation for archive JSON files

### Medium Effort

- Build a dedicated scraper module for one inspiration site
- Create color-psychology.md in observed-expression
- Implement archive search functionality
- Add quantitative trend tracking

### Larger Projects

- Full scraper infrastructure with multiple sources
- Semantic search across research archive
- Visualization dashboard for trends
- Integration with design tool plugins

---

## Design Philosophy Alignment

This research capability should follow the Amplifier design philosophy:

1. **Mechanism, not policy** - Provide research infrastructure; let users decide how to use it
2. **Ruthless simplicity** - Start simple, add complexity only when justified
3. **Composable** - Research components should work independently
4. **Observable** - Research process should be transparent and debuggable

When contributing, prefer:
- Simple implementations that work over complex ones that might
- Clear documentation over clever code
- Explicit behavior over implicit magic

---

## Questions for Community Discussion

1. **How often should research run?** Weekly? Daily? On-demand only?
2. **What sources are most valuable?** Focus on few high-quality or many varied?
3. **How much historical data to keep?** Rolling window vs. full archive?
4. **Should trend analysis be automated or human-curated?**
5. **Integration depth** - How tightly should research connect to design agents?

---

*This document should evolve as the community contributes. Update it when making significant changes to the research capability.*
