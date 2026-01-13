# Node Specifications: n8n Workflow Nodes

## Specification Status

| Status | Details |
|--------|---------|
| **Design Date** | 2026-01-07 |
| **Version** | 1.0 |
| **Platform** | n8n Cloud |
| **Node Types** | 15 unique types |

---

## Node Type Reference

### Core Nodes Used

| Node Type | Display Name | Use Case |
|-----------|--------------|----------|
| `n8n-nodes-base.scheduleTrigger` | Schedule Trigger | Weekly automation |
| `n8n-nodes-base.manualTrigger` | Manual Trigger | Ad-hoc runs |
| `n8n-nodes-base.httpRequest` | HTTP Request | GSC API, Ghost CMS |
| `n8n-nodes-base.googleSheets` | Google Sheets | Data storage |
| `n8n-nodes-base.googleSheetsTrigger` | Google Sheets Trigger | Queue processing |
| `n8n-nodes-base.slack` | Slack | Notifications |
| `n8n-nodes-base.if` | IF | Conditional logic |
| `n8n-nodes-base.switch` | Switch | Market routing |
| `n8n-nodes-base.set` | Set | Data transformation |
| `n8n-nodes-base.code` | Code | Custom logic |
| `n8n-nodes-base.merge` | Merge | Combine data |
| `@n8n/n8n-nodes-langchain.agent` | AI Agent | Content generation |
| `@n8n/n8n-nodes-langchain.lmChatAnthropic` | Anthropic Chat | Claude models |
| `@n8n/n8n-nodes-langchain.lmChatOpenAi` | OpenAI Chat | GPT fallback |
| `@n8n/n8n-nodes-langchain.outputParserStructured` | Output Parser | JSON extraction |

---

## Workflow 1: Research - Node Specifications

### Node 1.1: Schedule Trigger
```json
{
  "nodeType": "n8n-nodes-base.scheduleTrigger",
  "name": "Weekly Research Trigger",
  "parameters": {
    "rule": {
      "interval": [
        {
          "field": "weeks",
          "weeksInterval": 1,
          "triggerAtDay": ["monday"],
          "triggerAtHour": 6,
          "triggerAtMinute": 0
        }
      ]
    }
  }
}
```

### Node 1.2: HTTP Request - France GSC
```json
{
  "nodeType": "n8n-nodes-base.httpRequest",
  "name": "Get France Blog Data",
  "parameters": {
    "method": "POST",
    "url": "https://searchconsole.googleapis.com/webmasters/v3/sites/sc-domain%3Afr.getaround.com/searchAnalytics/query",
    "authentication": "oAuth2",
    "sendBody": true,
    "bodyParameters": {
      "parameters": [
        {
          "name": "startDate",
          "value": "={{ $now.minus(7, 'days').toFormat('yyyy-MM-dd') }}"
        },
        {
          "name": "endDate",
          "value": "={{ $now.minus(1, 'days').toFormat('yyyy-MM-dd') }}"
        },
        {
          "name": "dimensions",
          "value": ["page", "query"]
        },
        {
          "name": "dimensionFilterGroups",
          "value": [{
            "filters": [{
              "dimension": "page",
              "operator": "contains",
              "expression": "/blog/"
            }]
          }]
        },
        {
          "name": "rowLimit",
          "value": 500
        }
      ]
    }
  },
  "credentials": {
    "googleSearchConsoleOAuth2Api": "GSC-Getaround"
  }
}
```

