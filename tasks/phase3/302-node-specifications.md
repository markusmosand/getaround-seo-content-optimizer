# Task 302: Node Specifications

## Status: [x] Completed ✅ 2026-01-07

## Objective
Create detailed node configurations for all 5 workflows.

## Output
`architecture/NODE_SPECIFICATIONS.md`

## Summary

### Node Types Used (15)

| Category | Nodes |
|----------|-------|
| **Triggers** | Schedule, Manual, Google Sheets Trigger |
| **Data** | HTTP Request, Google Sheets |
| **Logic** | IF, Switch, Code, Set, Merge |
| **AI** | AI Agent, Anthropic Chat, OpenAI Chat, Output Parser |
| **Notifications** | Slack |

### Key Configurations

**GSC Integration:**
- Direct API calls via HTTP Request node
- OAuth 2.0 authentication
- Filter by `/blog/` (France) or `/blogg/` (Norway)

**AI Models:**
- Claude Opus for writing (quality)
- Claude Sonnet for planning (speed + quality)
- GPT-4 as fallback

**Schema Generation:**
- Custom Code node
- Auto-extracts FAQ from content
- Generates FAQPage + Article schema

### Credentials Required

| Credential | Type |
|------------|------|
| GSC-Getaround | Google OAuth 2.0 |
| Google-Sheets | Google OAuth 2.0 |
| Slack-Getaround | Bot Token |
| Anthropic-API | API Key |

### Shared Variables

- Sheet IDs for Research, Content Queue, Drafts, Published
- Slack channel names
- All configurable via n8n Variables
