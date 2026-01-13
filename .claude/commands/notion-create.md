Create a new task in the Notion SEO Skill Tasks database.

## Quick Create

Just tell me what you need:
- "Create task: [description]"
- "Add task: [description] - P1, AI can do it"
- "New task: [description] blocking Spain support"

I'll ask clarifying questions if needed.

## Full Task Creation

For complete task details, I need:

### Required
1. **Task name** - Clear, actionable description
   - Good: "Add inline quick reference to SKILL.md"
   - Bad: "Fix stuff"

### Optional (I'll ask if not provided)

2. **Type** - Who should do this?
   - 🤖 **AI-solo** - I can complete independently
   - 🤝 **Collaboration** - Needs human input + AI execution
   - 👤 **Human-only** - Requires human access/judgment

3. **Priority** - How urgent?
   - **P0 Critical** - Must do today, blocks everything
   - **P1 High** - Should do this week
   - **P2 Medium** - Important but not urgent
   - **P3 Low** - Backlog, nice to have

4. **Effort** - How long will it take?
   - **S** - Small (<1 hour)
   - **M** - Medium (1-4 hours)
   - **L** - Large (4-8 hours)
   - **XL** - Extra large (>8 hours)

5. **Project** - Which phase?
   - Phase 1: Reliability
   - Phase 2: Spain
   - Phase 3: QA
   - Phase 4: Rollout

6. **Blocked By** - Any dependencies?
   - List tasks that must be done first
   - I'll set up the relations

7. **Due Date** - When should it be done?

## What I'll Do

1. **Validate** - Check task doesn't already exist
2. **Create** - Add to Notion with all properties
3. **Set Status** - "Ready" if no blockers, "Blocked" if has dependencies
4. **Link** - Set up "Blocked By" relations if needed
5. **Notify** - Post to Slack: "�� New task: [name]"
6. **Confirm** - Show the created task with link

## Bulk Create

You can also give me multiple tasks:
```
Create these tasks:
1. Add inline quick reference - P1, AI-solo, M
2. Create MAINTENANCE.md - P1, AI-solo, S
3. Export GSC data for Spain - P1, Human-only, S
```

I'll create all of them and show a summary.
