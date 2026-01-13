Update a task in the Notion database after completing work.

## Information Needed

Please provide:

1. **Which task?** (task name, or paste the Notion URL)
2. **New status?** (Done, In Review, Blocked, etc.)
3. **What was accomplished?** (Brief summary for AI Notes)
4. **Any follow-up tasks?** (New tasks that emerged)
5. **Any blockers encountered?** (For other tasks to know)

## What I'll Do

### Step 1: Find the Task
- Search Notion database for the task by name or ID
- Confirm I found the right one before updating

### Step 2: Update Task Properties
- Status → New status
- AI Notes → Add completion summary with timestamp
- Last AI Review → Today's date

### Step 3: Handle Dependencies
If task was blocking other tasks:
- Find tasks where "Blocked By" includes this task
- Update their status from "Blocked" to "Ready" (if no other blockers)
- Add note: "Unblocked - [task name] completed"

### Step 4: Create Follow-up Tasks (if any)
For each follow-up:
- Create new task in Notion
- Set appropriate Type, Priority, Effort
- Link as "Blocked By" if dependent on something

### Step 5: Notify
- Post update to Slack #seo-skill-tasks
- Format: "✅ Completed: [Task Name] - [Brief summary]"
- If tasks were unblocked: "🔓 Unblocked: [Task names]"

### Step 6: Confirm
Show summary of all changes made.

---

## Quick Update (if you just want to mark done)

You can also just say:
- "Mark [task name] as done"
- "Complete [task name] - [what was done]"

I'll handle the rest automatically.