### Node 1.3: HTTP Request - Norway GSC
```json
{
  "nodeType": "n8n-nodes-base.httpRequest",
  "name": "Get Norway Blog Data",
  "parameters": {
    "method": "POST",
    "url": "https://searchconsole.googleapis.com/webmasters/v3/sites/sc-domain%3Ano.getaround.com/searchAnalytics/query",
    "authentication": "oAuth2",
    "sendBody": true,
    "bodyParameters": {
      "parameters": [
        {
          "name": "startDate",
          "value": "={{ $now.minus(7, 'days').toFormat('yyyy-MM-dd') }}"
        },
        {
          "name": "endDate",
          "value": "={{ $now.minus(1, 'days').toFormat('yyyy-MM-dd') }}"
        },
        {
          "name": "dimensions",
          "value": ["page", "query"]
        },
        {
          "name": "dimensionFilterGroups",
          "value": [{
            "filters": [{
              "dimension": "page",
              "operator": "contains",
              "expression": "/blogg/"
            }]
          }]
        },
        {
          "name": "rowLimit",
          "value": 500
        }
      ]
    }
  },
  "credentials": {
    "googleSearchConsoleOAuth2Api": "GSC-Getaround"
  }
}
```

### Node 1.4: Code - Process Opportunities
```json
{
  "nodeType": "n8n-nodes-base.code",
  "name": "Identify Opportunities",
  "parameters": {
    "mode": "runOnceForAllItems",
    "jsCode": "// Combine France and Norway data\nconst franceData = $input.all()[0].json;\nconst norwayData = $input.all()[1].json;\n\n// CTR Gap Analysis\nfunction findCTRGaps(rows, market) {\n  return rows\n    .filter(r => r.impressions > 1000 && r.ctr < 0.01)\n    .map(r => ({\n      ...r,\n      market,\n      opportunity: 'ctr_gap',\n      potentialClicks: Math.round(r.impressions * 0.02 - r.clicks)\n    }))\n    .sort((a, b) => b.potentialClicks - a.potentialClicks)\n    .slice(0, 10);\n}\n\n// Position Opportunities (page 2 candidates)\nfunction findPositionOpps(rows, market) {\n  return rows\n    .filter(r => r.position >= 11 && r.position <= 20 && r.impressions > 500)\n    .map(r => ({\n      ...r,\n      market,\n      opportunity: 'position',\n      gapToPage1: r.position - 10\n    }))\n    .sort((a, b) => a.gapToPage1 - b.gapToPage1)\n    .slice(0, 10);\n}\n\nconst opportunities = {\n  france: {\n    ctrGaps: findCTRGaps(franceData.rows || [], 'france'),\n    positionOpps: findPositionOpps(franceData.rows || [], 'france')\n  },\n  norway: {\n    ctrGaps: findCTRGaps(norwayData.rows || [], 'norway'),\n    positionOpps: findPositionOpps(norwayData.rows || [], 'norway')\n  },\n  extractedAt: new Date().toISOString()\n};\n\nreturn [{ json: opportunities }];"
  }
}
```

### Node 1.5: Google Sheets - Save Report
```json
{
  "nodeType": "n8n-nodes-base.googleSheets",
  "name": "Save Weekly Report",
  "parameters": {
    "operation": "append",
    "documentId": "{{ $vars.SHEETS_RESEARCH_ID }}",
    "sheetName": "Weekly_Reports",
    "columns": {
      "mappingMode": "defineBelow",
      "value": {
        "Date": "={{ $now.toFormat('yyyy-MM-dd') }}",
        "France_CTR_Gaps": "={{ JSON.stringify($json.france.ctrGaps) }}",
        "France_Position_Opps": "={{ JSON.stringify($json.france.positionOpps) }}",
        "Norway_CTR_Gaps": "={{ JSON.stringify($json.norway.ctrGaps) }}",
        "Norway_Position_Opps": "={{ JSON.stringify($json.norway.positionOpps) }}"
      }
    }
  },
  "credentials": {
    "googleSheetsOAuth2Api": "Google-Sheets"
  }
}
```

