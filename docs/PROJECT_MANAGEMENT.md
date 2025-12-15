# Project Management & Automation Setup

**Purpose:** Efficient workflow for iterating on the Getaround SEO Content Optimizer skill using Claude Code, VS Code, GitHub, and Slack.

---

## 1. Recommended Tool Stack

### 1.1 Core Tools

| Tool | Purpose | Integration |
|------|---------|-------------|
| **Claude Code** | Skill development, testing, iteration | Primary development environment |
| **VS Code** | Code editing, file management | Claude Code extension |
| **GitHub** | Version control, issue tracking | Repository + Projects |
| **Slack** | Team communication | GitHub notifications |
| **Google Sheets** | Task tracking, metrics | Manual or Zapier |

### 1.2 Automation Tools (Optional)

| Tool | Purpose | Setup Effort |
|------|---------|--------------|
| **GitHub Actions** | Automated testing, deployment | Medium |
| **Zapier/Make** | Cross-tool automation | Low |
| **GitHub Projects** | Kanban board, roadmap | Low |
| **Slack Workflows** | Daily standup automation | Low |

---

## 2. Recommended Workflow

### 2.1 Daily Workflow

```
┌─────────────────────────────────────────────────────────────┐
│  MORNING (Automated)                                        │
├─────────────────────────────────────────────────────────────┤
│  1. GitHub Action runs at 08:00                             │
│  2. Generates daily task review                             │
│  3. Posts to Slack #seo-skill-dev                           │
│  4. Categorizes tasks:                                      │
│     🤖 AI can do alone                                      │
│     🤝 Collaboration needed                                 │
│     👤 Human only                                           │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│  WORK SESSION                                               │
├─────────────────────────────────────────────────────────────┤
│  1. Review morning summary in Slack                         │
│  2. Open Claude Code for AI tasks                           │
│  3. Use VS Code for manual edits                            │
│  4. Commit changes to feature branch                        │
│  5. Create PR when feature complete                         │
└─────────────────────────────────────────────────────────────┘
                           │
                           ▼
┌─────────────────────────────────────────────────────────────┐
│  END OF DAY                                                 │
├─────────────────────────────────────────────────────────────┤
│  1. Update task status in GitHub Issues                     │
│  2. Push all changes                                        │
│  3. Add notes for next session                              │
└─────────────────────────────────────────────────────────────┘
```

### 2.2 Task Categorization Framework

Use these labels in GitHub Issues:

| Label | Meaning | Example |
|-------|---------|---------|
| `🤖 ai-solo` | Claude can complete independently | "Add inline quick reference to SKILL.md" |
| `🤝 ai-collab` | Needs human input + AI execution | "Create Spain market context" |
| `👤 human-only` | Requires human judgment/access | "Get GSC data export" |
| `⏰ daily-review` | Include in morning review | Any active task |
| `📊 needs-data` | Blocked on data/input | "Performance data for Spain" |
| `✅ ready-to-test` | Complete, needs verification | Any finished task |

---

## 3. GitHub Setup

### 3.1 Repository Structure

```
getaround-seo-content-optimizer/
├── .github/
│   ├── workflows/
│   │   ├── daily-review.yml      # Morning task review
│   │   ├── test-skill.yml        # Skill validation
│   │   └── deploy.yml            # Deploy to production
│   ├── ISSUE_TEMPLATE/
│   │   ├── task.md               # Standard task template
│   │   ├── bug.md                # Bug report template
│   │   └── feature.md            # Feature request template
│   └── CODEOWNERS                # Review requirements
├── docs/
│   ├── PROJECT_ANALYSIS.md       # This file
│   ├── PROJECT_MANAGEMENT.md     # Workflow documentation
│   ├── MAINTENANCE.md            # Update procedures
│   └── VALIDATION.md             # Quality checklist
├── references/
│   └── [existing structure]
├── examples/                      # Gold standard articles
├── SKILL.md
├── README.md
└── CHANGELOG.md
```

### 3.2 GitHub Projects Board

Create a project board with these columns:

| Column | Purpose |
|--------|---------|
| **Backlog** | All tasks not yet prioritized |
| **This Week** | Tasks planned for current week |
| **In Progress** | Currently being worked on |
| **In Review** | Waiting for PR review or testing |
| **Done** | Completed this week |

### 3.3 Issue Template (task.md)

```markdown
---
name: Task
about: Standard task for skill development
title: '[TASK] '
labels: '⏰ daily-review'
assignees: ''
---

## Description
[Clear description of what needs to be done]

## Type
- [ ] 🤖 AI can do alone
- [ ] 🤝 Collaboration needed
- [ ] 👤 Human only

## Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2

## Dependencies
- Blocked by: #issue-number (if any)
- Blocks: #issue-number (if any)

## Effort Estimate
- [ ] Small (<1h)
- [ ] Medium (1-4h)
- [ ] Large (4-8h)
- [ ] XL (>8h)

## Notes
[Any additional context]
```

