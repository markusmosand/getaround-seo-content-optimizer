# Notion + Slack + AI Task Management System

A high-automation workflow where tasks live in Notion, communication happens in Slack, and AI reviews/executes tasks daily.

---

## System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                     NOTION DATABASE                              │
│                   (Single Source of Truth)                       │
│                                                                  │
│  Tasks with properties:                                          │
│  - Status: Backlog | Ready | In Progress | Review | Done        │
│  - Type: 🤖 AI-solo | 🤝 Collab | 👤 Human-only                 │
│  - Priority: P0 | P1 | P2 | P3                                  │
│  - Effort: S | M | L | XL                                       │
│  - Blocked by: [relation to other tasks]                        │
│  - Due date, Assignee, Project, etc.                            │
└─────────────────────────────────────────────────────────────────┘
                              │
                              │ Notion MCP
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    CLAUDE CODE (AI Agent)                        │
│                                                                  │
│  Daily at 08:00:                                                 │
│  1. Read all tasks from Notion                                   │
│  2. Analyze blockers, priorities, types                          │
│  3. Generate daily plan                                          │
│  4. Post summary to Slack                                        │
│  5. Execute AI-solo tasks (if approved)                          │
│  6. Update Notion with progress                                  │
└─────────────────────────────────────────────────────────────────┘
                              │
                              │ Slack MCP
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                    SLACK CHANNEL                                 │
│                 #seo-skill-tasks                                 │
│                                                                  │
│  - Daily standup posts (AI-generated)                           │
│  - Task updates and progress                                     │
│  - Human-AI conversation threads                                 │
│  - Approval requests                                             │
│  - Completion notifications                                      │
└─────────────────────────────────────────────────────────────────┘
```

---

## Notion Database Setup

### Database Name: `SEO Skill Tasks`

### Properties

| Property | Type | Options/Description |
|----------|------|---------------------|
| **Task** | Title | Task name |
| **Status** | Select | `Backlog`, `Ready`, `In Progress`, `In Review`, `Done`, `Blocked` |
| **Type** | Select | `🤖 AI-solo`, `🤝 Collaboration`, `👤 Human-only` |
| **Priority** | Select | `P0 Critical`, `P1 High`, `P2 Medium`, `P3 Low` |
| **Effort** | Select | `S (<1h)`, `M (1-4h)`, `L (4-8h)`, `XL (>8h)` |
| **Project** | Select | `Phase 1: Reliability`, `Phase 2: Spain`, `Phase 3: QA`, `Phase 4: Rollout` |
| **Assignee** | Person | Who's responsible |
| **Due Date** | Date | When it should be done |
| **Blocked By** | Relation | Links to blocking tasks |
| **AI Notes** | Text | AI's analysis and recommendations |
| **Last AI Review** | Date | When AI last analyzed this task |
| **Slack Thread** | URL | Link to Slack discussion |

### Views

1. **🎯 Daily Focus** (Board view)
   - Filter: Status is not `Done` and not `Backlog`
   - Group by: Status
   - Sort by: Priority

2. **🤖 AI Queue** (Table view)
   - Filter: Type is `🤖 AI-solo` AND Status is `Ready`
   - Sort by: Priority, then Due Date

3. **🚫 Blocked** (Table view)
   - Filter: Status is `Blocked` OR Blocked By is not empty
   - Show: Blocked By relation prominently

4. **📊 All Tasks** (Table view)
   - No filter
   - Group by: Project

---

## Slack Setup

### Channel: `#seo-skill-tasks`

### Channel Description
```
Task management for SEO Content Optimizer skill development.
Daily AI standups at 08:00. Use threads for task discussions.
```

### Slack Workflow Automations

#### 1. Daily Standup Reminder (08:00)
```
Trigger: Schedule (08:00 weekdays)
Action: Post message
Message: "🌅 Good morning! AI standup incoming..."
```

#### 2. Task Completion Notification
```
Trigger: Notion status changes to "Done"
Action: Post to channel
Message: "✅ Task completed: {Task Name}"
```

#### 3. Blocker Alert
```
Trigger: Notion status changes to "Blocked"
Action: Post to channel
Message: "🚫 Task blocked: {Task Name} - Blocked by: {Blocked By}"
```

---

## MCP Configuration

### Required MCP Servers

```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@notionhq/notion-mcp-server"],
      "env": {
        "NOTION_API_KEY": "your-notion-api-key",
        "NOTION_DATABASE_ID": "your-database-id"
      }
    },
    "slack": {
      "command": "npx",
      "args": ["-y", "@anthropic/slack-mcp-server"],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-your-token",
        "SLACK_CHANNEL_ID": "C0123456789"
      }
    }
  }
}
```