### Node 1.6: Slack - Send Report
```json
{
  "nodeType": "n8n-nodes-base.slack",
  "name": "Send Weekly Report",
  "parameters": {
    "operation": "postMessage",
    "channel": "#seo-automation",
    "text": "📊 *Weekly SEO Research Report*\n\n*France:*\n• CTR Gaps: {{ $json.france.ctrGaps.length }} opportunities\n• Position Opps: {{ $json.france.positionOpps.length }} pages near page 1\n\n*Norway:*\n• CTR Gaps: {{ $json.norway.ctrGaps.length }} opportunities\n• Position Opps: {{ $json.norway.positionOpps.length }} pages near page 1\n\n📋 <{{ $vars.SHEETS_RESEARCH_URL }}|View Full Report>"
  },
  "credentials": {
    "slackApi": "Slack-Getaround"
  }
}
```

---

## Workflow 2: Planning - Node Specifications

### Node 2.1: Set - Market Context
```json
{
  "nodeType": "n8n-nodes-base.set",
  "name": "Set Market Context",
  "parameters": {
    "mode": "manual",
    "duplicateItem": false,
    "assignments": {
      "assignments": [
        {
          "name": "franceContext",
          "value": "You are creating content for Getaround France (fr.getaround.com/blog/). Target audience: B2B professionals and fleet managers. Tone: Formal 'vous', professional. Top content types: Professional vehicle displacement, ZFE regulations, company car tax (TVS/TVA), van road trips. Always include year in titles for regulatory content. Format preference: Detailed guides with calculations.",
          "type": "string"
        },
        {
          "name": "norwayContext",
          "value": "You are creating content for Getaround Norway (no.getaround.com/blogg/). Target audience: B2C consumers, families, outdoor enthusiasts. Tone: Informal 'du', friendly and inspiring. Top content types: Activity listicles, road trip itineraries, seasonal events (17. mai, fellesferie). Format preference: 'Topp 5/10' listicles, day-by-day itineraries. Focus on experiences that require renting a car.",
          "type": "string"
        }
      ]
    }
  }
}
```

### Node 2.2: Switch - Market Router
```json
{
  "nodeType": "n8n-nodes-base.switch",
  "name": "Route by Market",
  "parameters": {
    "dataType": "string",
    "value1": "={{ $json.market }}",
    "rules": {
      "rules": [
        {
          "value2": "france",
          "output": 0
        },
        {
          "value2": "norway",
          "output": 1
        }
      ]
    },
    "fallbackOutput": 2
  }
}
```

### Node 2.3: AI Agent - Topic Generation (France)
```json
{
  "nodeType": "@n8n/n8n-nodes-langchain.agent",
  "name": "Generate France Topics",
  "typeVersion": 3.1,
  "parameters": {
    "promptType": "define",
    "text": "Based on these SEO opportunities:\n\n{{ JSON.stringify($json.opportunities) }}\n\nGenerate 3 content topic proposals for the Getaround France blog.\n\nContext:\n{{ $node['Set Market Context'].json.franceContext }}\n\nFor each topic provide:\n1. Title (French, with year if regulatory)\n2. Target keyword\n3. Content type (B2B Guide / ZFE Update / Van Content / Owner Guide)\n4. Brief outline (3-5 bullet points)\n5. Business fit score (1-5, where 5 = high rental intent)\n6. Estimated search volume (Low/Medium/High based on impressions data)\n\nFormat as JSON array."
  },
  "connections": {
    "ai_languageModel": {
      "main": [[{ "node": "Claude Sonnet", "type": "main", "index": 0 }]]
    },
    "ai_outputParser": {
      "main": [[{ "node": "JSON Parser", "type": "main", "index": 0 }]]
    }
  }
}
```

### Node 2.4: AI Agent - Topic Generation (Norway)
```json
{
  "nodeType": "@n8n/n8n-nodes-langchain.agent",
  "name": "Generate Norway Topics",
  "typeVersion": 3.1,
  "parameters": {
    "promptType": "define",
    "text": "Based on these SEO opportunities:\n\n{{ JSON.stringify($json.opportunities) }}\n\nGenerate 3 content topic proposals for the Getaround Norway blog.\n\nContext:\n{{ $node['Set Market Context'].json.norwayContext }}\n\nFor each topic provide:\n1. Title (Norwegian)\n2. Target keyword\n3. Content type (Activity Listicle / Road Trip / Owner Guide / Seasonal)\n4. Brief outline (3-5 bullet points)\n5. Business fit score (1-5, where 5 = high rental intent)\n6. Estimated search volume (Low/Medium/High based on impressions data)\n\nFormat as JSON array."
  }
}
```

