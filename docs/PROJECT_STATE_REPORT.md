# Project State Report: Getaround SEO Automation

## Report Status

| Status | Details |
|--------|---------|
| **Report Date** | 2026-01-07 |
| **Phase** | 2 - Project State Synthesis |
| **Purpose** | Foundation for workflow architecture |
| **Readiness** | Ready for Phase 3 |

---

## 1. Executive Summary

### Project Mission
Build an AI-powered SEO content automation system for Getaround using n8n workflows, reducing content creation time from 5-6 hours to 1 hour while improving SEO performance.

### Current State
- **Phase 0 (Market Validation):** Complete - Data-driven market strategies validated
- **Phase 1 (Context Discovery):** Complete - SEO trends and tools documented
- **Phase 2 (State Synthesis):** This report
- **Phase 3+ (Workflow Design):** Ready to begin

### Key Validated Findings

| Finding | Implication |
|---------|-------------|
| France is B2B market (45%+ professional) | Regulatory/tax content priority |
| Norway is B2C market (70%+ consumer) | Activity/travel content priority |
| CTR optimization = fastest growth | Title/meta fixes before new content |
| 60% zero-click searches (2026) | Answer-first content structure |
| Human expertise differentiating | E-E-A-T signals critical |

### Readiness Assessment

| Dimension | Status | Notes |
|-----------|--------|-------|
| Market data | ✅ Ready | Full year GSC data extracted |
| Content strategy | ✅ Ready | Validated per market |
| Technical tools | ✅ Ready | GSC + n8n MCP connected |
| SEO requirements | ✅ Ready | 2026 trends documented |
| Stakeholder requirements | ✅ Ready | From project-context.md |

---

## 2. Market Performance Summary

### France Blog (`fr.getaround.com/blog/`)

| Metric | 2025 Value | Benchmark | Status |
|--------|------------|-----------|--------|
| **Annual Clicks** | ~40,200 | - | Strong |
| **Annual Impressions** | ~2,550,000 | - | High volume |
| **Average CTR** | 1.58% | 2-3% | Below target |
| **Average Position** | ~18.5 | Top 10 | Page 2 average |
| **Total Articles** | 451 | - | Good coverage |
| **Mobile Traffic** | 70% | - | Mobile-first |

**Top Content Types:**
1. B2B/Professional (45%) - déplacement professionnel, redevance
2. Van/Road Trip (20%) - van aménagé, road trips
3. ZFE Regulatory (17%) - city-specific guides
4. Owner/Rentability (10%) - earning calculators

**Peak Season:** January (ZFE regulations)

**Quick Win Opportunity:** `prix-location-voiture-au-mois` - 508K impressions, 0.46% CTR → +7,800 clicks potential

### Norway Blog (`no.getaround.com/blogg/`)

| Metric | 2025 Value | Benchmark | Status |
|--------|------------|-----------|--------|
| **Annual Clicks** | ~3,000 | - | Needs growth |
| **Annual Impressions** | ~484,000 | - | Moderate |
| **Average CTR** | 0.62% | 2-3% | Well below target |
| **Average Position** | ~28 | Top 10 | Page 3 average |
| **Total Articles** | 230 | - | Adequate |
| **Mobile Traffic** | 75% | - | Mobile-first |

**Top Content Types:**
1. Activity Listicles (30%) - "aktiviteter barn Oslo"
2. Road Trip Guides (24%) - specific itineraries
3. Owner Guides (15%) - "disse bilene bør du leie ut"
4. City Guides (12%) - underperforming

**Peak Season:** July (Fellesferie)

**Best Performer:** `2-dagers-tur-hardangervidda` - 12.99% CTR, position 2.7

### Cross-Market Comparison

| Aspect | France | Norway | Ratio |
|--------|--------|--------|-------|
| Clicks | 40,200 | 3,000 | 13.4x |
| CTR | 1.58% | 0.62% | 2.5x |
| Content Type | B2B | B2C | Different |
| Peak Season | January | July | Opposite |
| Strategy | Regulatory guides | Activity listicles | Different |

---

## 3. Validated Content Strategy

### France Content Strategy

| Element | Validated Approach |
|---------|-------------------|
| **Primary Focus** | B2B professional content |
| **Secondary Focus** | ZFE regulatory guides |
| **Tertiary Focus** | Van/road trip content |
| **Format** | Detailed guides with calculations |
| **Tone** | Formal "vous", professional |
| **Year-Stamping** | Mandatory for regulatory |
| **Schema** | FAQPage, HowTo |
| **Cities** | Paris, Lyon, Toulouse (ZFE) |

**Content Formula:**
```
B2B topic + Regulatory angle + Year-stamp = High performance
```

### Norway Content Strategy

