# Workflow Architecture: Getaround SEO Automation

## Architecture Status

| Status | Details |
|--------|---------|
| **Design Date** | 2026-01-07 |
| **Version** | 1.0 |
| **Status** | Ready for Implementation |
| **Platform** | n8n Cloud |

---

## Executive Summary

A 5-workflow system to automate SEO content creation for Getaround's France and Norway blogs, reducing content creation time from 5-6 hours to ~1.5 hours while improving SEO performance.

### System Overview

```
┌─────────────────────────────────────────────────────────────────────┐
│                    GETAROUND SEO AUTOMATION SYSTEM                  │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐    ┌──────────┐      │
│  │ WORKFLOW │    │ WORKFLOW │    │ WORKFLOW │    │ WORKFLOW │      │
│  │    1     │───▶│    2     │───▶│    3     │───▶│    4     │      │
│  │ RESEARCH │    │ PLANNING │    │ WRITING  │    │  REVIEW  │      │
│  └──────────┘    └──────────┘    └──────────┘    └──────────┘      │
│       │                                               │             │
│       │              ┌──────────┐                     │             │
│       └─────────────▶│ WORKFLOW │◀────────────────────┘             │
│                      │    5     │                                   │
│                      │MONITORING│                                   │
│                      └──────────┘                                   │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Workflow 1: Research

### Purpose
Automated weekly data collection from GSC to identify content opportunities, track performance, and surface optimization candidates.

### Trigger
- **Primary:** Schedule Trigger (Weekly - Monday 6:00 AM)
- **Secondary:** Manual trigger for ad-hoc research

### Data Flow

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Schedule  │────▶│  GSC Data   │────▶│   Process   │────▶│   Output    │
│   Trigger   │     │  Extraction │     │   & Rank    │     │   Report    │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
                          │                    │                    │
                          ▼                    ▼                    ▼
                    ┌───────────┐        ┌───────────┐        ┌───────────┐
                    │ France    │        │ CTR Gaps  │        │ Google    │
                    │ Norway    │        │ Position  │        │ Sheets    │
                    │ Data      │        │ Opps      │        │ Slack     │
                    └───────────┘        └───────────┘        └───────────┘
```

### Inputs
| Input | Source | Format |
|-------|--------|--------|
| France GSC data | `sc-domain:fr.getaround.com` | API response |
| Norway GSC data | `sc-domain:no.getaround.com` | API response |
| Historical data | Google Sheets | Previous weeks |

### Outputs
| Output | Destination | Format |
|--------|-------------|--------|
| Weekly report | Google Sheets | Structured data |
| Opportunity alerts | Slack | Message |
| Topic suggestions | Workflow 2 input | JSON |

### Key Metrics Extracted
- Top pages by impressions (week-over-week change)
- CTR gap opportunities (>1000 impressions, <1% CTR)
- Position opportunities (position 11-20, high impressions)
- New ranking queries
- Declining pages (>20% drop)

### Market-Specific Logic
| Market | Filter | Focus Areas |
|--------|--------|-------------|
| France | `/blog/` | B2B queries, ZFE terms, van content |
| Norway | `/blogg/` | Activity queries, road trip terms, seasonal |

---

## Workflow 2: Planning

### Purpose
Generate content topics, angles, and outlines based on research data, applying market-specific content strategies.

### Trigger
- **Primary:** Workflow 1 completion webhook
- **Secondary:** Manual trigger with topic input

### Data Flow

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  Research   │────▶│   Market    │────▶│  AI Topic   │────▶│   Human     │
│   Data      │     │  Detection  │     │ Generation  │     │  Approval   │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
                          │                    │                    │
                          ▼                    ▼                    ▼
                    ┌───────────┐        ┌───────────┐        ┌───────────┐
                    │ France    │        │ Claude    │        │ Slack     │
                    │ Norway    │        │ Prompts   │        │ Approval  │
                    │ Strategy  │        │           │        │           │
                    └───────────┘        └───────────┘        └───────────┘