### Node 2.5: Anthropic Chat Model
```json
{
  "nodeType": "@n8n/n8n-nodes-langchain.lmChatAnthropic",
  "name": "Claude Sonnet",
  "parameters": {
    "model": "claude-sonnet-4-20250514",
    "temperature": 0.7,
    "maxTokens": 2000
  },
  "credentials": {
    "anthropicApi": "Anthropic-API"
  }
}
```

### Node 2.6: Structured Output Parser
```json
{
  "nodeType": "@n8n/n8n-nodes-langchain.outputParserStructured",
  "name": "JSON Parser",
  "parameters": {
    "schemaType": "manual",
    "schema": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "title": { "type": "string" },
          "targetKeyword": { "type": "string" },
          "contentType": { "type": "string" },
          "outline": { "type": "array", "items": { "type": "string" } },
          "businessFitScore": { "type": "number" },
          "searchVolume": { "type": "string" }
        },
        "required": ["title", "targetKeyword", "contentType", "outline", "businessFitScore"]
      }
    }
  }
}
```

### Node 2.7: Slack - Approval Request
```json
{
  "nodeType": "n8n-nodes-base.slack",
  "name": "Request Topic Approval",
  "parameters": {
    "operation": "postMessage",
    "channel": "#seo-content-approval",
    "text": "🆕 *New Topic Proposals - {{ $json.market | capitalize }}*\n\n{{ $json.topics.map((t, i) => `*${i+1}. ${t.title}*\n• Type: ${t.contentType}\n• Keyword: ${t.targetKeyword}\n• Business Fit: ${'⭐'.repeat(t.businessFitScore)}\n• Volume: ${t.searchVolume}`).join('\\n\\n') }}\n\nReact with ✅ to approve, ❌ to reject, or reply with changes."
  }
}
```

---

## Workflow 3: Writing - Node Specifications

### Node 3.1: Google Sheets Trigger - Queue
```json
{
  "nodeType": "n8n-nodes-base.googleSheetsTrigger",
  "name": "New Approved Topic",
  "parameters": {
    "documentId": "{{ $vars.SHEETS_CONTENT_QUEUE_ID }}",
    "sheetName": "Approved_Topics",
    "event": "rowAdded",
    "includeInOutput": "all"
  },
  "credentials": {
    "googleSheetsOAuth2Api": "Google-Sheets"
  }
}
```

### Node 3.2: AI Agent - Article Generation
```json
{
  "nodeType": "@n8n/n8n-nodes-langchain.agent",
  "name": "Generate Article Draft",
  "typeVersion": 3.1,
  "parameters": {
    "promptType": "define",
    "text": "Write a comprehensive SEO-optimized blog article based on this brief:\n\n**Title:** {{ $json.title }}\n**Target Keyword:** {{ $json.targetKeyword }}\n**Market:** {{ $json.market }}\n**Content Type:** {{ $json.contentType }}\n**Outline:**\n{{ $json.outline.map(item => '- ' + item).join('\\n') }}\n\n**Market Context:**\n{{ $json.market === 'france' ? $node['Set Market Context'].json.franceContext : $node['Set Market Context'].json.norwayContext }}\n\n**Requirements:**\n1. Length: 1200-1800 words\n2. Structure: Use H2 and H3 headings\n3. Include an FAQ section with 4-5 questions\n4. Start with a 2-3 sentence direct answer (for AI/featured snippets)\n5. Include a CTA mentioning Getaround at the end\n6. Use natural language, avoid keyword stuffing\n7. Include specific details, locations, or calculations where relevant\n8. Write in the appropriate language (French for France, Norwegian for Norway)\n\n**Output Format:**\nReturn the article in Markdown format with:\n- Title (H1)\n- All sections with proper headings\n- FAQ section using Q: and A: format\n- Meta description (150-160 characters)\n- Suggested internal links (2-3 relevant existing articles)"
  }
}
```

