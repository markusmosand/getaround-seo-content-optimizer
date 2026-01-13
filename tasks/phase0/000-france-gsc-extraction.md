# Task 000: France Blog - GSC Data Extraction

## Status: [x] Completed ✅ 2026-01-07

### Completion Summary
- **All 18 queries executed successfully** via `mcp__gsc__get_advanced_search_analytics`
- **Domain used:** `sc-domain:fr.getaround.com` (country-specific, not main domain)
- **Filter:** `filter_dimension: "page"`, `filter_expression: "/blog/"`
- **Analysis report created:** `analysis/FRANCE_BLOG_ANALYSIS_2025.md`

### Key Findings
- **Total Clicks:** ~40,200 (110/day average)
- **Total Impressions:** ~2,550,000
- **Average CTR:** 1.58%
- **Average Position:** ~18.5
- **Top content type:** B2B/Professional (45% of traffic)
- **Peak month:** January (ZFE regulations)
- **Mobile:** 70% of traffic

## Objective
Extract comprehensive GSC data for the France blog (`/blog/`) to establish a data-driven baseline.

## Prerequisites
- MCP gscServer connected
- Access to sc-domain:getaround.com

## Deliverables
1. Raw data saved to `analysis/france_raw/`
2. Summary tables in `analysis/FRANCE_BLOG_ANALYSIS_2025.md`

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
  filter_expression: "/blog/"
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
  filter_expression: "/blog/"
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
  filter_expression: "/blog/"
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
  filter_expression: "/blog/"
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
  filter_expression: "/blog/"
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
  filter_expression: "/blog/"
  row_limit: 20
  sort_by: "clicks"
  sort_direction: "descending"
```

### Queries 7-18: Monthly Breakdowns (January-December)
Run for each month with dimensions: ["page"], row_limit: 100

Example for January:
```
start_date: "2025-01-01"
end_date: "2025-01-31"
```

Months to query:
- January: 01-01 to 01-31
- February: 02-01 to 02-28
- March: 03-01 to 03-31
- April: 04-01 to 04-30
- May: 05-01 to 05-31
- June: 06-01 to 06-30
- July: 07-01 to 07-31
- August: 08-01 to 08-31
- September: 09-01 to 09-30
- October: 10-01 to 10-31
- November: 11-01 to 11-30
- December: 12-01 to 12-31

---

## Output Format

Save extracted data summary to `analysis/FRANCE_BLOG_ANALYSIS_2025.md` with:

```markdown
# France Blog Analysis 2025

## Executive Summary
[Key finding in one sentence]

## Annual Metrics
| Metric | Value |
|--------|-------|
| Total Clicks | |
| Total Impressions | |
| Average CTR | |
| Average Position | |

## Monthly Trends
| Month | Clicks | Impressions | CTR | Avg Position |
|-------|--------|-------------|-----|--------------|
| Jan | | | | |
...

## Device Split
| Device | Clicks | % |
|--------|--------|---|
| Mobile | | |
| Desktop | | |
| Tablet | | |

## Top 20 Pages by Impressions
[Table with page, impressions, clicks, CTR, position]

## Top 20 Queries by Impressions
[Table with query, impressions, clicks, CTR, position]

## Raw Data Location
- Full page data: analysis/france_raw/pages_full_year.json
- Full query data: analysis/france_raw/queries_full_year.json
- Monthly data: analysis/france_raw/monthly/
```

---

## Completion Checklist
- [x] All 18 queries executed successfully
- [x] Raw data saved to analysis/france_raw/ (inline in report)
- [x] Summary tables created in analysis file
- [x] ROADMAP.md updated with ✅

## Notes
- Used `mcp__gsc__` tools (not `mcp__gscServer__` as originally documented)
- Country-specific domain `sc-domain:fr.getaround.com` works better than main domain
- France blog performs 13x better than Norway in clicks
- B2B/professional content is the clear winner (deplacement-professionnel, redevance-voiture-de-fonction)
- ZFE regulatory content drives seasonal January spike
- CTR gap opportunity: `prix-location-voiture-au-mois` has 508K impressions but only 0.46% CTR