```

### Inputs
| Input | Source | Format |
|-------|--------|--------|
| Opportunity data | Workflow 1 | JSON |
| Market context | Config | Market-specific prompts |
| Content calendar | Google Sheets | Existing planned content |

### Outputs
| Output | Destination | Format |
|--------|-------------|--------|
| Topic proposals | Slack | Formatted message |
| Approved topics | Google Sheets | Content queue |
| Content briefs | Workflow 3 input | JSON |

### AI Generation Logic

**France Topics (B2B Focus):**
```
Prompt Framework:
- Regulatory angle (ZFE, TVS, professional displacement)
- Year-stamp inclusion
- Professional audience tone
- Calculator/guide format preference
```

**Norway Topics (B2C Focus):**
```
Prompt Framework:
- Activity/experience angle
- Specific location + duration
- Family/outdoor focus
- Listicle format preference
```

### Approval Flow
1. AI generates 3-5 topic proposals per market
2. Slack notification with topic details
3. Human selects/modifies topics
4. Approved topics added to content queue

---

## Workflow 3: Writing

### Purpose
Generate SEO-optimized article drafts based on approved content briefs, with market-specific tone and structure.

### Trigger
- **Primary:** Approved topic in queue (Google Sheets trigger)
- **Secondary:** Manual trigger with brief

### Data Flow

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  Content    │────▶│   Market    │────▶│  AI Draft   │────▶│   Output    │
│   Brief     │     │  Prompts    │     │ Generation  │     │  Formatting │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
                          │                    │                    │
                          ▼                    ▼                    ▼
                    ┌───────────┐        ┌───────────┐        ┌───────────┐
                    │ FR: Formal│        │ Claude    │        │ Markdown  │
                    │ NO: Casual│        │ Opus/     │        │ + Schema  │
                    │           │        │ Sonnet    │        │           │
                    └───────────┘        └───────────┘        └───────────┘
```

### Inputs
| Input | Source | Format |
|-------|--------|--------|
| Content brief | Workflow 2 / Google Sheets | JSON |
| Market prompts | Config | System prompts |
| Style guide | Config | Tone/format rules |

### Outputs
| Output | Destination | Format |
|--------|-------------|--------|
| Draft article | Google Docs | Markdown |
| Meta description | Draft metadata | Text |
| Schema markup | Draft metadata | JSON-LD |
| Internal link suggestions | Draft metadata | URLs |

### Content Structure Templates

**France Article Structure:**
```markdown
# [Title with Year]

[2-3 sentence answer to main question - AEO optimized]

## [Section 1: Problem/Context]
[Professional context, regulations]

## [Section 2: Solution/Guide]
[Detailed explanation with calculations if relevant]

## [Section 3: Practical Steps]
[Numbered steps or checklist]

## FAQ
[3-5 common questions with direct answers]

## Conclusion
[Summary + CTA to Getaround]
```

**Norway Article Structure:**
```markdown
# [Title - Activity/Location focused]

[Hook sentence + what reader will discover]

## Highlights
- [Bullet 1]
- [Bullet 2]
- [Bullet 3]

## [Main Content - Listicle or Itinerary]
### 1. [Item/Day 1]
[Description + why car needed]

### 2. [Item/Day 2]
[Description + practical tips]

[Continue pattern...]

## Praktiske tips
[Local knowledge, parking, driving tips]

## FAQ
[3-5 questions]

## Lei en bil og oppdag [location]
[CTA to Getaround]
```

### Schema Generation
| Schema Type | When to Use | Auto-Generated |
|-------------|-------------|----------------|
| FAQPage | All articles with FAQ section | Yes |
| HowTo | Step-by-step guides, itineraries | Yes |
| Article | All articles | Yes |
| BreadcrumbList | All articles | Yes |

---

## Workflow 4: Review

### Purpose
Quality assurance checks on generated content before human final approval.