### Node 3.3: Anthropic Chat Model - Writing
```json
{
  "nodeType": "@n8n/n8n-nodes-langchain.lmChatAnthropic",
  "name": "Claude Opus",
  "parameters": {
    "model": "claude-opus-4-20250514",
    "temperature": 0.6,
    "maxTokens": 4000
  },
  "credentials": {
    "anthropicApi": "Anthropic-API"
  }
}
```

### Node 3.4: Code - Generate Schema
```json
{
  "nodeType": "n8n-nodes-base.code",
  "name": "Generate Schema Markup",
  "parameters": {
    "mode": "runOnceForEachItem",
    "jsCode": "const article = $input.item.json;\n\n// Extract FAQ from article\nconst faqRegex = /Q:\\s*(.+?)\\nA:\\s*(.+?)(?=\\nQ:|$)/gs;\nconst faqs = [];\nlet match;\nwhile ((match = faqRegex.exec(article.content)) !== null) {\n  faqs.push({\n    '@type': 'Question',\n    'name': match[1].trim(),\n    'acceptedAnswer': {\n      '@type': 'Answer',\n      'text': match[2].trim()\n    }\n  });\n}\n\n// FAQPage Schema\nconst faqSchema = {\n  '@context': 'https://schema.org',\n  '@type': 'FAQPage',\n  'mainEntity': faqs\n};\n\n// Article Schema\nconst articleSchema = {\n  '@context': 'https://schema.org',\n  '@type': 'Article',\n  'headline': article.title,\n  'description': article.metaDescription,\n  'author': {\n    '@type': 'Organization',\n    'name': 'Getaround'\n  },\n  'publisher': {\n    '@type': 'Organization',\n    'name': 'Getaround',\n    'logo': {\n      '@type': 'ImageObject',\n      'url': 'https://getaround.com/logo.png'\n    }\n  },\n  'datePublished': new Date().toISOString(),\n  'dateModified': new Date().toISOString()\n};\n\nreturn {\n  json: {\n    ...article,\n    schemas: {\n      faq: faqSchema,\n      article: articleSchema\n    }\n  }\n};"
  }
}
```

### Node 3.5: Google Sheets - Save Draft
```json
{
  "nodeType": "n8n-nodes-base.googleSheets",
  "name": "Save Draft",
  "parameters": {
    "operation": "append",
    "documentId": "{{ $vars.SHEETS_DRAFTS_ID }}",
    "sheetName": "Drafts",
    "columns": {
      "mappingMode": "defineBelow",
      "value": {
        "Date": "={{ $now.toFormat('yyyy-MM-dd') }}",
        "Title": "={{ $json.title }}",
        "Market": "={{ $json.market }}",
        "Content": "={{ $json.content }}",
        "Meta_Description": "={{ $json.metaDescription }}",
        "Schema_FAQ": "={{ JSON.stringify($json.schemas.faq) }}",
        "Schema_Article": "={{ JSON.stringify($json.schemas.article) }}",
        "Internal_Links": "={{ JSON.stringify($json.internalLinks) }}",
        "Status": "Pending Review"
      }
    }
  }
}
```

---

## Workflow 4: Review - Node Specifications

