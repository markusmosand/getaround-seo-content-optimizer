# Task 011: Norway Blog - Content Classification

## Status: [ ] Todo

## Prerequisite
- Task 010 (GSC extraction) completed

## Objective
Classify top 100 Norway blog articles to understand content patterns.

---

## Classification Taxonomy

### Content Type Categories

| Category | Trigger Keywords (in URL or title) |
|----------|-----------------------------------|
| **Activities/Leisure** | aktiviteter, ting å gjøre, opplevelser, utflukter |
| **Family** | barn, familie, barnevennlig, kids |
| **Nature/Outdoor** | vandring, fjell, natur, tur, ski, friluftsliv |
| **City Guides** | Oslo, Bergen, Tromsø, Stavanger, Trondheim |
| **How-to/Practical** | hvordan, guide, tips, råd, slik |
| **Owner/Supply** | utleier, leie ut, inntekt, tjene penger |
| **Product Features** | levering, Connect, langtidsleie, forsikring |
| **Seasonal** | sommer, vinter, jul, påske, nordlys, 17. mai |
| **Road Trips** | roadtrip, kjøretur, rute, destinasjon |
| **Comparison** | vs, sammenligning, beste, alternativ |

### Format Categories

| Format | Pattern |
|--------|---------|
| **Listicle** | "Topp X", "X beste", "X ting" |
| **Comprehensive Guide** | "Komplett guide", "Alt du trenger" |
| **How-to** | "Hvordan...", "Slik..." |
| **Question-based** | Title starts with question |
| **Year-stamped** | Contains 2024, 2025 |
| **Case Study** | Person name, "møt", "historien om" |
| **Standard Article** | None of the above |

---

## Classification Table Template

```markdown
| Rank | URL | Title | Content Type | Format | Biz Fit | Impressions | Clicks | CTR |
|------|-----|-------|--------------|--------|---------|-------------|--------|-----|
| 1 | | | | | | | | |
```

**Business Fit Score:**
- 5 = Direct rental intent ("lei bil til bryllup")
- 4 = Activity requiring car ("roadtrip fra Oslo")
- 3 = May need car ("aktiviteter i Bergen")
- 2 = Tangential ("tips for biltur")
- 1 = Vanity traffic ("skifte vinterdekk")

---

## Output: Add to NORWAY_BLOG_ANALYSIS_2025.md

```markdown
## Content Classification Results

### Content Type Distribution
| Content Type | # Articles | % | Total Impressions | Avg CTR |
|--------------|------------|---|-------------------|---------|
| Activities/Leisure | | | | |
| Family | | | | |
| Nature/Outdoor | | | | |
| City Guides | | | | |
| How-to | | | | |
| Owner/Supply | | | | |
| Product Features | | | | |
| Seasonal | | | | |
| Road Trips | | | | |
| Comparison | | | | |

### Format Distribution
| Format | # Articles | % | Avg Impressions | Avg CTR |
|--------|------------|---|-----------------|---------|
| Listicle | | | | |
| Comprehensive Guide | | | | |
| How-to | | | | |
| Question-based | | | | |
| Year-stamped | | | | |
| Case Study | | | | |
| Standard Article | | | | |

### City Distribution
| City | # Articles | Impressions | % of City Content |
|------|------------|-------------|-------------------|
| Oslo | | | |
| Bergen | | | |
| Tromsø | | | |
| Stavanger | | | |
| Trondheim | | | |
| Other | | | |

### Business Fit Analysis
| Score | # Articles | % | Avg CTR |
|-------|------------|---|---------|
| 5 (High intent) | | | |
| 4 (Good intent) | | | |
| 3 (Medium) | | | |
| 2 (Low) | | | |
| 1 (Vanity) | | | |
```

---

## Completion Checklist
- [ ] 100 articles classified
- [ ] All distribution tables completed
- [ ] City breakdown documented
- [ ] Business fit analyzed
- [ ] ROADMAP.md updated
