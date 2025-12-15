# Task List - Getaround SEO Content Optimizer

**Last AI Review:** Not yet reviewed
**Next Review:** Daily at 08:00

---

## How This Works

This file is reviewed daily by Claude Code (via `/daily-standup` command or GitHub Action).

Each task has:
- **Status:** `[ ]` todo, `[~]` in progress, `[x]` done, `[!]` blocked
- **Type:** 🤖 AI-solo, 🤝 Collaboration, 👤 Human-only
- **Priority:** P0 (critical), P1 (high), P2 (medium), P3 (low)
- **Effort:** S (small <1h), M (medium 1-4h), L (large 4-8h), XL (>8h)

---

## Phase 1: Reliability

### P0 - Critical

- [ ] 🤝 **Implement hybrid approach** [M]
  - Add inline quick reference to SKILL.md
  - Consolidate critical context (50-100 lines)
  - Keep detailed references as linked files
  - _Collaboration: Need to decide what's "critical" vs "detailed"_

- [ ] 🤖 **Verify reference file links** [S]
  - Check all paths in SKILL.md work
  - Test in Claude Code session
  - _AI can do: Just needs file access_

### P1 - High

- [ ] 🤖 **Create MAINTENANCE.md** [S]
  - Document quarterly update procedure
  - List files that need regular updates
  - Define update triggers
  - _AI can do: Follow pattern from other docs_

- [ ] 🤖 **Add CHANGELOG.md** [S]
  - Create initial changelog
  - Document v1.0 features
  - _AI can do: Standard format_

---

## Phase 2: Spain Support

### P1 - High

- [ ] 👤 **Export GSC data for Spain** [S]
  - Need access to Spanish blog GSC
  - Export last 90 days performance
  - _Human only: Requires GSC access_

- [ ] 👤 **Get Spanish marketing guidelines** [S]
  - Contact stakeholder for brand guidelines
  - Confirm tone (tú vs usted)
  - _Human only: Stakeholder input_

- [!] 🤝 **Create market_context_es.md** [M]
  - Research Spanish market
  - Document competitors, USPs
  - Add fleet data if available
  - _Blocked by: GSC data, marketing guidelines_

- [!] 🤝 **Create tone_guide_es.md** [M]
  - Establish tú/usted convention
  - Create vocabulary banks
  - Define hook patterns
  - _Blocked by: Marketing guidelines_

- [!] 🤝 **Create performance_data_es.md** [M]
  - Analyze GSC data
  - Identify top performers
  - Set benchmarks
  - _Blocked by: GSC data_

- [!] 🤖 **Create owner_content_guide_es.md** [S]
  - Adapt from FR/NO templates
  - Localize terminology
  - Add Spanish income examples
  - _Blocked by: Market context_

- [!] 🤖 **Update SKILL.md for Spain** [S]
  - Add ES to market detection
  - Add ES calibrations
  - Link new reference files
  - _Blocked by: All ES files complete_

---

## Phase 3: Quality Assurance

### P2 - Medium

- [ ] 🤝 **Create example_listicle_no.md** [M]
  - Use "Topp 5 aktiviteter for barn i Oslo" as base
  - Annotate with comments explaining choices
  - _Collaboration: Need to select/approve example_

- [ ] 🤝 **Create example_b2b_fr.md** [M]
  - Use "Déplacement professionnel" as base
  - Annotate SEO/AEO decisions
  - _Collaboration: Need to select/approve example_

- [!] 🤝 **Create example_consumer_es.md** [M]
  - Create from scratch following patterns
  - _Blocked by: Spain support complete_

- [ ] 🤖 **Create VALIDATION.md** [M]
  - Checklist for reviewing skill outputs
  - Format validation rules
  - Content quality checks
  - _AI can do: Based on existing guidelines_

---

## Phase 4: Rollout

### P3 - Low

- [ ] 🤝 **Create training materials** [M]
  - Quick start guide for marketing team
  - Common use cases
  - Troubleshooting FAQ
  - _Collaboration: Need user perspective_

- [ ] 🤖 **Create slash commands** [S]
  - `/seo-analyze` - Quick analysis workflow
  - `/seo-rewrite` - Full rewrite workflow
  - `/seo-validate` - Check output quality
  - _AI can do: Standard Claude Code format_

- [ ] 👤 **Conduct user testing** [M]
  - Schedule session with marketing team
  - Collect feedback
  - Document issues
  - _Human only: Requires coordination_

---

## Backlog (Not Prioritized)

- [ ] 🤝 **Integration with GSC API** [XL]
- [ ] 🤝 **A/B testing framework** [L]
- [ ] 🤖 **Market expansion template** [M]
- [ ] 👤 **Define success metrics tracking** [M]
- [ ] 🤝 **Add Germany support** [L]
- [ ] 🤝 **Add Belgium support** [L]

---

## Completed

_Move tasks here when done_

### 2025-12-15
- [x] 🤝 **Initial skill development** - v1.0 complete for NO/FR
- [x] 🤖 **Create PROJECT_ANALYSIS.md**
- [x] 🤖 **Create PROJECT_MANAGEMENT.md**
- [x] 🤖 **Create TODO.md**
- [x] 🤖 **Push to GitHub**

---

## AI Review Notes

_This section is updated by Claude during daily reviews_

### Latest Review: [DATE]

**Recommended focus today:**
1. [Task]
2. [Task]
3. [Task]

**Blockers to address:**
- [Blocker]

**Tasks I can complete independently:**
- [Task]

**Questions for human:**
- [Question]
