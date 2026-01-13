# Task 500: Build WF1 Research Workflow

## Status: [x] Completed 2026-01-10

## n8n Cloud Deployment
- **Workflow ID:** `92m9ouhgzWQCpGVa`
- **URL:** https://markusmosand.app.n8n.cloud/workflow/92m9ouhgzWQCpGVa
- **Status:** Inactive (requires credential configuration)

## Objective
Build the first n8n workflow for weekly SEO research data collection.

## Output
`workflows/wf1-research-weekly-data-collection.json`

## Workflow Summary

### Name
SEO Research - Weekly Data Collection

### Schedule
Every Monday at 06:00 UTC

### Nodes (7 total)

| Node | Type | Purpose |
|------|------|---------|
| Weekly Research Trigger | scheduleTrigger | Runs every Monday at 6am |
| Get France Blog Data | httpRequest | GSC API call for `/blog/` pages |
| Get Norway Blog Data | httpRequest | GSC API call for `/blogg/` pages |
| Merge GSC Data | merge | Combines France + Norway data |
| Identify Opportunities | code | JS analysis for CTR gaps & position opportunities |
| Save Weekly Report | googleSheets | Appends results to tracking sheet |
| Send Weekly Report | slack | Posts summary to SEO channel |

### Data Flow
```
Trigger → [France GSC, Norway GSC] (parallel)
       → Merge → Code Analysis
       → [Sheets, Slack] (parallel)
```

### Opportunity Detection Logic

**CTR Gaps:**
- Impressions > 100
- CTR < 2%
- Recommendation: Optimize title/meta

**Position Opportunities:**
- Position 4-15
- Impressions > 50
- Recommendation: Content refresh

### Environment Variables Required

| Variable | Purpose |
|----------|---------|
| `GOOGLE_SHEETS_SEO_REPORT_ID` | Target spreadsheet for reports |
| `SLACK_SEO_CHANNEL_ID` | Channel for notifications |

### Credentials Required

| Credential | Type | Usage |
|------------|------|-------|
| Google OAuth 2.0 | oAuth2Api | GSC API access |
| Google Sheets | serviceAccount | Sheet write access |
| Slack OAuth 2.0 | slackOAuth2Api | Channel posting |

## Validation Results

- **Errors:** 0
- **Warnings:** 6 (non-blocking suggestions)
- **Valid:** Yes

### Warnings (Informational)
1. Code node error handling (acceptable - data validation built-in)
2. Sheets valueInputMode (acceptable - autoMap works)
3. Slack rate limits (acceptable - weekly frequency)
4. General error handling suggestion
5-6. HTTP retry defaults (3 attempts is fine)

## Next Steps
1. Import workflow JSON to n8n Cloud
2. Configure environment variables
3. Set up OAuth credentials
4. Test with manual trigger
5. Enable scheduled execution

## Dependencies
- Google Search Console API access
- Google Sheets API access
- Slack Bot with channel posting permissions