### Node 4.1: Code - Quality Checks
```json
{
  "nodeType": "n8n-nodes-base.code",
  "name": "Run Quality Checks",
  "parameters": {
    "mode": "runOnceForEachItem",
    "jsCode": "const draft = $input.item.json;\nconst checks = [];\nlet score = 0;\nconst maxScore = 100;\n\n// Word count (target: 1000-2500)\nconst wordCount = draft.content.split(/\\s+/).length;\nif (wordCount >= 1000 && wordCount <= 2500) {\n  checks.push({ name: 'Word Count', status: 'pass', value: wordCount, target: '1000-2500' });\n  score += 15;\n} else {\n  checks.push({ name: 'Word Count', status: 'fail', value: wordCount, target: '1000-2500' });\n}\n\n// Title length (target: 50-60 chars)\nconst titleLength = draft.title.length;\nif (titleLength >= 50 && titleLength <= 60) {\n  checks.push({ name: 'Title Length', status: 'pass', value: titleLength, target: '50-60' });\n  score += 10;\n} else if (titleLength >= 40 && titleLength <= 70) {\n  checks.push({ name: 'Title Length', status: 'warning', value: titleLength, target: '50-60' });\n  score += 5;\n} else {\n  checks.push({ name: 'Title Length', status: 'fail', value: titleLength, target: '50-60' });\n}\n\n// Meta description (target: 150-160 chars)\nconst metaLength = draft.metaDescription?.length || 0;\nif (metaLength >= 150 && metaLength <= 160) {\n  checks.push({ name: 'Meta Description', status: 'pass', value: metaLength, target: '150-160' });\n  score += 10;\n} else if (metaLength >= 120 && metaLength <= 180) {\n  checks.push({ name: 'Meta Description', status: 'warning', value: metaLength, target: '150-160' });\n  score += 5;\n} else {\n  checks.push({ name: 'Meta Description', status: 'fail', value: metaLength, target: '150-160' });\n}\n\n// H2 headings (target: 3-7)\nconst h2Count = (draft.content.match(/^## /gm) || []).length;\nif (h2Count >= 3 && h2Count <= 7) {\n  checks.push({ name: 'H2 Headings', status: 'pass', value: h2Count, target: '3-7' });\n  score += 10;\n} else {\n  checks.push({ name: 'H2 Headings', status: 'fail', value: h2Count, target: '3-7' });\n}\n\n// FAQ section present\nconst hasFAQ = draft.content.toLowerCase().includes('faq') || draft.content.includes('Q:');\nif (hasFAQ) {\n  checks.push({ name: 'FAQ Section', status: 'pass', value: 'Present' });\n  score += 15;\n} else {\n  checks.push({ name: 'FAQ Section', status: 'fail', value: 'Missing' });\n}\n\n// Schema present\nif (draft.schemas?.faq && draft.schemas?.article) {\n  checks.push({ name: 'Schema Markup', status: 'pass', value: 'FAQPage + Article' });\n  score += 15;\n} else {\n  checks.push({ name: 'Schema Markup', status: 'fail', value: 'Missing' });\n}\n\n// CTA present\nconst hasCTA = draft.content.toLowerCase().includes('getaround');\nif (hasCTA) {\n  checks.push({ name: 'CTA Present', status: 'pass', value: 'Getaround mentioned' });\n  score += 10;\n} else {\n  checks.push({ name: 'CTA Present', status: 'fail', value: 'Missing' });\n}\n\n// Internal links\nconst linkCount = draft.internalLinks?.length || 0;\nif (linkCount >= 2) {\n  checks.push({ name: 'Internal Links', status: 'pass', value: linkCount, target: '2+' });\n  score += 15;\n} else if (linkCount >= 1) {\n  checks.push({ name: 'Internal Links', status: 'warning', value: linkCount, target: '2+' });\n  score += 7;\n} else {\n  checks.push({ name: 'Internal Links', status: 'fail', value: linkCount, target: '2+' });\n}\n\nconst passedChecks = checks.filter(c => c.status === 'pass').length;\nconst failedChecks = checks.filter(c => c.status === 'fail').length;\nconst overallStatus = failedChecks === 0 ? 'PASS' : failedChecks <= 2 ? 'NEEDS_WORK' : 'FAIL';\n\nreturn {\n  json: {\n    ...draft,\n    qualityReport: {\n      score,\n      maxScore,\n      percentage: Math.round(score / maxScore * 100),\n      status: overallStatus,\n      checks,\n      passedChecks,\n      failedChecks,\n      generatedAt: new Date().toISOString()\n    }\n  }\n};"
  }
}
```