### Getting API Keys

#### Notion
1. Go to https://www.notion.so/my-integrations
2. Create new integration
3. Copy "Internal Integration Token"
4. Share your database with the integration

#### Slack
1. Go to https://api.slack.com/apps
2. Create new app → From scratch
3. Add Bot Token Scopes: `chat:write`, `channels:read`, `channels:history`
4. Install to workspace
5. Copy "Bot User OAuth Token"

---

## Daily AI Workflow

### Morning Review (08:00)

The AI performs these steps automatically:

```markdown
## Step 1: Fetch Tasks from Notion
- Query all tasks where Status != Done
- Include Blocked By relations
- Sort by Priority

## Step 2: Analyze Task State
For each task:
- Check if blocked (Blocked By has incomplete tasks)
- Check if ready (all blockers resolved)
- Evaluate if AI can execute (Type = AI-solo AND Status = Ready)

## Step 3: Generate Daily Plan
Categorize tasks into:
- 🔥 Critical (P0, any type)
- 🤖 AI can execute now
- 🤝 Needs collaboration today
- 👤 Human tasks for today
- 🚫 Currently blocked
- 📋 Backlog (not urgent)

## Step 4: Post to Slack
Format and post the daily standup message

## Step 5: Request Approval
Ask: "Should I proceed with AI-solo tasks?"

## Step 6: Execute (if approved)
- Work through AI-solo tasks
- Update Notion status as tasks progress
- Post completion messages to Slack
```

### Slack Message Format

```markdown
# 🌅 Daily Standup - December 16, 2025

## 🔥 Critical (P0)
None currently

## 🤖 AI Can Execute Now
1. **Add inline quick reference to SKILL.md** [P1, M]
   - Ready to implement hybrid approach
   - Will consolidate critical context
2. **Create MAINTENANCE.md** [P1, S]
   - Document quarterly update procedure

## 🤝 Collaboration Needed Today
1. **Create Spain market context** [P1, M]
   - ⏳ Waiting for: Market brief from stakeholder
   - I can draft structure, need data input

## 👤 Human Tasks
1. **Export GSC data for Spain** [P1, S]
   - Requires GSC access
2. **Get Spanish marketing guidelines** [P1, S]
   - Contact stakeholder

## 🚫 Blocked
1. **Create performance_data_es.md** → Blocked by: GSC data export
2. **Create tone_guide_es.md** → Blocked by: Marketing guidelines

## 📊 Summary
- Total open: 12 tasks
- Ready for AI: 2 tasks
- Blocked: 4 tasks

---
**Should I proceed with the AI-solo tasks?**
Reply with ✅ to approve or provide specific instructions.
```

---

## Slash Commands for Claude Code

### `/notion-standup`

```markdown
Perform the daily standup routine:

1. **Connect to Notion** using the Notion MCP
   - Query the SEO Skill Tasks database
   - Get all tasks where Status is not "Done"
   - Include the "Blocked By" relation

2. **Analyze each task:**
   - Is it blocked? (Check if Blocked By tasks are incomplete)
   - Is it ready? (Status = "Ready" and not blocked)
   - Can AI execute? (Type = "🤖 AI-solo" and ready)
   - What's the priority?

3. **Generate the daily plan** in this format:

   ## 🔥 Critical (P0)
   [List P0 tasks regardless of type]

   ## 🤖 AI Can Execute Now
   [AI-solo tasks that are Ready and not blocked]

   ## 🤝 Collaboration Needed
   [Collab tasks that are Ready, note what input is needed]

   ## 👤 Human Only
   [Human-only tasks that are Ready]

   ## 🚫 Blocked
   [All blocked tasks with what's blocking them]

4. **Post to Slack** channel #seo-skill-tasks

5. **Update Notion:**
   - Set "Last AI Review" to today
   - Add analysis notes to "AI Notes" field

6. **Ask for approval** to proceed with AI-solo tasks
```

### `/notion-update-task`

```markdown
Update a task in Notion after completing work.

Ask me:
1. Which task did you complete? (task name or Notion URL)
2. What was accomplished?
3. Any follow-up tasks to create?
4. Any blockers encountered?

Then:
1. Update the task status in Notion to "Done" (or appropriate status)
2. Add completion notes to the task
3. Create any follow-up tasks
4. Update "Blocked By" for dependent tasks
5. Post completion message to Slack
```

### `/notion-create-task`