### Trigger
- **Primary:** Workflow 3 completion
- **Secondary:** Manual trigger for existing content

### Data Flow

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│   Draft     │────▶│  Automated  │────▶│   Score     │────▶│   Human     │
│  Article    │     │   Checks    │     │  & Report   │     │   Review    │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
                          │                    │                    │
                          ▼                    ▼                    ▼
                    ┌───────────┐        ┌───────────┐        ┌───────────┐
                    │ SEO Check │        │ Pass/Fail │        │ Slack     │
                    │ E-E-A-T   │        │ Details   │        │ Approval  │
                    │ Schema    │        │           │        │           │
                    └───────────┘        └───────────┘        └───────────┘
```

### Automated Checks
| Check | Criteria | Pass Threshold |
|-------|----------|----------------|
| **Word count** | 1000-2500 words | Required |
| **Title length** | 50-60 characters | Required |
| **Meta description** | 150-160 characters | Required |
| **H2 headings** | 3-7 per article | Required |
| **FAQ section** | Present with 3-5 questions | Required |
| **Schema markup** | Valid JSON-LD | Required |
| **Internal links** | 2-5 suggestions | Recommended |
| **CTA present** | Getaround mention | Required |
| **Business fit** | Rental intent validation | Required |

### E-E-A-T Checklist
| Signal | Check | Auto-Detectable |
|--------|-------|-----------------|
| Experience | First-hand language present | Partial |
| Expertise | Specific details, accuracy | No |
| Authority | Citations, data references | Yes |
| Trust | Accurate info, updated date | Partial |

### Review Report Format
```
CONTENT REVIEW: [Title]
Market: [France/Norway]
Status: [PASS/NEEDS WORK]

✅ Passed Checks:
- Word count: 1,450 words
- Schema: Valid FAQPage + Article
- CTA: Present

⚠️ Needs Attention:
- Meta description: 172 chars (reduce by 12)
- Internal links: Only 1 found (add 2-3)

📊 Quality Score: 85/100

[APPROVE] [REQUEST CHANGES] [REJECT]
```

---

## Workflow 5: Monitoring

### Purpose
Track published content performance, identify optimization opportunities, and generate weekly reports.

### Trigger
- **Primary:** Schedule Trigger (Weekly - Friday 6:00 AM)
- **Secondary:** Manual trigger for specific URL

### Data Flow

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  Schedule   │────▶│  GSC Data   │────▶│  Compare    │────▶│   Report    │
│  Trigger    │     │  Published  │     │  to Prior   │     │  Generate   │
└─────────────┘     └─────────────┘     └─────────────┘     └─────────────┘
                          │                    │                    │
                          ▼                    ▼                    ▼
                    ┌───────────┐        ┌───────────┐        ┌───────────┐
                    │ New       │        │ WoW       │        │ Slack     │
                    │ Content   │        │ Changes   │        │ Google    │
                    │ URLs      │        │           │        │ Sheets    │
                    └───────────┘        └───────────┘        └───────────┘
```

### Tracking Scope
| Content Type | Tracking Period | Metrics |
|--------------|-----------------|---------|
| New articles (0-30 days) | Weekly | Indexing, first impressions |
| Recent articles (30-90 days) | Weekly | Position, CTR trends |
| Established articles (90+ days) | Monthly | Performance changes |

### Key Metrics Tracked
- **Indexing status** - Via URL inspection API
- **First impressions** - When content starts appearing
- **Position trajectory** - Week-over-week movement
- **CTR changes** - Impact of title/meta updates
- **Click growth** - Absolute performance

### Alert Triggers
| Alert | Condition | Action |
|-------|-----------|--------|
| Not indexed | 7+ days after publish | Check technical issues |
| Position drop | >10 positions WoW | Review content |
| CTR spike | >50% improvement | Document what worked |
| Traffic loss | >30% WoW decline | Investigate cause |

