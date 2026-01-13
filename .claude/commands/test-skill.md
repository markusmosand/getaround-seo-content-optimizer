Test the SEO Content Optimizer skill to verify it's working correctly.

## Test Procedure

### Step 1: Load the Skill
Read `SKILL.md` completely.

### Step 2: Verify Reference Loading
Check that you can access all reference files by reading the first 10 lines of each:
- `references/shared/seo_aeo_best_practices.md`
- `references/shared/owner_content_principles.md`
- `references/shared/product_glossary.json`
- `references/shared/country_config.json`
- `references/norway/market_context_no.md`
- `references/france/market_context_fr.md`

### Step 3: Simulate Analysis
Using this sample article metadata, walk through Steps 0-4 of the skill workflow:

**Sample Article:**
- Title: "Topp 10 ting å gjøre i Bergen med barn"
- URL: /no/blog/topp-10-ting-a-gjore-i-bergen-med-barn
- Market: Norway
- Audience: Renter (consumer)
- Word count: 1,400
- Has FAQ: No
- Has practical info: Partial

### Step 4: Report Results

Provide a test report:

```
## Skill Test Report - [DATE]

### Context Loading
- [ ] SKILL.md loaded successfully
- [ ] Norway references accessible
- [ ] France references accessible
- [ ] Shared references accessible

### Workflow Execution
- [ ] Step 0 (Market Detection): [PASS/FAIL]
- [ ] Step 1 (Audience ID): [PASS/FAIL]
- [ ] Step 2 (Business Fit): [PASS/FAIL]
- [ ] Step 3 (6D Analysis): [PASS/FAIL]
- [ ] Step 4 (Prioritization): [PASS/FAIL]

### Issues Found
[List any problems encountered]

### Recommendations
[Suggestions for improvement]
```

If all tests pass, confirm: "Skill is functioning correctly."
If tests fail, explain what went wrong and suggest fixes.
