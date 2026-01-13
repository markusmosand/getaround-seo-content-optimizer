# Task 102: MCP Tools Inventory

## Status: [x] Completed ✅ 2026-01-07

## Objective
Test and document all available MCP tools for use in workflow design.

## Output
`docs/MCP_TOOLS_INVENTORY.md`

## Summary

### Connected MCP Servers

| Server | Tools | Status | Relevance |
|--------|-------|--------|-----------|
| **gsc** | 15+ | Connected | Critical |
| **n8n-mcp** | 19 | Connected | Critical |
| **figma** | 8 | Connected | Low |
| **fiken** | 20+ | Connected | None (accounting) |

### GSC Properties Available

| Property | Market |
|----------|--------|
| sc-domain:no.getaround.com | Norway |
| sc-domain:fr.getaround.com | France |
| sc-domain:es.getaround.com | Spain |
| sc-domain:de.getaround.com | Germany |
| sc-domain:at.getaround.com | Austria |
| sc-domain:be.getaround.com | Belgium |

### Critical Tools for Workflows

**Research Workflow:**
- `mcp__gsc__get_advanced_search_analytics` - Core data extraction
- `mcp__gsc__compare_search_periods` - Trend analysis
- `mcp__gsc__get_search_by_page_query` - Content optimization

**Planning Workflow:**
- `mcp__n8n-mcp__search_nodes` - Find integration nodes
- `mcp__n8n-mcp__get_node` - Configure AI nodes

**Monitoring Workflow:**
- `mcp__gsc__inspect_url_enhanced` - Indexing status
- `mcp__gsc__check_indexing_issues` - Technical SEO

**Deployment:**
- `mcp__n8n-mcp__validate_workflow` - Pre-deployment checks
- `mcp__n8n-mcp__n8n_create_workflow` - Deploy to n8n

### Integration Gaps

| Integration | Status | Impact |
|-------------|--------|--------|
| Semrush | Manual only | Limited keyword research automation |
| Ghost CMS | Manual only | No direct publishing |
| GA4 | Manual only | No traffic correlation |
| Slack | Via n8n node | Notifications possible |

### Key Learning: Domain Structure

**Working Pattern:**
```
site_url: "sc-domain:no.getaround.com"  # Country-specific
filter_dimension: "page"
filter_expression: "/blogg/"
```

**NOT:**
```
site_url: "sc-domain:getaround.com"  # Main domain doesn't have blog data
```

## Recommendations

1. Use country-specific GSC properties (no., fr., etc.)
2. Always use filter_dimension + filter_expression for blog data
3. Leverage n8n template search for workflow patterns
4. Consider future Semrush MCP for keyword automation