---

## 4. Automated Daily Review System

### 4.1 GitHub Action: Daily Review

Create `.github/workflows/daily-review.yml`:

```yaml
name: Daily Task Review

on:
  schedule:
    - cron: '0 7 * * 1-5'  # 08:00 CET on weekdays
  workflow_dispatch:  # Manual trigger

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Generate Task Review
        uses: actions/github-script@v7
        with:
          script: |
            const issues = await github.rest.issues.listForRepo({
              owner: context.repo.owner,
              repo: context.repo.repo,
              state: 'open',
              labels: '⏰ daily-review'
            });

            let aiSolo = [];
            let aiCollab = [];
            let humanOnly = [];
            let blocked = [];

            for (const issue of issues.data) {
              const labels = issue.labels.map(l => l.name);
              const item = `- [#${issue.number}](${issue.html_url}) ${issue.title}`;

              if (labels.includes('📊 needs-data')) {
                blocked.push(item);
              } else if (labels.includes('🤖 ai-solo')) {
                aiSolo.push(item);
              } else if (labels.includes('🤝 ai-collab')) {
                aiCollab.push(item);
              } else if (labels.includes('👤 human-only')) {
                humanOnly.push(item);
              }
            }

            const summary = `
            # Daily Task Review - ${new Date().toLocaleDateString()}

            ## 🤖 AI Can Do Alone
            ${aiSolo.length ? aiSolo.join('\n') : '_No tasks_'}

            ## 🤝 Collaboration Needed
            ${aiCollab.length ? aiCollab.join('\n') : '_No tasks_'}

            ## 👤 Human Only
            ${humanOnly.length ? humanOnly.join('\n') : '_No tasks_'}

            ## 📊 Blocked (Needs Data)
            ${blocked.length ? blocked.join('\n') : '_No blocked tasks_'}

            ---
            _Total open tasks: ${issues.data.length}_
            `;

            core.setOutput('summary', summary);

      - name: Post to Slack
        uses: slackapi/slack-github-action@v1.24.0
        with:
          channel-id: 'seo-skill-dev'
          slack-message: ${{ steps.review.outputs.summary }}
        env:
          SLACK_BOT_TOKEN: ${{ secrets.SLACK_BOT_TOKEN }}
```

### 4.2 Slack Integration

1. Create Slack channel: `#seo-skill-dev`
2. Create Slack app with Bot Token
3. Add Bot Token to GitHub Secrets as `SLACK_BOT_TOKEN`
4. Invite bot to channel

### 4.3 Morning Summary Format

Every weekday at 08:00, you'll receive:

```
# Daily Task Review - 2025-12-16

## 🤖 AI Can Do Alone
- #12 Add inline quick reference to SKILL.md
- #15 Create validation checklist template

## 🤝 Collaboration Needed
- #8 Create Spain market context (needs market brief first)
- #14 Add example article for Norway

## 👤 Human Only
- #9 Export GSC data for Spain
- #11 Review and approve example articles

## 📊 Blocked (Needs Data)
- #10 Create Spain performance_data_es.md (waiting for #9)

---
_Total open tasks: 6_
```

---

## 5. Claude Code Best Practices

### 5.1 Session Management

| Practice | Why |
|----------|-----|
| Start with context | "I'm working on the SEO skill. Current task: #12" |
| Reference issues | "See GitHub issue #12 for requirements" |
| Commit frequently | Small, atomic commits for easy rollback |
| Use TodoWrite | Keep Claude aware of progress |
| End with summary | "Here's what we accomplished..." |

### 5.2 Effective Prompts for This Project

**For AI-solo tasks:**
```
I need you to complete GitHub issue #12: "Add inline quick reference to SKILL.md"

Requirements:
- Add a "Quick Reference" section after the frontmatter
- Include Norway and France at-a-glance summaries
- Keep it under 100 lines
- Link to detailed references

Please read SKILL.md first, then make the changes.
```

**For collaboration tasks:**
```
I'm working on GitHub issue #8: "Create Spain market context"

I have this market brief: [paste brief]

Help me create market_context_es.md following the same structure as market_context_no.md and market_context_fr.md.
```

**For review tasks:**
```
Please review the changes in this PR: [link]

Check against:
1. Does it follow existing patterns?
2. Is the formatting consistent?
3. Are there any errors or omissions?
```

### 5.3 Useful Claude Code Commands

| Command | Purpose |
|---------|---------|
| `/init` | Start new session with context |
| `/clear` | Clear context for fresh start |
| `/cost` | Check token usage |
| `/help` | See available commands |

### 5.4 Custom Slash Commands (Recommended)

Create `.claude/commands/` for project-specific commands:

