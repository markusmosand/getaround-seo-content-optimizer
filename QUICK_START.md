# Quick Start - Copy-Paste Prompts

## First Time Setup

1. Copy all files from this package to your project folder
2. Open terminal and navigate to your project:
   ```bash
   cd /path/to/your/project
   ```
3. Start Claude Code:
   ```bash
   claude
   ```

---

## Session 1: France GSC Data Extraction

**Copy and paste this as your first message:**

```
Read @ROADMAP.md to understand the project structure.
Then read @tasks/phase0/000-france-gsc-extraction.md for this session's task.

We're starting Phase 0: Market Validation.

Execute the GSC queries listed in the task file to extract France blog (/blog/) data.

For each query:
1. Run the MCP tool with specified parameters
2. Save results summary
3. Note any errors or missing data

Start with Query 1 (Full Year - Top Pages by Impressions).

After completing all queries, create analysis/FRANCE_BLOG_ANALYSIS_2025.md with the summary tables.

Update ROADMAP.md to mark task 000 as in progress with today's date.
```

**After completion, before closing:**
```
Update ROADMAP.md:
- Mark "Extract GSC data" under 0A as complete with ✅ and today's date
- Log this session in the Session Log table

Then summarize what was accomplished and any issues encountered.
```

Then type `/clear` and close terminal.

---

## Session 2: France Content Classification

**Start fresh session, then paste:**

```
Read @ROADMAP.md to see current progress.
Then read @tasks/phase0/001-france-content-classification.md for this task.

Load the France data from analysis/FRANCE_BLOG_ANALYSIS_2025.md.

Classify the top 100 articles by:
1. Content Type (B2B, B2C, Regulatory, etc.)
2. Format (Listicle, Guide, How-to, etc.)
3. Business Fit Score (1-5)

Use the taxonomies defined in the task file.

Add classification tables to analysis/FRANCE_BLOG_ANALYSIS_2025.md.

Update ROADMAP.md to mark this task in progress.
```

**After completion:**
```
Update ROADMAP.md to mark "Classify content" as complete.
Log this session.
Summarize key findings about France content distribution.
```

Then `/clear`.

---

## Session 3: France Hypothesis Testing

```
Read @ROADMAP.md and @tasks/phase0/002-france-hypothesis-testing.md.

Using the classified data in analysis/FRANCE_BLOG_ANALYSIS_2025.md:

Test each hypothesis (H1-H6) with actual numbers.
For each hypothesis:
- Calculate the actual metrics
- Compare to expected values
- Mark as CONFIRMED, REJECTED, or PARTIAL
- Document the strategic implication

Complete the Summary Table and Strategy Implications sections.

Update ROADMAP.md when done.
```

---

## Session 4: Norway GSC Data Extraction

```
Read @ROADMAP.md and @tasks/phase0/010-norway-gsc-extraction.md.

We're now starting Phase 0B: Norway analysis.

Execute all GSC queries for Norway blog (/blogg/).
Save results to analysis/norway_raw/ and analysis/NORWAY_BLOG_ANALYSIS_2025.md.

Start with Query 1 and proceed through all 18 queries.

Pay attention to seasonality patterns in monthly data.
```

---

## Session 5: Norway Content Classification

```
Read @ROADMAP.md and @tasks/phase0/011-norway-content-classification.md.

Classify top 100 Norway articles using the Norway-specific taxonomy.

Compare patterns to what we found in France.

Add results to analysis/NORWAY_BLOG_ANALYSIS_2025.md.
```

---

## Session 6: Norway Hypothesis Testing

```
Read @ROADMAP.md and @tasks/phase0/012-norway-hypothesis-testing.md.

Test all 6 hypotheses against Norway data.

Key questions:
- Do listicles dominate as assumed?
- Is Oslo really 50%+ of city content?
- How strong is seasonality?

Document validated strategy for Norway.
```

---

## Session 7: Cross-Market Synthesis

```
Read @ROADMAP.md and @tasks/phase0/020-cross-market-synthesis.md.

Now synthesize France and Norway findings:

1. Compare market metrics side by side
2. Identify universal patterns (work in both)
3. Identify market-specific patterns
4. Document skill update requirements
5. Note workflow design implications

Create analysis/CROSS_MARKET_SYNTHESIS.md.

This completes Phase 0. Mark all Phase 0 tasks as complete in ROADMAP.md.
```

---

## Utility Prompts

### Check Current Status
```
Read @ROADMAP.md and tell me:
1. What phase are we in?
2. What's the current active task?
3. What tasks are completed?
4. What's the next task after current?
```

### Resume After Break
```
Read @ROADMAP.md and @SESSION_GUIDE.md.
Show me the session log and identify where we left off.
What should we work on next?
```

### Context Check
```
How much context are we using?
Should we /compact or /clear?
```

### Save Progress Before Closing
```
Before I close this session:
1. Update ROADMAP.md with current progress
2. Update the task file with any completed checkboxes
3. Log this session in the Session Log
4. Summarize what to do next session
```

### When Stuck
```
I'm stuck on this task. Let's:
1. Re-read the task file requirements
2. Check what we've completed so far
3. Identify the specific blocker
4. Create a plan to resolve it
```

---

## Emergency Recovery

### If Claude Seems Confused
```
/clear
```
Then:
```
Fresh start. Read @ROADMAP.md and @CLAUDE.md.
What's the current task and status?
```

### If You Lost Work
```
claude --resume
```
Select the session from the list.

### If MCP Tools Aren't Working
```
Test the GSC connection:
mcp__gscServer__list_properties

If that fails, check your MCP server configuration.
```
