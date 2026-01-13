# Claude Code Session Management Guide

## Quick Reference Card

### Essential Commands
```bash
# Start Claude Code in project directory
cd /path/to/getaround-seo-automation
claude

# Resume last session
claude --continue
# or
claude -c

# Resume specific session
claude --resume

# Inside Claude Code:
/clear          # Wipe conversation, keep CLAUDE.md
/compact        # Compress conversation, keep context
/context        # Check context usage
/init           # Generate CLAUDE.md from codebase
Shift+Tab       # Toggle plan mode (no edits)
Ctrl+C          # Interrupt Claude
Escape          # Interrupt mid-response
```

### Thinking Triggers (use for complex tasks)
```
"think"         → Standard extended thinking
"think hard"    → More computation
"think harder"  → Even more
"ultrathink"    → Maximum thinking budget
```

---

## Session Workflow

### Starting a New Session

**Step 1: Navigate to project**
```bash
cd /path/to/getaround-seo-automation
claude
```

**Step 2: First message pattern**
```
Read ROADMAP.md and identify the current task.
Then read the relevant task file and create a plan.
Do not execute yet - just plan.
```

**Step 3: Review plan, then execute**
```
The plan looks good. Execute step by step.
Update the task file with progress after each major step.
```

**Step 4: Complete and close**
```
Update ROADMAP.md to mark this task complete with today's date.
Summarize what was accomplished.
```
Then: `/clear` or close terminal

---

## When to Use Each Command

### /clear - Start Fresh
Use when:
- ✅ Switching to a completely different task
- ✅ Claude seems confused or repetitive
- ✅ You've completed a task and moving to next
- ✅ Context is polluted with irrelevant discussion
- ✅ Starting work after a break

Don't use when:
- ❌ Mid-task and need continuity
- ❌ You want to reference earlier conversation

### /compact - Preserve Key Context
Use when:
- ✅ Context is at 70-80%
- ✅ You want to continue but reduce tokens
- ✅ Long session but still on same task
- ✅ Need to preserve decisions made

Don't use when:
- ❌ About to switch tasks (use /clear instead)
- ❌ Session just started

### claude --continue - Resume Last Session
Use when:
- ✅ Terminal crashed mid-task
- ✅ Accidentally closed terminal
- ✅ Need to reference something from last session
- ✅ Continuing work from earlier today

### Shift+Tab (Plan Mode) - No Edits
Use when:
- ✅ Starting a complex task
- ✅ Want Claude to analyze without changing files
- ✅ Reviewing architecture decisions
- ✅ Creating task breakdown

---

## Session Patterns by Task Type

### Pattern A: Data Extraction (GSC Queries)
```
Session length: 30-60 min
Context usage: Medium (60-80%)

1. Read task file with query specifications
2. Execute queries one by one
3. Save results to files
4. Create summary tables
5. Update ROADMAP.md
6. /clear → Next task
```

### Pattern B: Analysis & Classification
```
Session length: 45-90 min
Context usage: High (can hit 90%+)

1. Load raw data files
2. Analyze patterns
3. /compact if hitting 80%
4. Create classification table
5. Document findings
6. Update task file
7. /clear → Next task
```

### Pattern C: Document Creation
```
Session length: 20-45 min
Context usage: Medium

1. Read source data
2. Use plan mode (Shift+Tab) to outline
3. Generate document sections
4. Review and refine
5. Save to output location
6. /clear → Next task
```

### Pattern D: Workflow Building (n8n)
```
Session length: 60-120 min
Context usage: High

1. Read architecture specs
2. Plan workflow structure
3. Build nodes incrementally
4. Test each section
5. /compact if needed
6. Complete and test full workflow
7. Document in task file
8. /clear → Next workflow
```

---

## Context Management Strategy

### Watch the Context Bar
Claude Code shows context usage. Monitor these thresholds:

| Usage | Action |
|-------|--------|
| 0-50% | Work normally |
| 50-70% | Consider finishing current subtask |
| 70-80% | Use /compact or wrap up task |
| 80-90% | Finish immediately, save state |
| 90%+ | Risk of degraded performance |

### Signs Claude is Struggling
- Forgetting earlier decisions
- Repeating itself
- Contradicting previous statements
- Generic/vague responses
- Ignoring task file details

**Fix:** `/compact` or `/clear` and restart with fresh context

---

## Session Log Template

Add to ROADMAP.md after each session:

