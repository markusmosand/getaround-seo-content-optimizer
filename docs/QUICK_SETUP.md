# Quick Setup Guide

Get the Notion + Slack + AI workflow running in under 30 minutes.

---

## Step 1: Notion Database (10 minutes)

### Create Database

1. Open Notion → Create new page → Select "Database - Full page"
2. Name it: `SEO Skill Tasks`

### Add Properties

Click "+ Add a property" for each:

| Property Name | Type | Configuration |
|---------------|------|---------------|
| Status | Select | Add options: `Backlog`, `Ready`, `In Progress`, `In Review`, `Done`, `Blocked` |
| Type | Select | Add options: `🤖 AI-solo`, `🤝 Collaboration`, `👤 Human-only` |
| Priority | Select | Add options: `P0 Critical`, `P1 High`, `P2 Medium`, `P3 Low` |
| Effort | Select | Add options: `S (<1h)`, `M (1-4h)`, `L (4-8h)`, `XL (>8h)` |
| Project | Select | Add options: `Phase 1: Reliability`, `Phase 2: Spain`, `Phase 3: QA`, `Phase 4: Rollout` |
| Due Date | Date | - |
| Blocked By | Relation | Link to same database |
| AI Notes | Text | - |
| Last AI Review | Date | - |
| Slack Thread | URL | - |

### Create Views

1. Click "+ Add a view" → Board → Name: "🎯 Daily Focus"
   - Group by: Status
   - Filter: Status is not Done, is not Backlog

2. Click "+ Add a view" → Table → Name: "🤖 AI Queue"
   - Filter: Type is "🤖 AI-solo" AND Status is "Ready"

### Get Integration Token

1. Go to https://www.notion.so/my-integrations
2. Click "+ New integration"
3. Name: "Claude Code"
4. Select workspace
5. Copy the "Internal Integration Secret"
6. Go back to your database → "..." menu → "Connections" → Add "Claude Code"

---

## Step 2: Slack Setup (5 minutes)

### Create Channel

1. Create new channel: `#seo-skill-tasks`
2. Add description: "Task management for SEO skill. Daily AI standups at 08:00."

### Create Slack App (for automation)

1. Go to https://api.slack.com/apps
2. Click "Create New App" → "From scratch"
3. Name: "SEO Task Bot", select workspace
4. Go to "OAuth & Permissions"
5. Add Bot Token Scopes:
   - `chat:write`
   - `channels:read`
   - `channels:history`
6. Click "Install to Workspace"
7. Copy "Bot User OAuth Token" (starts with `xoxb-`)
8. Invite bot to channel: `/invite @SEO Task Bot`

---

## Step 3: Claude Code Configuration (5 minutes)

### Configure MCP Servers

Add to your Claude Code MCP configuration (`~/.claude/mcp.json` or project settings):

```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@notionhq/notion-mcp-server"],
      "env": {
        "NOTION_API_KEY": "secret_xxxxxxxxxxxxxxxxxxxxx",
        "NOTION_DATABASE_ID": "your-database-id-here"
      }
    },
    "slack": {
      "command": "npx",
      "args": ["-y", "@anthropic/slack-mcp-server"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-xxxxxxxxxxxxxxxxxxxxx",
        "SLACK_CHANNEL_ID": "C0123456789"
      }
    }
  }
}
```

### Find Your IDs

**Notion Database ID:**
- Open your database in browser
- URL looks like: `notion.so/xxxxx/DATABASE_ID?v=xxxxx`
- Copy the DATABASE_ID part (32 characters)

**Slack Channel ID:**
- Right-click channel → "View channel details"
- Scroll to bottom, copy Channel ID

---

## Step 4: Import Initial Tasks (5 minutes)

Run this in Claude Code:

```
/notion-create

Create these tasks:

Phase 1: Reliability
1. Implement hybrid approach in SKILL.md - P0, Collaboration, M
2. Add inline quick reference section - P1, AI-solo, S
3. Verify reference file links - P1, AI-solo, S
4. Create MAINTENANCE.md - P1, AI-solo, S
5. Create CHANGELOG.md - P2, AI-solo, S

Phase 2: Spain Support
6. Export GSC data for Spain - P1, Human-only, S
7. Get Spanish marketing guidelines - P1, Human-only, S
8. Create market_context_es.md - P1, Collaboration, M, blocked by #6 and #7
9. Create tone_guide_es.md - P1, Collaboration, M, blocked by #7
10. Create performance_data_es.md - P1, Collaboration, M, blocked by #6
11. Create owner_content_guide_es.md - P2, AI-solo, S, blocked by #8
12. Update SKILL.md for Spain detection - P1, AI-solo, S, blocked by #8-11

Phase 3: Quality Assurance
13. Create example_listicle_no.md - P2, Collaboration, M
14. Create example_b2b_fr.md - P2, Collaboration, M
15. Create VALIDATION.md checklist - P2, AI-solo, M
```

---

## Step 5: Test the Workflow (5 minutes)

### Test Daily Standup

```
/notion-standup
```

You should see:
- List of tasks fetched from Notion
- Categorized by type and status
- AI recommendations

### Test Task Update

```
/notion-update
Task: Create CHANGELOG.md
Status: Done
Notes: Created initial changelog with v1.0 features
```

### Test Slack Posting

If Slack MCP is configured, check #seo-skill-tasks for messages.

---

## Daily Usage

### Morning (2 minutes)
```
/notion-standup
```
Review the plan, reply ✅ to approve AI tasks.

### During Work
- AI executes approved tasks
- Use `/notion-create` for new tasks
- Use `/notion-update` when completing work

### Slack
- Get notifications for completed tasks
- Discuss blockers in threads
- Tag @SEO Task Bot for questions

---

## Troubleshooting

| Problem | Solution |
|---------|----------|
| "Notion MCP not found" | Check MCP config, run `npx @notionhq/notion-mcp-server` to test |
| "Database not found" | Verify database ID, ensure integration has access |
| "Slack post failed" | Check bot token, verify bot is in channel |
| "Permission denied" | Re-share database with integration |

---

## Next Steps

Once basic setup works:

1. **Add automation** - Set up scheduled standups
2. **Customize views** - Create Notion views for your workflow
3. **Add integrations** - Connect to GitHub, Calendar, etc.
4. **Build observability** - Track AI task completion rates

See `NOTION_SLACK_AI_WORKFLOW.md` for advanced configuration.
