# Automation Matrix: Manual vs Automated Steps

## Matrix Status

| Status | Details |
|--------|---------|
| **Design Date** | 2026-01-07 |
| **Version** | 1.0 |
| **Time Savings** | 5-6 hours → ~1.5 hours |

---

## Executive Summary

### Time Allocation

| Activity | Current (Manual) | Target (Automated) | Savings |
|----------|------------------|-------------------|---------|
| Research | 1-2 hours | 15 min | 75-88% |
| Planning | 1 hour | 15 min | 75% |
| Writing | 2-3 hours | 45 min | 63-75% |
| Review | 1 hour | 30 min | 50% |
| Publishing | 30 min | 15 min | 50% |
| **TOTAL** | **5.5-7.5 hours** | **~2 hours** | **70%+** |

### Automation Levels

| Level | Definition | Human Involvement |
|-------|------------|-------------------|
| **Full** | No human input needed | 0% |
| **High** | Human reviews output | 10-20% |
| **Medium** | Human edits/modifies | 30-50% |
| **Low** | Human does most work, AI assists | 60-80% |
| **Manual** | Fully human | 100% |

---

## Workflow 1: Research

### Step Breakdown

| Step | Current Process | Automated Process | Level | Human Touch |
|------|-----------------|-------------------|-------|-------------|
| **1.1** Open GSC | Manual login | Schedule trigger | Full | None |
| **1.2** Select property | Manual selection | Config-based | Full | None |
| **1.3** Set date range | Manual input | Auto (last 7 days) | Full | None |
| **1.4** Extract France data | Manual export | API call | Full | None |
| **1.5** Extract Norway data | Manual export | API call | Full | None |
| **1.6** Identify CTR gaps | Manual analysis | Algorithm | Full | None |
| **1.7** Identify position opps | Manual analysis | Algorithm | Full | None |
| **1.8** Compare to last week | Manual comparison | Auto calculation | Full | None |
| **1.9** Generate report | Manual writing | Template fill | Full | None |
| **1.10** Send to team | Manual email | Slack auto-post | Full | None |
| **1.11** Review findings | - | Human review | Manual | **Review report** |

### Automation Summary - Research
| Metric | Value |
|--------|-------|
| Total steps | 11 |
| Fully automated | 10 |
| Human required | 1 |
| Automation level | **91%** |
| Time: Before | 1-2 hours |
| Time: After | 15 min (review only) |

---

## Workflow 2: Planning

### Step Breakdown

| Step | Current Process | Automated Process | Level | Human Touch |
|------|-----------------|-------------------|-------|-------------|
| **2.1** Review opportunities | Manual reading | Auto-prioritized list | High | Quick scan |
| **2.2** Check content calendar | Manual lookup | Auto-check for duplicates | Full | None |
| **2.3** Identify market | Manual decision | Auto-detection | Full | None |
| **2.4** Load market strategy | Mental recall | Config-loaded prompts | Full | None |
| **2.5** Brainstorm topics | Manual ideation | AI generation | High | Review suggestions |
| **2.6** Evaluate business fit | Manual assessment | AI scoring | Medium | **Validate fit** |
| **2.7** Select angle | Manual decision | AI suggestions | Medium | **Choose angle** |
| **2.8** Create brief | Manual writing | AI generation | High | Review brief |
| **2.9** Add to queue | Manual entry | Auto-add on approval | Full | None |
| **2.10** Approve topic | - | - | Manual | **Approve/reject** |

### Automation Summary - Planning
| Metric | Value |
|--------|-------|
| Total steps | 10 |
| Fully automated | 4 |
| High automation | 3 |
| Medium automation | 2 |
| Manual required | 1 |
| Automation level | **70%** |
| Time: Before | 1 hour |
| Time: After | 15 min |

---

## Workflow 3: Writing

### Step Breakdown

| Step | Current Process | Automated Process | Level | Human Touch |
|------|-----------------|-------------------|-------|-------------|
| **3.1** Load content brief | Manual reading | Auto-loaded | Full | None |
| **3.2** Research topic | Web research | AI knowledge + brief | High | None |
| **3.3** Create outline | Manual structure | AI template-based | High | Review outline |
| **3.4** Write introduction | Manual writing | AI generation | High | Review |
| **3.5** Write main sections | Manual writing | AI generation | Medium | **Edit content** |
| **3.6** Write FAQ | Manual writing | AI generation | High | Review |
| **3.7** Write meta title | Manual writing | AI generation | High | Review |
| **3.8** Write meta description | Manual writing | AI generation | High | Review |
| **3.9** Generate schema | Manual coding | Auto-generation | Full | None |
| **3.10** Suggest internal links | Manual search | Auto-suggestion | High | **Select links** |
| **3.11** Format document | Manual formatting | Template-based | Full | None |
| **3.12** Human editing | - | - | Manual | **Edit draft** |

### Automation Summary - Writing
| Metric | Value |
|--------|-------|
| Total steps | 12 |
| Fully automated | 3 |
| High automation | 7 |
| Medium automation | 1 |
| Manual required | 1 |
| Automation level | **75%** |
| Time: Before | 2-3 hours |
| Time: After | 45 min |

---

## Workflow 4: Review

### Step Breakdown

