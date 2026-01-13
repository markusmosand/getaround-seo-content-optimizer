# MCP Tools Inventory

## Status

| Status | Details |
|--------|---------|
| **Inventory Date** | 2026-01-07 |
| **Connection Status** | All tools tested |
| **Relevance** | Critical for workflow automation |

---

## Available MCP Servers

### 1. Google Search Console (gsc)

**Server:** `mcp__gsc__*`
**Status:** Connected
**Use Case:** SEO performance data extraction

#### Available Properties

| Property | Permission | Market |
|----------|------------|--------|
| sc-domain:no.getaround.com | siteFullUser | Norway |
| sc-domain:fr.getaround.com | siteFullUser | France |
| sc-domain:es.getaround.com | siteFullUser | Spain |
| sc-domain:de.getaround.com | siteFullUser | Germany |
| sc-domain:at.getaround.com | siteFullUser | Austria |
| sc-domain:be.getaround.com | siteFullUser | Belgium |
| sc-domain:fr.be.getaround.com | siteFullUser | Belgium (FR) |
| sc-domain:getaround.com | siteFullUser | Global |

#### Key Tools

| Tool | Purpose | Use Case |
|------|---------|----------|
| `list_properties` | List all GSC properties | Initial setup |
| `get_search_analytics` | Basic search data | Quick reports |
| `get_advanced_search_analytics` | Filtered, sorted data | Deep analysis |
| `compare_search_periods` | Period comparison | Trend analysis |
| `get_performance_overview` | Summary metrics | Dashboards |
| `get_search_by_page_query` | Page-level queries | Content optimization |
| `inspect_url_enhanced` | URL indexing status | Technical SEO |
| `batch_url_inspection` | Bulk URL checks | Audits |
| `check_indexing_issues` | Indexing problems | Debugging |
| `manage_sitemaps` | Sitemap operations | Technical SEO |

#### Tested Query Pattern

```
mcp__gsc__get_advanced_search_analytics
  site_url: "sc-domain:no.getaround.com"
  start_date: "2025-01-01"
  end_date: "2025-12-31"
  dimensions: "page"
  filter_dimension: "page"
  filter_operator: "contains"
  filter_expression: "/blogg/"
  row_limit: 500
  sort_by: "clicks"
  sort_direction: "descending"
```

---

### 2. n8n MCP Tools (n8n-mcp)

**Server:** `mcp__n8n-mcp__*`
**Status:** Connected
**Use Case:** Workflow building and automation

#### Tool Categories (19 Tools)

**Discovery:**
| Tool | Purpose | Performance |
|------|---------|-------------|
| `search_nodes` | Find n8n nodes by keyword | Instant (<10ms) |

**Configuration:**
| Tool | Purpose | Performance |
|------|---------|-------------|
| `get_node` | Get node info (minimal/standard/full) | Instant-Fast |

**Validation:**
| Tool | Purpose | Performance |
|------|---------|-------------|
| `validate_node` | Validate node config | Fast (<100ms) |
| `validate_workflow` | Validate entire workflow | Moderate |

**Templates:**
| Tool | Purpose | Performance |
|------|---------|-------------|
| `get_template` | Get workflow by ID | Fast |
| `search_templates` | Search workflow templates | Fast |

**n8n API (13 tools):**
| Tool | Purpose |
|------|---------|
| `n8n_create_workflow` | Create new workflows |
| `n8n_get_workflow` | Retrieve workflow details |
| `n8n_update_full_workflow` | Full workflow replacement |
| `n8n_update_partial_workflow` | Incremental updates |
| `n8n_delete_workflow` | Remove workflow |
| `n8n_list_workflows` | List all workflows |
| `n8n_validate_workflow` | Validate by ID |
| `n8n_autofix_workflow` | Auto-fix issues |
| `n8n_test_workflow` | Test/trigger workflows |
| `n8n_executions` | Execution management |
| `n8n_health_check` | API connectivity check |
| `n8n_workflow_versions` | Version history |
| `n8n_deploy_template` | Deploy from templates |