**`/daily-standup.md`:**
```markdown
Please review the current state of the SEO skill project:

1. Read docs/PROJECT_ANALYSIS.md for context
2. Check GitHub issues labeled "⏰ daily-review"
3. Summarize:
   - What's in progress
   - What's blocked
   - What I should focus on today
4. Suggest which tasks you can help with
```

**`/test-skill.md`:**
```markdown
Test the SEO skill by:

1. Read SKILL.md
2. Simulate analyzing this article: [URL or paste content]
3. Check if all steps are followed correctly
4. Report any issues with context loading or workflow
```

**`/update-task.md`:**
```markdown
I've completed work on a task. Help me:

1. Summarize what was accomplished
2. Draft a commit message
3. Update any relevant documentation
4. Identify next steps or follow-up tasks
```

---

## 6. VS Code Setup

### 6.1 Recommended Extensions

| Extension | Purpose |
|-----------|---------|
| Claude Code | AI integration |
| GitHub Pull Requests | PR management |
| GitLens | Git history visualization |
| Markdown All in One | Markdown editing |
| YAML | YAML validation |
| JSON Tools | JSON formatting |

### 6.2 Workspace Settings

Create `.vscode/settings.json`:

```json
{
  "editor.formatOnSave": true,
  "editor.wordWrap": "on",
  "files.trimTrailingWhitespace": true,
  "markdown.preview.breaks": true,
  "[markdown]": {
    "editor.defaultFormatter": "yzhang.markdown-all-in-one"
  },
  "[json]": {
    "editor.defaultFormatter": "vscode.json-language-features"
  }
}
```

### 6.3 Recommended Tasks

Create `.vscode/tasks.json`:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Validate JSON files",
      "type": "shell",
      "command": "python -m json.tool references/shared/*.json > /dev/null && echo 'JSON valid'",
      "problemMatcher": []
    },
    {
      "label": "Count lines",
      "type": "shell",
      "command": "wc -l SKILL.md references/**/*.md references/**/*.json | tail -1",
      "problemMatcher": []
    },
    {
      "label": "Check links",
      "type": "shell",
      "command": "grep -r 'references/' SKILL.md | head -20",
      "problemMatcher": []
    }
  ]
}
```

---

## 7. Metrics & Tracking

### 7.1 Weekly Metrics (Google Sheets)

Track these metrics weekly:

| Metric | How to Measure | Target |
|--------|----------------|--------|
| Tasks completed | GitHub Issues closed | 5-10/week |
| AI-solo completion rate | AI tasks / total | >40% |
| Skill test success rate | Pass / total tests | >90% |
| Article production time | Time tracking | <60 min |
| First-draft acceptance | Approved / submitted | >70% |

### 7.2 Monthly Review Checklist

```markdown
## Monthly Review - [Month Year]

### Progress
- [ ] All planned tasks completed?
- [ ] Any scope changes?
- [ ] Blockers encountered?

### Quality
- [ ] Skill tested with 5+ articles?
- [ ] User feedback collected?
- [ ] Performance data updated?

### Process
- [ ] Daily reviews working?
- [ ] Automation running smoothly?
- [ ] Documentation up to date?

### Next Month
- [ ] Priority tasks identified
- [ ] Dependencies cleared
- [ ] Resources allocated
```

---

## 8. Quick Start Guide

### Day 1 Setup (30 minutes)

1. **GitHub**
   - [ ] Create project board with columns
   - [ ] Add issue templates
   - [ ] Create initial issues from PROJECT_ANALYSIS.md

2. **Slack**
   - [ ] Create `#seo-skill-dev` channel
   - [ ] Set up Slack app (optional for automation)

3. **VS Code**
   - [ ] Install recommended extensions
   - [ ] Add workspace settings

4. **Claude Code**
   - [ ] Create custom slash commands
   - [ ] Test skill loading

### Daily Routine (5-10 minutes admin)

**Morning:**
1. Check Slack for daily review (or run `/daily-standup`)
2. Pick tasks for the day
3. Update GitHub Issues to "In Progress"

**During work:**
1. Use Claude Code for AI tasks
2. Commit frequently
3. Update task notes as needed

**End of day:**
1. Push all changes
2. Update issue status
3. Add blockers/notes for tomorrow

---

## 9. Troubleshooting

| Issue | Solution |
|-------|----------|
| Daily review not posting | Check GitHub Action logs, verify Slack token |
| Claude not loading context | Use explicit file reads, check paths |
| Merge conflicts | Pull before starting, use feature branches |
| Skill not triggering | Check description in SKILL.md frontmatter |
| Slow Claude responses | Reduce context, be more specific |

---

## 10. Resources

- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Slack API Documentation](https://api.slack.com/)
- [Project Repository](https://github.com/markusmosand/getaround-seo-content-optimizer)