| Element | Validated Approach |
|---------|-------------------|
| **Primary Focus** | Consumer activity content |
| **Secondary Focus** | Specific road trip itineraries |
| **Tertiary Focus** | Owner/supply guides |
| **Format** | Listicles, day-by-day itineraries |
| **Tone** | Informal "du", friendly |
| **Year-Stamping** | Optional for evergreen |
| **Schema** | HowTo, FAQPage |
| **Cities** | Oslo >> Tromsø > Bergen |

**Content Formula:**
```
Consumer activity + Specific location/duration + Car necessity = High performance
```

### Universal Patterns (Both Markets)

| Pattern | Evidence |
|---------|----------|
| Mobile dominance | 70-75% traffic |
| Owner content works | High CTR in both |
| Generic city guides fail | Low CTR, poor position |
| Desktop users higher CTR | +24-28% vs mobile |
| Van/camper content works | Strong in both |
| Price comparison fails | High impressions, <1% CTR |

### Anti-Patterns (Avoid)

| Pattern | Reason |
|---------|--------|
| Vanity traffic content | Attracts car owners, not renters |
| Generic price comparisons | Loses to aggregators |
| Broad city guides | Not car-rental specific |
| Maintenance tips | Wrong audience |

---

## 4. Technical Infrastructure

### Available MCP Servers

| Server | Status | Tools | Use Case |
|--------|--------|-------|----------|
| **gsc** | ✅ Connected | 15+ | SEO data extraction |
| **n8n-mcp** | ✅ Connected | 19 | Workflow building |
| **figma** | ✅ Connected | 8 | Design assets |
| **fiken** | ✅ Connected | 20+ | Not relevant |

### GSC Properties

| Property | Market | Status |
|----------|--------|--------|
| sc-domain:no.getaround.com | Norway | ✅ Active |
| sc-domain:fr.getaround.com | France | ✅ Active |
| sc-domain:es.getaround.com | Spain | Available |
| sc-domain:de.getaround.com | Germany | Available |

### Key Tools for Workflows

| Workflow | Primary Tools |
|----------|---------------|
| **Research** | `get_advanced_search_analytics`, `compare_search_periods` |
| **Planning** | `get_search_by_page_query`, n8n AI nodes |
| **Writing** | n8n Claude/OpenAI nodes |
| **Review** | Validation tools, schema checkers |
| **Monitoring** | `inspect_url_enhanced`, `compare_search_periods` |

### Integration Gaps

| Integration | Status | Impact | Workaround |
|-------------|--------|--------|------------|
| Semrush | No MCP | Limited keyword research | Manual export |
| Ghost CMS | No MCP | No direct publishing | n8n HTTP node |
| GA4 | No MCP | No traffic correlation | Manual export |
| Slack | Via n8n | Notifications OK | n8n Slack node |

---

## 5. SEO/AEO Requirements (2026)

### Industry Trends Impacting Strategy

| Trend | Impact | Response |
|-------|--------|----------|
| 60% zero-click searches | Less traffic from rankings | Optimize for being THE answer |
| 25% traffic → AI chatbots | New distribution channel | Track AI citations |
| GEO/AEO essential | New optimization discipline | Answer-first content |
| Human expertise valued | AI content devalued | E-E-A-T signals |
| Search fragmentation | Users across platforms | Multi-platform monitoring |

### Content Structure Requirements

| Requirement | Implementation |
|-------------|----------------|
| **Answer-first** | Direct answer in first 1-3 sentences |
| **Question headings** | H2s matching search queries |
| **Scannable format** | Lists, bold, short paragraphs |
| **Schema markup** | FAQPage, HowTo on all content |
| **E-E-A-T signals** | Author bios, credentials, citations |

### Schema Markup Priority

| Schema | Use Case | Priority |
|--------|----------|----------|
| FAQPage | Q&A content, ZFE guides | Critical |
| HowTo | Road trip itineraries, guides | Critical |
| Article | All blog posts with author | High |
| LocalBusiness | Location-specific pages | Medium |

### New KPIs for 2026

| KPI | Measurement Method |
|-----|-------------------|
| Featured snippet presence | Semrush/Ahrefs tracking |
| AI Overview appearance | Manual GSC monitoring |
| Brand mentions in AI | Manual ChatGPT/Perplexity queries |
| Zero-click traffic | Impressions vs clicks analysis |

---

## 6. Workflow Requirements

### Stakeholder Requirements (from PM)

| Requirement | Detail |
|-------------|--------|
| **Volume** | 6 FR articles/month, 4 NO articles/month |
| **Process** | Friday assignments → publish by next Friday |
| **Review** | Human approval required before publishing |
| **Quality** | SEO optimized, internal linking, images |

### Time Savings Target

| Step | Current | Target | Automation |
|------|---------|--------|------------|
| Research | 1-2 hours | 15 min | High |
| Planning/Outline | 1 hour | 10 min | High |
| Writing | 2-3 hours | 30 min | Medium |
| Review/Edit | 1 hour | 30 min | Low |
| Publishing | 30 min | 15 min | Medium |
| **Total** | **5-6 hours** | **~1.5 hours** | - |