#### Workflow Building Pattern

```
1. search_nodes({query: "slack"})
2. get_node({nodeType: "nodes-base.slack", detail: "standard"})
3. validate_node({nodeType: "nodes-base.slack", config: {...}})
4. validate_workflow({workflow: {...}})
5. n8n_create_workflow({...})
```

---

### 3. Fiken Accounting (fiken)

**Server:** `mcp__fiken__*`
**Status:** Connected
**Use Case:** Financial operations (not SEO-related)

#### Company Connected

| Field | Value |
|-------|-------|
| Company | TWAIN AS |
| Org Number | 932602326 |
| API Access | Yes |

**Note:** This is for accounting, not relevant to SEO automation project.

---

### 4. Figma (figma)

**Server:** `mcp__figma__*`
**Status:** Available
**Use Case:** Design asset extraction

#### Key Tools

| Tool | Purpose |
|------|---------|
| `get_screenshot` | Generate node screenshots |
| `get_design_context` | Extract UI code |
| `get_metadata` | Get layer structure |
| `generate_diagram` | Create flowcharts |

**Relevance:** Medium - useful for documentation visuals.

---

## Tools Relevant to SEO Automation

### Critical Tools

| Tool | Server | Use in Workflow |
|------|--------|-----------------|
| `get_advanced_search_analytics` | gsc | Research workflow data |
| `compare_search_periods` | gsc | Trend analysis |
| `search_nodes` | n8n-mcp | Find integration nodes |
| `get_node` | n8n-mcp | Configure nodes |
| `validate_workflow` | n8n-mcp | Pre-deployment checks |
| `n8n_create_workflow` | n8n-mcp | Deploy workflows |

### Supporting Tools

| Tool | Server | Use in Workflow |
|------|--------|-----------------|
| `inspect_url_enhanced` | gsc | Technical SEO checks |
| `get_search_by_page_query` | gsc | Content optimization |
| `search_templates` | n8n-mcp | Find example workflows |
| `n8n_test_workflow` | n8n-mcp | Testing automation |

---

## Integration Gaps

### Available via MCP
- Google Search Console
- n8n Cloud
- Figma (design)
- Fiken (accounting)

### NOT Available (Manual Only)
| Integration | Status | Workaround |
|-------------|--------|------------|
| Semrush | No MCP | Manual CSV export |
| Ghost CMS | No MCP | API integration via n8n |
| GA4 | No MCP | Manual export / BigQuery |
| Slack | No MCP | n8n Slack node |
| OpenAI/Claude | No MCP | n8n AI nodes |

### Recommended Additions
1. **Semrush MCP** - Would enable automated keyword research
2. **Ghost CMS MCP** - Would enable direct publishing
3. **GA4 MCP** - Would enable traffic correlation

---

## Usage Patterns for Workflows

### Research Workflow (Weekly)

```
GSC Tools Used:
├── get_advanced_search_analytics (pages by impressions)
├── get_advanced_search_analytics (queries by clicks)
├── compare_search_periods (week-over-week)
└── get_search_by_page_query (top pages)
```

### Planning Workflow

```
GSC Tools Used:
├── get_search_analytics (CTR gaps)
└── get_advanced_search_analytics (position opportunities)

n8n Tools Used:
├── search_nodes (find AI nodes)
└── get_node (configure Claude/OpenAI)
```

### Monitoring Workflow

```
GSC Tools Used:
├── compare_search_periods (performance tracking)
├── inspect_url_enhanced (indexing status)
└── check_indexing_issues (new content)
```

---

## Rate Limits & Considerations

### GSC API
- 1,200 queries per minute per project
- 25,000 rows max per query
- 24-48 hour data lag

### n8n API
- Depends on n8n Cloud plan
- Execution limits apply
- Webhook rate limits

### Best Practices
1. Batch GSC queries where possible
2. Use caching for repeated queries
3. Schedule heavy operations off-peak
4. Monitor API quota usage

---

*Inventory Generated: 2026-01-07*
*Next Update: When new MCP servers added*