### Weekly Report Format
```
📊 WEEKLY SEO PERFORMANCE REPORT
Period: [Date Range]

FRANCE BLOG
- New articles indexed: 2/2
- Avg position change: +3.2
- Total clicks: 1,050 (+8% WoW)
- Top performer: [Article] +45 clicks

NORWAY BLOG
- New articles indexed: 1/1
- Avg position change: +1.8
- Total clicks: 82 (+12% WoW)
- Top performer: [Article] +15 clicks

🎯 QUICK WINS IDENTIFIED
1. [Article] - Position 11, needs push to page 1
2. [Article] - High impressions, low CTR - title test

📋 ACTION ITEMS
- [ ] Update meta for [Article]
- [ ] Add internal links to [Article]
```

---

## Inter-Workflow Communication

### Data Handoff Pattern

```
Workflow 1 ──[opportunities.json]──▶ Workflow 2
Workflow 2 ──[approved_topics.json]──▶ Workflow 3
Workflow 3 ──[draft_article.json]──▶ Workflow 4
Workflow 4 ──[published_url]──▶ Workflow 5
Workflow 5 ──[performance_data]──▶ Workflow 1
```

### Shared Data Store
| Data | Location | Purpose |
|------|----------|---------|
| Content queue | Google Sheets | Topic tracking |
| Published URLs | Google Sheets | Performance tracking |
| Historical metrics | Google Sheets | Trend analysis |
| Config/prompts | n8n Variables | System settings |

### Webhook Connections
| From | To | Trigger |
|------|----|----|
| Workflow 1 | Workflow 2 | Research complete |
| Workflow 2 | Workflow 3 | Topic approved |
| Workflow 3 | Workflow 4 | Draft complete |
| Workflow 4 | Workflow 5 | Content published |

---

## Error Handling

### Retry Strategy
| Error Type | Retry Count | Delay | Escalation |
|------------|-------------|-------|------------|
| API timeout | 3 | 30s exponential | Slack alert |
| Rate limit | 5 | 60s | Queue for later |
| Auth failure | 0 | - | Immediate alert |
| AI generation fail | 2 | 10s | Use fallback model |

### Fallback Models
| Primary | Fallback | Use Case |
|---------|----------|----------|
| Claude Opus | Claude Sonnet | Writing |
| Claude Sonnet | GPT-4 | Planning |
| GPT-4 | Claude Haiku | Quick tasks |

### Alert Channels
| Severity | Channel | Response Time |
|----------|---------|---------------|
| Critical | Slack + Email | Immediate |
| Warning | Slack | Same day |
| Info | Google Sheets log | Weekly review |

---

## Security & Access

### Credentials Required
| Service | Credential Type | Scope |
|---------|-----------------|-------|
| Google Sheets | OAuth 2.0 | Read/Write |
| GSC (via MCP) | OAuth 2.0 | Read only |
| Slack | Bot token | Post messages |
| Anthropic | API key | Claude models |
| OpenAI | API key | GPT models (fallback) |

### Data Handling
- No PII in content generation
- GSC data aggregated (no user-level data)
- Logs retained for 30 days
- API keys stored in n8n credentials

---

## Implementation Priority

| Phase | Workflow | Priority | Dependencies |
|-------|----------|----------|--------------|
| 1 | Research (WF1) | Critical | GSC MCP |
| 2 | Monitoring (WF5) | Critical | WF1 |
| 3 | Planning (WF2) | High | WF1, AI nodes |
| 4 | Writing (WF3) | High | WF2 |
| 5 | Review (WF4) | Medium | WF3 |

### MVP Scope
1. **Week 1:** Research + Monitoring workflows
2. **Week 2:** Planning workflow with approval
3. **Week 3:** Writing workflow with templates
4. **Week 4:** Review workflow + full integration

---

*Architecture Version: 1.0*
*Last Updated: 2026-01-07*
*Ready for: Phase 5 Implementation*
