Perform the daily standup routine for the SEO Content Optimizer project.

## Prerequisites
- Notion MCP must be configured
- Slack MCP must be configured (optional, for posting)

## Step 1: Fetch Tasks from Notion

Query the SEO Skill Tasks database:
- Get all tasks where Status is NOT "Done"
- Include the "Blocked By" relation
- Get properties: Task, Status, Type, Priority, Effort, Blocked By, AI Notes

## Step 2: Analyze Each Task

For each task, determine:

1. **Is it blocked?**
   - Check if "Blocked By" contains any incomplete tasks
   - A task is blocked if ANY blocking task has Status != "Done"

2. **Is it ready?**
   - Status = "Ready" AND not blocked

3. **Can AI execute?**
   - Type = "🤖 AI-solo" AND ready AND not blocked

4. **Priority level?**
   - P0 = Critical (do today regardless of type)
   - P1 = High (should be done this week)
   - P2 = Medium (nice to have)
   - P3 = Low (backlog)

## Step 3: Generate Daily Plan

Create a summary in this format:

```
# 🌅 Daily Standup - [Today's Date]

## 🔥 Critical (P0)
[List all P0 tasks regardless of type - these need attention today]

## 🤖 AI Can Execute Now
[List AI-solo tasks that are Ready and not blocked]
For each: Show priority, effort, and brief description

## 🤝 Collaboration Needed
[List Collaboration tasks that are Ready]
For each: Note what input/decision is needed from human

## 👤 Human Only
[List Human-only tasks that are Ready]

## 🚫 Blocked
[List all blocked tasks]
For each: Show what's blocking it (task name)

## 📊 Summary
- Total open tasks: X
- Ready for AI: X
- Needs collaboration: X
- Blocked: X

---
**Should I proceed with the AI-solo tasks?**
Reply with ✅ to approve, or provide specific instructions.
```

## Step 4: Update Notion (Optional)

If you have write access:
- Update "Last AI Review" date on analyzed tasks
- Add brief analysis to "AI Notes" field

## Step 5: Post to Slack (Optional)

If Slack MCP is configured:
- Post the daily plan to #seo-skill-tasks channel
- Use the formatted message above

## Step 6: Await Instructions

After presenting the plan:
- Wait for approval to execute AI-solo tasks
- Or accept specific instructions for what to work on

---

If Notion MCP is not available, fall back to reading `docs/TODO.md` instead.
