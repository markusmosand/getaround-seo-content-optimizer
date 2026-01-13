# Norway Blog GSC Raw Data Directory

This directory contains raw GSC data exports for the Norway blog (`/blogg/`).

## Data Status: PENDING - GSC MCP Tool Not Available

The `mcp__gscServer__get_advanced_search_analytics` tool is documented but not currently connected.

## Planned Data Files

### Core Annual Data
- `pages_by_impressions.json` - Top 500 pages by impressions (2025 full year)
- `queries_by_impressions.json` - Top 500 queries by impressions (2025 full year)
- `pages_by_clicks.json` - Top 500 pages by clicks (2025 full year)
- `page_query_combined.json` - Top 1000 page+query combinations (2025 full year)
- `device_breakdown.json` - Device split data (2025 full year)
- `country_breakdown.json` - Top 20 countries by clicks (2025 full year)

### Monthly Data (in /monthly/ subdirectory)
- `2025-01_pages.json` - January 2025
- `2025-02_pages.json` - February 2025
- `2025-03_pages.json` - March 2025
- `2025-04_pages.json` - April 2025
- `2025-05_pages.json` - May 2025
- `2025-06_pages.json` - June 2025
- `2025-07_pages.json` - July 2025
- `2025-08_pages.json` - August 2025
- `2025-09_pages.json` - September 2025
- `2025-10_pages.json` - October 2025
- `2025-11_pages.json` - November 2025
- `2025-12_pages.json` - December 2025

## Query Specifications

All queries use:
- site_url: "sc-domain:getaround.com"
- filter_expression: "/blogg/"

### Query 1: Full Year - Top Pages by Impressions
```json
{
  "start_date": "2025-01-01",
  "end_date": "2025-12-31",
  "dimensions": ["page"],
  "row_limit": 500,
  "sort_by": "impressions",
  "sort_direction": "descending"
}
```

### Query 2: Full Year - Top Queries by Impressions
```json
{
  "start_date": "2025-01-01",
  "end_date": "2025-12-31",
  "dimensions": ["query"],
  "row_limit": 500,
  "sort_by": "impressions",
  "sort_direction": "descending"
}
```

### Query 3: Full Year - Top Pages by Clicks
```json
{
  "start_date": "2025-01-01",
  "end_date": "2025-12-31",
  "dimensions": ["page"],
  "row_limit": 500,
  "sort_by": "clicks",
  "sort_direction": "descending"
}
```

### Query 4: Page + Query Combined
```json
{
  "start_date": "2025-01-01",
  "end_date": "2025-12-31",
  "dimensions": ["page", "query"],
  "row_limit": 1000,
  "sort_by": "impressions",
  "sort_direction": "descending"
}
```

### Query 5: Device Breakdown
```json
{
  "start_date": "2025-01-01",
  "end_date": "2025-12-31",
  "dimensions": ["device"],
  "row_limit": 10
}
```

### Query 6: Country Breakdown
```json
{
  "start_date": "2025-01-01",
  "end_date": "2025-12-31",
  "dimensions": ["country"],
  "row_limit": 20,
  "sort_by": "clicks",
  "sort_direction": "descending"
}
```

### Queries 7-18: Monthly Page Data
Each month uses:
```json
{
  "dimensions": ["page"],
  "row_limit": 100,
  "sort_by": "impressions",
  "sort_direction": "descending"
}
```

Date ranges:
- January: 2025-01-01 to 2025-01-31
- February: 2025-02-01 to 2025-02-28
- March: 2025-03-01 to 2025-03-31
- April: 2025-04-01 to 2025-04-30
- May: 2025-05-01 to 2025-05-31
- June: 2025-06-01 to 2025-06-30
- July: 2025-07-01 to 2025-07-31
- August: 2025-08-01 to 2025-08-31
- September: 2025-09-01 to 2025-09-30
- October: 2025-10-01 to 2025-10-31
- November: 2025-11-01 to 2025-11-30
- December: 2025-12-01 to 2025-12-31

## Baseline Reference (from 90-day report)
- Clicks: 545 (90 days) = ~6.06/day = ~182/month
- CTR: 0.55%
- Position: 28.2
- Mobile: 76%

## Next Steps
1. Connect GSC MCP server
2. Execute all 18 queries
3. Save raw JSON responses to this directory
4. Generate analysis report