### Node 4.2: Slack - Review Request
```json
{
  "nodeType": "n8n-nodes-base.slack",
  "name": "Request Human Review",
  "parameters": {
    "operation": "postMessage",
    "channel": "#seo-content-review",
    "text": "📝 *Content Review Required*\n\n*Title:* {{ $json.title }}\n*Market:* {{ $json.market | capitalize }}\n*Quality Score:* {{ $json.qualityReport.percentage }}% ({{ $json.qualityReport.status }})\n\n*Checks:*\n{{ $json.qualityReport.checks.map(c => `${c.status === 'pass' ? '✅' : c.status === 'warning' ? '⚠️' : '❌'} ${c.name}: ${c.value}`).join('\\n') }}\n\n📄 <{{ $vars.SHEETS_DRAFTS_URL }}|View Draft>\n\nReact: ✅ Approve | 🔄 Request Changes | ❌ Reject"
  }
}
```

---

## Workflow 5: Monitoring - Node Specifications

### Node 5.1: Schedule Trigger - Weekly Monitor
```json
{
  "nodeType": "n8n-nodes-base.scheduleTrigger",
  "name": "Weekly Monitoring",
  "parameters": {
    "rule": {
      "interval": [
        {
          "field": "weeks",
          "weeksInterval": 1,
          "triggerAtDay": ["friday"],
          "triggerAtHour": 6,
          "triggerAtMinute": 0
        }
      ]
    }
  }
}
```

### Node 5.2: Google Sheets - Get Published URLs
```json
{
  "nodeType": "n8n-nodes-base.googleSheets",
  "name": "Get Published Content",
  "parameters": {
    "operation": "read",
    "documentId": "{{ $vars.SHEETS_PUBLISHED_ID }}",
    "sheetName": "Published_Articles",
    "options": {
      "valueRenderMode": "UNFORMATTED_VALUE"
    }
  }
}
```

### Node 5.3: Code - Generate Performance Report
```json
{
  "nodeType": "n8n-nodes-base.code",
  "name": "Generate Performance Report",
  "parameters": {
    "mode": "runOnceForAllItems",
    "jsCode": "const currentData = $input.all()[0].json; // GSC data\nconst previousData = $input.all()[1].json; // Previous week\nconst publishedArticles = $input.all()[2].json; // Published list\n\n// Calculate week-over-week changes\nfunction calculateChanges(current, previous) {\n  return {\n    clicksChange: current.clicks - (previous?.clicks || 0),\n    clicksChangePercent: previous?.clicks ? Math.round((current.clicks - previous.clicks) / previous.clicks * 100) : null,\n    impressionsChange: current.impressions - (previous?.impressions || 0),\n    positionChange: previous?.position ? Math.round((previous.position - current.position) * 10) / 10 : null,\n    ctrChange: previous?.ctr ? Math.round((current.ctr - previous.ctr) * 10000) / 100 : null\n  };\n}\n\n// Find top performers and alerts\nconst articles = publishedArticles.map(article => {\n  const current = currentData.find(d => d.page === article.url);\n  const previous = previousData.find(d => d.page === article.url);\n  const changes = calculateChanges(current || {}, previous);\n  \n  let alerts = [];\n  if (changes.clicksChangePercent < -30) alerts.push('Traffic drop >30%');\n  if (changes.positionChange < -10) alerts.push('Position dropped >10');\n  if (changes.clicksChangePercent > 50) alerts.push('Traffic spike!');\n  \n  return {\n    ...article,\n    current: current || { clicks: 0, impressions: 0, ctr: 0, position: 0 },\n    changes,\n    alerts,\n    publishedDaysAgo: Math.floor((new Date() - new Date(article.publishDate)) / 86400000)\n  };\n});\n\n// Summary stats\nconst franceArticles = articles.filter(a => a.market === 'france');\nconst norwayArticles = articles.filter(a => a.market === 'norway');\n\nconst report = {\n  period: {\n    start: $now.minus(7, 'days').toFormat('yyyy-MM-dd'),\n    end: $now.minus(1, 'days').toFormat('yyyy-MM-dd')\n  },\n  france: {\n    totalClicks: franceArticles.reduce((sum, a) => sum + a.current.clicks, 0),\n    avgPosition: franceArticles.length ? Math.round(franceArticles.reduce((sum, a) => sum + a.current.position, 0) / franceArticles.length * 10) / 10 : 0,\n    articlesWithAlerts: franceArticles.filter(a => a.alerts.length > 0),\n    topPerformer: franceArticles.sort((a, b) => b.changes.clicksChange - a.changes.clicksChange)[0]\n  },\n  norway: {\n    totalClicks: norwayArticles.reduce((sum, a) => sum + a.current.clicks, 0),\n    avgPosition: norwayArticles.length ? Math.round(norwayArticles.reduce((sum, a) => sum + a.current.position, 0) / norwayArticles.length * 10) / 10 : 0,\n    articlesWithAlerts: norwayArticles.filter(a => a.alerts.length > 0),\n    topPerformer: norwayArticles.sort((a, b) => b.changes.clicksChange - a.changes.clicksChange)[0]\n  },\n  allArticles: articles,\n  generatedAt: new Date().toISOString()\n};\n\nreturn [{ json: report }];"
  }
}
```