```markdown
Create a new task in the Notion database.

Ask me:
1. Task name/description
2. Type: 🤖 AI-solo, 🤝 Collaboration, or 👤 Human-only?
3. Priority: P0, P1, P2, or P3?
4. Effort estimate: S, M, L, or XL?
5. Project/Phase?
6. Any blockers?

Then:
1. Create the task in Notion with all properties
2. Post notification to Slack
3. If blocked, set appropriate relations
```

---

## Automation Recipes

### Recipe 1: Auto-Execute AI Tasks (Advanced)

For truly autonomous operation, set up a scheduled job:

```python
# pseudo-code for scheduled automation
import schedule
import time

def morning_routine():
    # 1. Fetch tasks from Notion
    tasks = notion.query_database(database_id, filter={
        "and": [
            {"property": "Status", "select": {"equals": "Ready"}},
            {"property": "Type", "select": {"equals": "🤖 AI-solo"}}
        ]
    })

    # 2. Post plan to Slack
    slack.post_message(channel, format_daily_plan(tasks))

    # 3. Wait for approval (or auto-approve low-risk tasks)
    if auto_approve_enabled:
        for task in tasks:
            if task.priority in ["P2", "P3"]:  # Low risk
                execute_task(task)

def execute_task(task):
    # Launch Claude Code agent for the task
    agent = ClaudeAgent(task.instructions)
    result = agent.execute()

    # Update Notion
    notion.update_page(task.id, {
        "Status": "Done",
        "AI Notes": result.summary
    })

    # Notify Slack
    slack.post_message(channel, f"✅ Completed: {task.name}")

# Schedule
schedule.every().day.at("08:00").do(morning_routine)

while True:
    schedule.run_pending()
    time.sleep(60)
```

### Recipe 2: Slack-Triggered Task Execution

React to Slack messages to trigger tasks:

```
User in Slack: "@AI execute task: Add inline quick reference"

AI:
1. Search Notion for matching task
2. Confirm: "Found task 'Add inline quick reference to SKILL.md'. Execute now?"
3. On confirmation: Execute and report back
```

### Recipe 3: Blocker Resolution Alerts

When a blocking task is completed, notify and update:

```
Trigger: Task A status changes to "Done"
Check: Any tasks blocked by Task A?
Action:
  - Update blocked tasks: Remove blocker, change status to "Ready"
  - Post to Slack: "🔓 Unblocked: [Task B, Task C] - Task A is now complete"
```

---

## Implementation Checklist

### Phase 1: Basic Setup (1-2 hours)

- [ ] Create Notion database with all properties
- [ ] Create Notion views (Daily Focus, AI Queue, etc.)
- [ ] Create Slack channel #seo-skill-tasks
- [ ] Get Notion API key and share database
- [ ] Get Slack bot token with required scopes
- [ ] Configure MCP servers in Claude Code

### Phase 2: Slash Commands (1 hour)

- [ ] Create `/notion-standup` command
- [ ] Create `/notion-update-task` command
- [ ] Create `/notion-create-task` command
- [ ] Test each command

### Phase 3: Automation (2-3 hours)

- [ ] Set up Slack workflow for daily reminder
- [ ] Set up Notion → Slack notifications (completion, blockers)
- [ ] Test full daily workflow manually
- [ ] Document the process

### Phase 4: Advanced (Optional)

- [ ] Set up scheduled auto-execution script
- [ ] Implement Slack-triggered execution
- [ ] Add blocker resolution automation
- [ ] Create dashboard for observability

---

## Daily Usage Guide

### Morning (5 minutes)
1. Check Slack for daily standup message
2. Review AI recommendations
3. Approve or modify the plan
4. Reply with ✅ to let AI proceed

### During Work
1. Use `/notion-create-task` for new tasks
2. Discuss in Slack threads
3. AI executes approved tasks autonomously
4. Get completion notifications

### End of Day (2 minutes)
1. Check Slack for completed tasks
2. Review any blockers surfaced
3. Adjust priorities for tomorrow if needed

### Weekly (15 minutes)
1. Review "All Tasks" view in Notion
2. Archive completed tasks
3. Reassess priorities
4. Plan next week's focus

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Notion MCP not connecting | Check API key, ensure database is shared with integration |
| Slack messages not posting | Verify bot token, check channel ID, ensure bot is in channel |
| Tasks not updating | Check Notion permissions, verify database ID |
| AI executing wrong tasks | Review Type labels, ensure Status workflow is correct |
| Blockers not resolving | Check "Blocked By" relations are set correctly |
