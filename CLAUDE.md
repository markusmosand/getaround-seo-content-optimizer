# Getaround SEO Automation Project

## Quick Reference
See @ROADMAP.md for current phase and progress.
See @docs/project-context.md for detailed background.
See @tasks/ for task specifications.

## Project Mission
Build an AI-powered SEO content automation system for Getaround using n8n workflows.
- Markets: Norway (`/blogg/`), France (`/blog/`)
- Goal: 5-6 hour manual process → 1-hour AI-assisted workflow
- Output: n8n workflows for Research → Planning → Writing → Review → Monitoring

## Session Protocol

### Before Starting ANY Work
1. Read this file + @ROADMAP.md
2. Identify the current active task (marked with `[-]`)
3. Read the relevant task file in `tasks/`
4. Use **plan mode** (Shift+Tab) for complex work

### During Work
- Save progress to files, not just chat
- Update task file with findings/decisions
- At 80% context → use `/compact` or finish and `/clear`

### After Completing a Task
1. Update ROADMAP.md: `[-]` → `[x]` with timestamp
2. Update task file with "Completed" status and summary
3. `/clear` before starting next task

### When to Start a NEW Session
⚠️ START FRESH SESSION when:
- Switching between phases (e.g., Phase 0 → Phase 1)
- Context reaches 80%+
- Task is complete and you're moving to next task
- Claude seems confused or repetitive
- You've been in same session for 30+ minutes of heavy work

## MCP Tools Available

### Google Search Console (gscServer)
```
mcp__gscServer__list_properties
mcp__gscServer__get_search_analytics
mcp__gscServer__get_advanced_search_analytics
mcp__gscServer__compare_search_periods
```

### n8n Cloud
```
mcp__n8n-cloud__n8n_health_check
mcp__n8n-cloud__n8n_create_workflow
mcp__n8n-cloud__n8n_list_workflows
mcp__n8n-cloud__search_nodes
```

## Progress Tracking Convention
- `[ ]` = Todo
- `[-]` = In Progress 🏗️ YYYY-MM-DD
- `[x]` = Completed ✅ YYYY-MM-DD

## Key Constraints
- Phase 0 MUST complete before Phase 1+ (data validation first)
- Human approval required before any workflow goes to production
- All market assumptions must be validated with GSC data
- Save all analysis outputs to `analysis/` directory

## Thinking Triggers
Use these phrases for complex reasoning:
- "think" → standard extended thinking
- "think hard" → more computation
- "think harder" → even more
- "ultrathink" → maximum thinking budget

## Current Focus
👉 Check @ROADMAP.md for the active task.