### Node 5.4: Slack - Weekly Report
```json
{
  "nodeType": "n8n-nodes-base.slack",
  "name": "Send Weekly Performance",
  "parameters": {
    "operation": "postMessage",
    "channel": "#seo-automation",
    "text": "📊 *Weekly SEO Performance Report*\n_{{ $json.period.start }} to {{ $json.period.end }}_\n\n*🇫🇷 France Blog*\n• Total Clicks: {{ $json.france.totalClicks }}\n• Avg Position: {{ $json.france.avgPosition }}\n• Top Performer: {{ $json.france.topPerformer?.title || 'N/A' }}\n• Alerts: {{ $json.france.articlesWithAlerts.length }} articles need attention\n\n*🇳🇴 Norway Blog*\n• Total Clicks: {{ $json.norway.totalClicks }}\n• Avg Position: {{ $json.norway.avgPosition }}\n• Top Performer: {{ $json.norway.topPerformer?.title || 'N/A' }}\n• Alerts: {{ $json.norway.articlesWithAlerts.length }} articles need attention\n\n📋 <{{ $vars.SHEETS_MONITORING_URL }}|View Full Report>"
  }
}
```

---

## Shared Configuration Variables

### n8n Variables Required
```json
{
  "SHEETS_RESEARCH_ID": "1abc123...",
  "SHEETS_RESEARCH_URL": "https://docs.google.com/spreadsheets/d/1abc123...",
  "SHEETS_CONTENT_QUEUE_ID": "1def456...",
  "SHEETS_DRAFTS_ID": "1ghi789...",
  "SHEETS_DRAFTS_URL": "https://docs.google.com/spreadsheets/d/1ghi789...",
  "SHEETS_PUBLISHED_ID": "1jkl012...",
  "SHEETS_MONITORING_URL": "https://docs.google.com/spreadsheets/d/1jkl012...",
  "SLACK_CHANNEL_REPORTS": "#seo-automation",
  "SLACK_CHANNEL_APPROVAL": "#seo-content-approval",
  "SLACK_CHANNEL_REVIEW": "#seo-content-review"
}
```

### Credentials Required
| Credential | Type | Used In |
|------------|------|---------|
| `GSC-Getaround` | Google OAuth 2.0 | Research, Monitoring |
| `Google-Sheets` | Google OAuth 2.0 | All workflows |
| `Slack-Getaround` | Slack Bot Token | All workflows |
| `Anthropic-API` | API Key | Planning, Writing |

---

*Specifications Version: 1.0*
*Last Updated: 2026-01-07*
*Ready for: Phase 5 Implementation*