```markdown
## Session Log

| # | Date | Time | Phase | Task | Context% | Status | Notes |
|---|------|------|-------|------|----------|--------|-------|
| 1 | 2026-01-07 | 45min | 0A | France GSC | 65% | ✅ | Extracted all queries |
| 2 | 2026-01-07 | 60min | 0A | France Class | 82% | ✅ | Used /compact at 75% |
| 3 | 2026-01-08 | 30min | 0A | France Hypo | 55% | ✅ | |
```

---

## Recommended Session Schedule

### Phase 0 (Estimated: 6-8 sessions)

| Session | Task | Est. Time | Notes |
|---------|------|-----------|-------|
| 1 | France GSC extraction | 45 min | Run all queries |
| 2 | France classification | 60 min | May need /compact |
| 3 | France hypothesis testing | 45 min | |
| 4 | Norway GSC extraction | 45 min | Run all queries |
| 5 | Norway classification | 60 min | May need /compact |
| 6 | Norway hypothesis testing | 45 min | |
| 7 | Cross-market synthesis | 60 min | |
| 8 | Skill update planning | 30 min | |

### Between Sessions
- Update ROADMAP.md with progress
- Log session in session table
- Note any blockers or questions
- Identify next task

---

## Prompts for Each Phase 0 Task

### Session 1: France GSC Extraction
```
Read @ROADMAP.md and @tasks/phase0/000-france-gsc-extraction.md

Execute each GSC query listed in the task file.
Save raw results to analysis/france_raw/
Create summary tables in analysis/FRANCE_BLOG_ANALYSIS_2025.md

Start with Query 1 and proceed through all 18 queries.
```

### Session 2: France Classification
```
Read @ROADMAP.md and @tasks/phase0/001-france-content-classification.md

Load the top 100 pages from analysis/france_raw/pages_full_year.json
Classify each article using the taxonomy in the task file.
Add classification results to analysis/FRANCE_BLOG_ANALYSIS_2025.md
```

### Session 3: France Hypothesis Testing
```
Read @ROADMAP.md and @tasks/phase0/002-france-hypothesis-testing.md

Using the classified data, test each hypothesis.
Document results with actual numbers vs expected.
Mark each hypothesis as CONFIRMED, REJECTED, or PARTIAL.
```

### Session 4: Norway GSC Extraction
```
Read @ROADMAP.md and @tasks/phase0/010-norway-gsc-extraction.md

Execute each GSC query for /blogg/.
Save raw results to analysis/norway_raw/
Create summary in analysis/NORWAY_BLOG_ANALYSIS_2025.md
```

### Session 5: Norway Classification
```
Read @ROADMAP.md and @tasks/phase0/011-norway-content-classification.md

Classify top 100 Norway articles using the task taxonomy.
Add results to analysis/NORWAY_BLOG_ANALYSIS_2025.md
```

### Session 6: Norway Hypothesis Testing
```
Read @ROADMAP.md and @tasks/phase0/012-norway-hypothesis-testing.md

Test all Norway hypotheses against classified data.
Document findings and strategic implications.
```

### Session 7: Cross-Market Synthesis
```
Read @ROADMAP.md and @tasks/phase0/020-cross-market-synthesis.md

Compare France and Norway findings.
Identify universal patterns and market-specific strategies.
Create analysis/CROSS_MARKET_SYNTHESIS.md
Document skill update requirements.
```

---

## Troubleshooting

### "Claude forgot what we discussed"
→ Context window full. Use `/compact` or `/clear` and re-state key points.

### "Claude keeps making the same mistake"
→ Add instruction to CLAUDE.md: `# DO NOT: [specific mistake]`

### "MCP tool not working"
→ Check connection: Ask Claude to run `mcp__gscServer__list_properties`

### "Task is too big for one session"
→ Break into subtasks. Update task file with checkboxes for each subtask.

### "Lost track of where I am"
→ Ask Claude: `Read ROADMAP.md and tell me the current status and next action`

---

## Best Practices Summary

1. **One task per session** - /clear between tasks
2. **Start with ROADMAP.md** - Always orient first
3. **Use plan mode for complex work** - Shift+Tab before executing
4. **Save progress to files** - Don't rely on chat memory
5. **Monitor context usage** - /compact at 70-80%
6. **Log sessions** - Track time and status in ROADMAP.md
7. **Update task files** - Mark checkboxes as you complete steps
8. **Keep CLAUDE.md short** - <300 lines, use @imports
9. **Use thinking triggers** - "think hard" for complex analysis
10. **Fresh start when stuck** - /clear is your friend
