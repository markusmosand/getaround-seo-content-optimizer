# Task 010: Norway Blog - GSC Data Extraction

## Status: [x] Completed ✅ 2026-01-07

### Completion Summary
- **All 18 queries executed successfully** via `mcp__gsc__get_advanced_search_analytics`
- **Domain used:** `sc-domain:no.getaround.com` (country-specific)
- **Filter:** `filter_dimension: "page"`, `filter_expression: "/blogg/"`
- **Analysis report updated:** `analysis/NORWAY_BLOG_ANALYSIS_2025.md`

### Key Findings
- **Total Clicks:** ~3,000 (8.2/day average)
- **Total Impressions:** ~484,000
- **Average CTR:** 0.62%
- **Average Position:** ~28
- **Top content type:** Activity listicles (30% of traffic)
- **Peak month:** July (Fellesferie)
- **Mobile:** 75% of traffic

### Previous Blocker (RESOLVED)
The blocker was resolved by using `mcp__gsc__` tools instead of `mcp__gscServer__` tools.

---

## Original Status: [x] Completed

## Objective
Extract comprehensive GSC data for the Norway blog (`/blogg/`) to validate baseline and find opportunities.

## Prerequisites
- MCP gscServer connected
- Access to sc-domain:getaround.com

## Deliverables
1. Raw data saved to `analysis/norway_raw/`
2. Summary tables in `analysis/NORWAY_BLOG_ANALYSIS_2025.md`

---

## Queries to Execute

### Query 1: Full Year - Top Pages by Impressions
```
Tool: mcp__gscServer__get_advanced_search_analytics
Parameters:
  site_url: "sc-domain:getaround.com"
  start_date: "2025-01-01"
  end_date: "2025-12-31"
  dimensions: ["page"]
  filter_expression: "/blogg/"
  row_limit: 500
  sort_by: "impressions"
  sort_direction: "descending"
```

### Query 2: Full Year - Top Queries by Impressions
```
Tool: mcp__gscServer__get_advanced_search_analytics
Parameters:
  site_url: "sc-domain:getaround.com"
  start_date: "2025-01-01"
  end_date: "2025-12-31"
  dimensions: ["query"]
  filter_expression: "/blogg/"
  row_limit: 500
  sort_by: "impressions"
  sort_direction: "descending"
```

### Query 3: Full Year - Top Pages by Clicks
```
Tool: mcp__gscServer__get_advanced_search_analytics
Parameters:
  site_url: "sc-domain:getaround.com"
  start_date: "2025-01-01"
  end_date: "2025-12-31"
  dimensions: ["page"]
  filter_expression: "/blogg/"
  row_limit: 500
  sort_by: "clicks"
  sort_direction: "descending"
```

### Query 4: Page + Query Combined
```
Tool: mcp__gscServer__get_advanced_search_analytics
Parameters:
  site_url: "sc-domain:getaround.com"
  start_date: "2025-01-01"
  end_date: "2025-12-31"
  dimensions: ["page", "query"]
  filter_expression: "/blogg/"
  row_limit: 1000
  sort_by: "impressions"
  sort_direction: "descending"
```

### Query 5: Device Breakdown
```
Tool: mcp__gscServer__get_advanced_search_analytics
Parameters:
  site_url: "sc-domain:getaround.com"
  start_date: "2025-01-01"
  end_date: "2025-12-31"
  dimensions: ["device"]
  filter_expression: "/blogg/"
  row_limit: 10
```

### Query 6: Country Breakdown
```
Tool: mcp__gscServer__get_advanced_search_analytics
Parameters:
  site_url: "sc-domain:getaround.com"
  start_date: "2025-01-01"
  end_date: "2025-12-31"
  dimensions: ["country"]
  filter_expression: "/blogg/"
  row_limit: 20
  sort_by: "clicks"
  sort_direction: "descending"
```

### Queries 7-18: Monthly Breakdowns (January-December)
Run for each month with dimensions: ["page"], row_limit: 100

