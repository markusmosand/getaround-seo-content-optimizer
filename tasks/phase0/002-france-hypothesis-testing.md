# Task 002: France Blog - Hypothesis Testing

## Status: [ ] Todo

## Prerequisites
- Task 000 (GSC extraction) completed
- Task 001 (Content classification) completed

## Objective
Test our assumptions about the France market against actual data.

---

## Hypotheses to Test

### H1: B2B Content Dominates (>50% of traffic)
**Assumption:** France blog is primarily B2B/professional focused (60% of content).

**Test Method:**
- Sum impressions for all B2B/Professional classified articles
- Calculate % of total impressions

**Metrics:**
| Metric | Expected | Actual | Verdict |
|--------|----------|--------|---------|
| B2B % of articles | 60% | | |
| B2B % of impressions | >50% | | |
| B2B % of clicks | >50% | | |

**Verdict:** ⬜ CONFIRMED / ⬜ REJECTED / ⬜ PARTIAL

---

### H2: Regulatory Content Performs Well
**Assumption:** ZFE, Crit'Air, and regulatory content has above-average CTR due to high user intent.

**Test Method:**
- Calculate average CTR for regulatory content
- Compare to overall blog average CTR

**Metrics:**
| Metric | Overall Blog | Regulatory | Difference |
|--------|--------------|------------|------------|
| Average CTR | | | |
| Average Position | | | |
| Total Impressions | | | |

**Verdict:** ⬜ CONFIRMED / ⬜ REJECTED / ⬜ PARTIAL

---

### H3: Professional Guides Outperform Listicles
**Assumption:** "Guide complet" format performs better than listicles in France.

**Test Method:**
- Compare average impressions and CTR between formats
- Control for content type

**Metrics:**
| Format | # Articles | Avg Impressions | Avg CTR | Avg Position |
|--------|------------|-----------------|---------|--------------|
| Comprehensive Guide | | | | |
| Listicle | | | | |
| How-to | | | | |

**Best Format:** ____________________

**Verdict:** ⬜ CONFIRMED / ⬜ REJECTED / ⬜ PARTIAL

---

### H4: Paris Dominates City Content (>50%)
**Assumption:** Paris-related content drives majority of city guide traffic.

**Test Method:**
- Filter articles containing "Paris" in URL/title
- Calculate % of city guide impressions

**Metrics:**
| City | # Articles | Impressions | % of City Content |
|------|------------|-------------|-------------------|
| Paris | | | |
| Lyon | | | |
| Marseille | | | |
| Bordeaux | | | |
| Nice | | | |
| Other | | | |

**Verdict:** ⬜ CONFIRMED / ⬜ REJECTED / ⬜ PARTIAL

---

### H5: Year-Stamped Content Has Better Position
**Assumption:** Articles with year (2024, 2025) in title rank better due to freshness signals.

**Test Method:**
- Compare average position of year-stamped vs non-year-stamped articles

**Metrics:**
| Type | # Articles | Avg Position | Avg CTR |
|------|------------|--------------|---------|
| Year-stamped | | | |
| Not year-stamped | | | |

**Verdict:** ⬜ CONFIRMED / ⬜ REJECTED / ⬜ PARTIAL

---

### H6: B2C Travel Content is Underserved
**Assumption:** Consumer travel/leisure content exists but is not prioritized, potentially missing opportunity.

**Test Method:**
- Identify B2C content in top 100
- Assess CTR vs B2B content
- Look for high-impression/low-click B2C opportunities

**Findings:**
| B2C Article | Impressions | Clicks | CTR | Opportunity? |
|-------------|-------------|--------|-----|--------------|
| | | | | |

**Verdict:** ⬜ CONFIRMED / ⬜ REJECTED / ⬜ PARTIAL

---

## Summary Table

| Hypothesis | Expected | Actual | Verdict | Implication |
|------------|----------|--------|---------|-------------|
| H1: B2B >50% | 60% B2B | | | |
| H2: Regulatory high CTR | Above avg | | | |
| H3: Guides > Listicles | Guides win | | | |
| H4: Paris >50% cities | Dominant | | | |
| H5: Year-stamp helps | Better pos | | | |
| H6: B2C underserved | Opportunity | | | |

---

## Strategic Implications

Based on hypothesis results, document:

### If H1 REJECTED (B2B not dominant):
- Revise content strategy to reflect actual traffic sources
- Update skill prompts for France market
- Reconsider B2B-first approach

### If H2 REJECTED (Regulatory underperforms):
- Investigate why (competition? wrong keywords? format?)
- Consider reducing regulatory content focus
- Look at what IS working

### If H3 REJECTED (Listicles win):
- Shift France format recommendations toward listicles
- Update translator skill tone guidance
- Test listicle format for professional topics

### Key Strategy Changes Required:
1. ____________________
2. ____________________
3. ____________________

---

## Completion Checklist
- [ ] All 6 hypotheses tested
- [ ] Verdict marked for each
- [ ] Strategic implications documented
- [ ] Skill update recommendations created
- [ ] ROADMAP.md updated

## Surprising Findings
[Document anything unexpected here - these are the most valuable insights]
