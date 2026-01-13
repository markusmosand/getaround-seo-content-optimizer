# Project Context: Getaround SEO Automation

## Company Overview
Getaround is a peer-to-peer car-sharing marketplace operating in Norway and France.
- **Business model:** Private owners and small professional actors list cars; renters book via app/web
- **Products:** Getaround Connect (hardware unlock), Native Connect (Tesla), Key handover, Long-term rental, B2B
- **Competitors:** Hyre (Norway), Turo (France), GoMore (Nordics), traditional rental companies

## Current Blog Performance

### Norway (`/blogg/`)
- **Articles:** 211 published
- **Clicks:** ~182/month (545 over 90 days)
- **CTR:** 0.55% (industry standard: 2-3%)
- **Position:** 28.2 average
- **Mobile:** 76% of traffic
- **Concentration:** Top 10 articles = 48% of traffic

### France (`/blog/`)
- **Articles:** 390+ published
- **Clicks:** ~92,000/month (reported, needs validation)
- **CTR:** 2.5% (reported, needs validation)

### Key Insight
Norway blog significantly underperforms. France appears stronger but assumptions need validation.

## Proven Content Patterns (Norway - VALIDATED)

### What Works
1. **Activity listicles:** "Topp 5 aktiviteter barn Oslo" (1,293 sessions, 78% engagement)
2. **Owner guides:** "Disse bilene bør du leie ut" (296 sessions, 90% engagement)
3. **Specific use-cases:** "Lei bil til bryllupet" (169 sessions, 85% engagement)
4. **Travel content:** "2 dagers tur Hardangervidda" (12.99% CTR, position 2.65)

### What Doesn't Work
1. **Vanity traffic:** "Skifte til vinterdekk" - maintenance topic, not rental-relevant
2. **Generic safety:** "Sikring av barn i bil" - high impressions, near-zero clicks
3. **Case studies without takeaways:** Personal stories without actionable content

## Current Assumptions (TO BE VALIDATED IN PHASE 0)

### France (UNVALIDATED)
- Tone: Formal "vous" with warmth
- Content focus: B2B/professional (60%), regulatory
- Format: Professional guides, regulatory explainers
- Priority cities: Paris, Lyon, Marseille
- Year-stamping mandatory for regulatory content

### Norway (PARTIALLY VALIDATED)
- Tone: Informal "du" ✅
- Content focus: Consumer activities (70%), outdoor/nature, family
- Format: Listicles "Topp 5/10..." ✅
- Priority cities: Oslo >> Tromsø > Bergen > Stavanger

## Technical Infrastructure

### Skills Available (in /mnt/skills/user/)
1. **getaround-seo-content-optimizer** - Article creation with market detection
2. **getaround-seo-aeo-analyst** - Performance analysis and diagnostics
3. **getaround-translator** - NO/EN/FR translation with brand voice
4. **gsc-analysis** - Comprehensive GSC analysis
5. **n8n-workflow-builder** - Workflow design patterns

### MCP Connections
- **gscServer:** Connected - 8 tools for GSC data
- **n8n-cloud:** Connected - Workflow management

### Integrations Status
- ✅ Google Search Console (MCP)
- ✅ n8n Cloud (MCP)
- ⏳ Semrush (manual export only)
- ⏳ Ghost CMS (API integration TBD)
- ⏳ GA4 (manual export only)
- ⏳ Slack notifications (easy to add)

## Stakeholder Requirements

### From PM (Clément)
- **Volume targets:** 6 FR articles/month, 4 NO articles/month, 3 ES articles/month
- **Focus:** B2C first, then Supply & B2B
- **Human review:** Required before publishing
- **Workflow:** Friday assignments, publish by following Friday

### Quality Requirements
- SEO optimized (impressions + clicks)
- Relevant backlinking strategy
- Internal linking between articles
- Images included
- Complete meta descriptions, titles

## Success Metrics

### Short-term (3 months)
- CTR: 0.55% → 1.5%
- Move 10+ articles from page 2 to page 1
- 500+ monthly clicks from optimized content
- Content creation time: 5-6 hours → 1 hour

### Long-term (12 months)
- 2,000+ monthly clicks (11x baseline)
- Topical authority established
- AI overview citations (Google, ChatGPT, Perplexity)
- Fully automated weekly reporting

## Business Fit Validation

**Critical Filter:** Every piece of content must attract users who want to RENT A CAR.

### Good Business Fit
- "Best road trips from Oslo" → User needs a car
- "How to rent a car for a wedding" → Transactional intent
- "Activities for families in Bergen" → May need car to get there

### Bad Business Fit (Vanity Traffic)
- "How to change winter tires" → User already has a car
- "Car safety regulations" → Informational, no rental intent
- "Best cars to buy in 2025" → Purchase intent, not rental

## GSC Query Parameters

### For France Blog
```
site_url: "sc-domain:getaround.com"
filter_expression: "/blog/"
```

### For Norway Blog
```
site_url: "sc-domain:getaround.com"
filter_expression: "/blogg/"
```

### Standard Parameters
```
dimensions: "page" or "query" or "page,query"
row_limit: 500-1000
sort_by: "impressions" or "clicks"
sort_direction: "descending"
```