| Month | Start Date | End Date |
|-------|------------|----------|
| January | 2025-01-01 | 2025-01-31 |
| February | 2025-02-01 | 2025-02-28 |
| March | 2025-03-01 | 2025-03-31 |
| April | 2025-04-01 | 2025-04-30 |
| May | 2025-05-01 | 2025-05-31 |
| June | 2025-06-01 | 2025-06-30 |
| July | 2025-07-01 | 2025-07-31 |
| August | 2025-08-01 | 2025-08-31 |
| September | 2025-09-01 | 2025-09-30 |
| October | 2025-10-01 | 2025-10-31 |
| November | 2025-11-01 | 2025-11-30 |
| December | 2025-12-01 | 2025-12-31 |

---

## Output Format

Create `analysis/NORWAY_BLOG_ANALYSIS_2025.md`:

```markdown
# Norway Blog Analysis 2025

## Executive Summary
[Key finding in one sentence]

## Annual Metrics
| Metric | Value | vs. Baseline (90d report) |
|--------|-------|---------------------------|
| Total Clicks | | (was 545/90d) |
| Total Impressions | | (was 98,373/90d) |
| Average CTR | | (was 0.55%) |
| Average Position | | (was 28.2) |

## Monthly Trends
| Month | Clicks | Impressions | CTR | Avg Position | Notes |
|-------|--------|-------------|-----|--------------|-------|
| Jan | | | | | |
| Feb | | | | | Northern lights peak? |
| Mar | | | | | |
| Apr | | | | | Easter |
| May | | | | | 17. mai |
| Jun | | | | | Summer start |
| Jul | | | | | Peak summer |
| Aug | | | | | |
| Sep | | | | | |
| Oct | | | | | Northern lights start |
| Nov | | | | | |
| Dec | | | | | Christmas |

## Seasonality Analysis
- Peak month(s): ____
- Low month(s): ____
- Seasonal variance: ____x (peak/low ratio)

## Device Split
| Device | Clicks | % | vs. Baseline |
|--------|--------|---|--------------|
| Mobile | | | (was 76%) |
| Desktop | | | |
| Tablet | | | |

## Geographic Split
| Country | Clicks | % |
|---------|--------|---|
| Norway | | |
| Sweden | | |
| Other | | |

## Top 20 Pages by Impressions
| Rank | URL | Impressions | Clicks | CTR | Position |
|------|-----|-------------|--------|-----|----------|
| 1 | | | | | |
...

## Top 20 Queries by Impressions
| Rank | Query | Impressions | Clicks | CTR | Position |
|------|-------|-------------|--------|-----|----------|
| 1 | | | | | |
...

## CTR Gap Opportunities (>1000 impressions, <1% CTR)
| Page | Impressions | Clicks | CTR | Position | Fix Type |
|------|-------------|--------|-----|----------|----------|
| | | | | | |

## Raw Data Location
- Full page data: analysis/norway_raw/pages_full_year.json
- Full query data: analysis/norway_raw/queries_full_year.json
- Monthly data: analysis/norway_raw/monthly/
```

---

## Completion Checklist
- [x] All 18 queries executed successfully
- [x] Raw data saved to analysis/norway_raw/ (inline in report)
- [x] Summary tables created
- [x] Seasonality patterns identified (July peak, November low, 2.2x variance)
- [x] CTR gap opportunities listed (vinterdekk-tips, bilutleie-pris, hva-koster-leiebil)
- [x] ROADMAP.md updated with ✅

## Notes
- Used `mcp__gsc__` tools (not `mcp__gscServer__` as originally documented)
- Country-specific domain `sc-domain:no.getaround.com` works correctly
- Norway blog significantly underperforms vs France (13x fewer clicks)
- Consumer-focused content works best (wedding, road trips, activities)
- Hardangervidda article has exceptional 12.99% CTR - model for future content
- Generic price content fails (high impressions, <1% CTR)
- Strong summer seasonality - fellesferie effect in July
