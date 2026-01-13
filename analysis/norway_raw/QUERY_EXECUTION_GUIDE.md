# Norway Blog GSC Query Execution Guide

## Prerequisites
- MCP gscServer must be connected
- Access to sc-domain:getaround.com verified

## Execution Instructions

When the `mcp__gscServer__get_advanced_search_analytics` tool is available, execute these 18 queries in order:

---

## Core Queries (1-6)

### Query 1: Full Year - Top Pages by Impressions
```
mcp__gscServer__get_advanced_search_analytics(
  site_url="sc-domain:getaround.com",
  start_date="2025-01-01",
  end_date="2025-12-31",
  dimensions=["page"],
  filter_expression="/blogg/",
  row_limit=500,
  sort_by="impressions",
  sort_direction="descending"
)
```
**Save to:** `analysis/norway_raw/pages_by_impressions.json`

---

### Query 2: Full Year - Top Queries by Impressions
```
mcp__gscServer__get_advanced_search_analytics(
  site_url="sc-domain:getaround.com",
  start_date="2025-01-01",
  end_date="2025-12-31",
  dimensions=["query"],
  filter_expression="/blogg/",
  row_limit=500,
  sort_by="impressions",
  sort_direction="descending"
)
```
**Save to:** `analysis/norway_raw/queries_by_impressions.json`

---

### Query 3: Full Year - Top Pages by Clicks
```
mcp__gscServer__get_advanced_search_analytics(
  site_url="sc-domain:getaround.com",
  start_date="2025-01-01",
  end_date="2025-12-31",
  dimensions=["page"],
  filter_expression="/blogg/",
  row_limit=500,
  sort_by="clicks",
  sort_direction="descending"
)
```
**Save to:** `analysis/norway_raw/pages_by_clicks.json`

---

### Query 4: Page + Query Combined
```
mcp__gscServer__get_advanced_search_analytics(
  site_url="sc-domain:getaround.com",
  start_date="2025-01-01",
  end_date="2025-12-31",
  dimensions=["page", "query"],
  filter_expression="/blogg/",
  row_limit=1000,
  sort_by="impressions",
  sort_direction="descending"
)
```
**Save to:** `analysis/norway_raw/page_query_combined.json`

---

### Query 5: Device Breakdown
```
mcp__gscServer__get_advanced_search_analytics(
  site_url="sc-domain:getaround.com",
  start_date="2025-01-01",
  end_date="2025-12-31",
  dimensions=["device"],
  filter_expression="/blogg/",
  row_limit=10
)
```
**Save to:** `analysis/norway_raw/device_breakdown.json`

---

### Query 6: Country Breakdown
```
mcp__gscServer__get_advanced_search_analytics(
  site_url="sc-domain:getaround.com",
  start_date="2025-01-01",
  end_date="2025-12-31",
  dimensions=["country"],
  filter_expression="/blogg/",
  row_limit=20,
  sort_by="clicks",
  sort_direction="descending"
)
```
**Save to:** `analysis/norway_raw/country_breakdown.json`

---

## Monthly Queries (7-18)

All monthly queries use:
- dimensions=["page"]
- row_limit=100
- sort_by="impressions"
- sort_direction="descending"

### Query 7: January 2025
```
start_date="2025-01-01", end_date="2025-01-31"
```
**Save to:** `analysis/norway_raw/monthly/2025-01_pages.json`

### Query 8: February 2025
```
start_date="2025-02-01", end_date="2025-02-28"
```
**Save to:** `analysis/norway_raw/monthly/2025-02_pages.json`

### Query 9: March 2025
```
start_date="2025-03-01", end_date="2025-03-31"
```
**Save to:** `analysis/norway_raw/monthly/2025-03_pages.json`

### Query 10: April 2025
```
start_date="2025-04-01", end_date="2025-04-30"
```
**Save to:** `analysis/norway_raw/monthly/2025-04_pages.json`

### Query 11: May 2025
```
start_date="2025-05-01", end_date="2025-05-31"
```
**Save to:** `analysis/norway_raw/monthly/2025-05_pages.json`

### Query 12: June 2025
```
start_date="2025-06-01", end_date="2025-06-30"
```
**Save to:** `analysis/norway_raw/monthly/2025-06_pages.json`

### Query 13: July 2025
```
start_date="2025-07-01", end_date="2025-07-31"
```
**Save to:** `analysis/norway_raw/monthly/2025-07_pages.json`

### Query 14: August 2025
```
start_date="2025-08-01", end_date="2025-08-31"
```
**Save to:** `analysis/norway_raw/monthly/2025-08_pages.json`

### Query 15: September 2025
```
start_date="2025-09-01", end_date="2025-09-30"
```
**Save to:** `analysis/norway_raw/monthly/2025-09_pages.json`

### Query 16: October 2025
```
start_date="2025-10-01", end_date="2025-10-31"
```
**Save to:** `analysis/norway_raw/monthly/2025-10_pages.json`

### Query 17: November 2025
```
start_date="2025-11-01", end_date="2025-11-30"
```
**Save to:** `analysis/norway_raw/monthly/2025-11_pages.json`

### Query 18: December 2025
```
start_date="2025-12-01", end_date="2025-12-31"
```
**Save to:** `analysis/norway_raw/monthly/2025-12_pages.json`

---

## Post-Execution Steps

1. **Validate Data Coverage**
   - Check that all months have data
   - Flag any gaps due to GSC 24-48h lag (especially December)
   - Calculate coverage percentage

2. **Update Analysis Report**
   - Fill in all [PENDING] fields in NORWAY_BLOG_ANALYSIS_2025.md
   - Calculate year totals and averages
   - Compare to baseline metrics
   - Identify CTR gap opportunities

3. **Generate Insights**
   - Monthly seasonality analysis
   - Device trend comparison
   - Geographic concentration
   - Content type performance

4. **Prioritize Actions**
   - Quick wins (position 1-10, low CTR)
   - Page 2 breakthroughs (position 11-15)
   - Content gaps to fill

---

## Expected Data Volume

| Query | Expected Rows | Notes |
|-------|---------------|-------|
| Pages by Impressions | ~100-200 | 211 total articles |
| Queries by Impressions | 500 | Full limit |
| Pages by Clicks | ~100-200 | Lower if traffic concentrated |
| Page+Query Combined | 1000 | Full limit |
| Device Breakdown | 3 | Mobile, Desktop, Tablet |
| Country Breakdown | 5-10 | Norway dominant |
| Monthly Pages | ~50-100 each | Variable by seasonality |

---

## Troubleshooting

### If tool returns empty:
1. Verify property access with `mcp__gscServer__list_properties`
2. Check filter expression is correct: `/blogg/` (not `/blog/`)
3. Verify date range is within GSC retention (16 months)

### If rows are fewer than expected:
1. Normal if blog has fewer pages
2. Check if filter is too restrictive
3. Some months may have genuinely lower traffic

### If December data is incomplete:
1. GSC has 24-48h lag
2. Note in analysis and update later
3. Calculate partial month metrics separately