### 5-Workflow System

| Workflow | Trigger | Automation Level | Human Touchpoint |
|----------|---------|------------------|------------------|
| **1. Research** | Weekly schedule | High | Review data |
| **2. Planning** | After research | High | Approve topics |
| **3. Writing** | After planning | Medium | Edit draft |
| **4. Review** | After writing | Medium | Final approval |
| **5. Monitoring** | Weekly schedule | High | Review report |

### Workflow Data Flow

```
Research → Planning → Writing → Review → [Publish] → Monitoring
    ↓          ↓          ↓         ↓                    ↓
GSC Data  Topic List  Draft    Approved        Performance
                               Article          Report
```

---

## 7. Success Metrics

### Short-term (3 months)

| Metric | Baseline | Target | Measurement |
|--------|----------|--------|-------------|
| Norway CTR | 0.62% | 1.5% | GSC |
| France CTR | 1.58% | 2.5% | GSC |
| Page 1 rankings | - | +10 articles | GSC position |
| Monthly clicks (NO) | 250 | 500 | GSC |
| Content creation time | 5-6 hours | 1.5 hours | Manual tracking |

### Long-term (12 months)

| Metric | Baseline | Target | Measurement |
|--------|----------|--------|-------------|
| Monthly clicks (NO) | 250 | 2,000 | GSC |
| Featured snippets | - | 20+ queries | Tracking tool |
| AI citations | - | Brand mentioned | Manual audit |
| Topical authority | - | Established | Position trends |

### Workflow Success Metrics

| Metric | Target |
|--------|--------|
| Research accuracy | 90%+ relevant opportunities identified |
| Planning efficiency | <10 min per topic |
| Draft quality | <30 min human editing needed |
| Review pass rate | 80%+ first-pass approval |
| Monitoring coverage | 100% of published content tracked |

---

## 8. Risks & Mitigations

### Technical Risks

| Risk | Impact | Mitigation |
|------|--------|------------|
| MCP server downtime | Workflow failure | Fallback to manual GSC |
| AI model changes | Output quality varies | Version pinning, prompt testing |
| Rate limits | Workflow delays | Batching, caching |
| Ghost CMS integration | Publishing bottleneck | HTTP API fallback |

### Content Risks

| Risk | Impact | Mitigation |
|------|--------|------------|
| AI content detection | Google penalty | Human review, editing |
| Outdated regulatory info | User trust damage | Year-stamping, review schedule |
| Wrong market tone | Low engagement | Market-specific prompts |
| Vanity traffic creation | Wasted resources | Business fit validation |

### Business Risks

| Risk | Impact | Mitigation |
|------|--------|------------|
| Low adoption by team | ROI not achieved | Training, documentation |
| Over-automation | Quality decline | Human touchpoints required |
| Competitor catch-up | Advantage lost | Continuous improvement |

---

## 9. Readiness for Phase 3

### Checklist

| Requirement | Status |
|-------------|--------|
| Market data extracted | ✅ Complete |
| Content strategy validated | ✅ Complete |
| Technical tools documented | ✅ Complete |
| SEO/AEO requirements defined | ✅ Complete |
| Workflow requirements clear | ✅ Complete |
| Success metrics defined | ✅ Complete |
| Risks identified | ✅ Complete |

### Phase 3 Deliverables

1. **WORKFLOW_ARCHITECTURE.md** - 5-workflow system design
2. **AUTOMATION_MATRIX.md** - Manual vs automated steps
3. **NODE_SPECIFICATIONS.md** - Detailed node configs

### Key Decisions for Phase 3

| Decision | Options | Recommendation |
|----------|---------|----------------|
| AI model for writing | Claude / GPT-4 / Both | Claude (better long-form) |
| Workflow trigger | Schedule / Manual / Both | Schedule + manual override |
| Review workflow | Slack / Email / Dashboard | Slack for speed |
| Publishing | Auto / Manual | Manual (human required) |

---

## Appendix: Document References

| Phase | Document | Location |
|-------|----------|----------|
| 0A | France Analysis | `analysis/FRANCE_BLOG_ANALYSIS_2025.md` |
| 0B | Norway Analysis | `analysis/NORWAY_BLOG_ANALYSIS_2025.md` |
| 0C | Cross-Market Synthesis | `analysis/CROSS_MARKET_SYNTHESIS.md` |
| 1 | SEO/AEO Trends | `docs/SEO_AEO_TRENDS_2026.md` |
| 1 | MCP Inventory | `docs/MCP_TOOLS_INVENTORY.md` |
| - | Project Context | `docs/project-context.md` |
| 2 | This Report | `docs/PROJECT_STATE_REPORT.md` |

---

*Report Generated: 2026-01-07*
*Ready for: Phase 3 - Workflow Architecture Design*