| Step | Current Process | Automated Process | Level | Human Touch |
|------|-----------------|-------------------|-------|-------------|
| **4.1** Check word count | Manual count | Auto-check | Full | None |
| **4.2** Check title length | Manual count | Auto-check | Full | None |
| **4.3** Check meta length | Manual count | Auto-check | Full | None |
| **4.4** Validate schema | Manual testing | Auto-validation | Full | None |
| **4.5** Check heading structure | Manual review | Auto-check | Full | None |
| **4.6** Verify FAQ present | Manual check | Auto-check | Full | None |
| **4.7** Check CTA presence | Manual check | Auto-check | Full | None |
| **4.8** Validate business fit | Manual assessment | AI scoring | Medium | **Verify** |
| **4.9** E-E-A-T review | Manual checklist | Partial auto | Low | **Review signals** |
| **4.10** Generate report | Manual writing | Auto-generation | Full | None |
| **4.11** Final approval | - | - | Manual | **Approve/reject** |

### Automation Summary - Review
| Metric | Value |
|--------|-------|
| Total steps | 11 |
| Fully automated | 8 |
| Medium automation | 1 |
| Low automation | 1 |
| Manual required | 1 |
| Automation level | **73%** |
| Time: Before | 1 hour |
| Time: After | 30 min |

---

## Workflow 5: Monitoring

### Step Breakdown

| Step | Current Process | Automated Process | Level | Human Touch |
|------|-----------------|-------------------|-------|-------------|
| **5.1** List published URLs | Manual tracking | Auto from sheets | Full | None |
| **5.2** Check indexing status | Manual GSC check | API inspection | Full | None |
| **5.3** Get current metrics | Manual GSC export | API extraction | Full | None |
| **5.4** Get historical metrics | Manual lookup | Auto from sheets | Full | None |
| **5.5** Calculate changes | Manual calculation | Auto-calculate | Full | None |
| **5.6** Identify winners | Manual analysis | Algorithm | Full | None |
| **5.7** Identify losers | Manual analysis | Algorithm | Full | None |
| **5.8** Generate alerts | Manual decision | Rule-based | Full | None |
| **5.9** Create report | Manual writing | Auto-generation | Full | None |
| **5.10** Send report | Manual email | Slack auto-post | Full | None |
| **5.11** Review & action | - | - | Manual | **Review report** |

### Automation Summary - Monitoring
| Metric | Value |
|--------|-------|
| Total steps | 11 |
| Fully automated | 10 |
| Manual required | 1 |
| Automation level | **91%** |
| Time: Before | 30 min |
| Time: After | 10 min (review only) |

---

## Human Touchpoints Summary

### Required Human Actions

| Workflow | Human Action | Frequency | Est. Time |
|----------|--------------|-----------|-----------|
| **Research** | Review weekly report | Weekly | 10 min |
| **Planning** | Approve topics | Per topic | 5 min each |
| **Planning** | Validate business fit | Per topic | 3 min each |
| **Writing** | Edit AI draft | Per article | 30 min |
| **Writing** | Select internal links | Per article | 5 min |
| **Review** | E-E-A-T verification | Per article | 10 min |
| **Review** | Final approval | Per article | 5 min |
| **Monitoring** | Review weekly report | Weekly | 10 min |

### Per-Article Human Time

| Phase | Human Time |
|-------|------------|
| Planning (1 topic) | 8 min |
| Writing (1 article) | 35 min |
| Review (1 article) | 15 min |
| **Total per article** | **~1 hour** |

### Weekly Human Time (4 NO + 6 FR = 10 articles/month)

| Activity | Time |
|----------|------|
| Research review | 10 min |
| Planning (~2.5 topics) | 20 min |
| Writing (~2.5 articles) | 1.5 hours |
| Review (~2.5 articles) | 40 min |
| Monitoring review | 10 min |
| **Weekly total** | **~3 hours** |

---

## Automation Dependencies

### Required for Full Automation

| Dependency | Status | Impact |
|------------|--------|--------|
| GSC MCP connection | ✅ Ready | Research, Monitoring |
| n8n Cloud access | ✅ Ready | All workflows |
| Claude API | ✅ Ready | Planning, Writing |
| Google Sheets API | ✅ Ready | All workflows |
| Slack API | ⏳ Needed | Notifications, Approvals |

### Nice-to-Have Integrations

| Integration | Benefit | Priority |
|-------------|---------|----------|
| Ghost CMS API | Direct publishing | Medium |
| Semrush API | Keyword research | Low |
| GA4 API | Traffic correlation | Low |

---

## Risk Assessment

### Automation Risks

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| AI hallucination | Medium | High | Human review required |
| Outdated info | Medium | High | Source citation, dates |
| Wrong tone | Low | Medium | Market-specific prompts |
| Duplicate content | Low | High | Calendar check |
| Over-optimization | Medium | Medium | Natural language guidelines |

### Quality Gates

| Gate | Location | Action on Fail |
|------|----------|----------------|
| Business fit check | Planning | Reject topic |
| Word count check | Review | Flag for expansion |
| Schema validation | Review | Auto-fix or flag |
| E-E-A-T score | Review | Human review required |
| Final approval | Review | Human decision |

---

## Recommendations

### Phase 1: Automate Data Collection
- Implement Research + Monitoring workflows first
- Highest ROI (91% automation each)
- Low risk (read-only operations)

### Phase 2: Add AI Assistance
- Implement Planning workflow
- Topic generation with human approval
- Test AI output quality

### Phase 3: AI Content Generation
- Implement Writing workflow
- Start with outlines, then full drafts
- Iterate on prompts based on feedback

### Phase 4: Quality Automation
- Implement Review workflow
- Automate checks, keep human approval
- Refine based on patterns

---

*Matrix Version: 1.0*
*Last Updated: 2026-01-07*
