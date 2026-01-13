# Skill Enhancements: Gap Analysis & Recommendations

## Status

| Status | Details |
|--------|---------|
| **Analysis Date** | 2026-01-07 |
| **Version** | 1.0 |
| **Existing Skills Reviewed** | 16 |
| **Gaps Identified** | 7 major, 5 minor |
| **Priority Updates** | 4 |

---

## Executive Summary

The existing Claude Code skills provide strong foundations for SEO analysis and content optimization. However, several gaps exist when mapping against the 5-workflow automation system requirements:

**Critical Gaps:**
1. France market coverage is minimal (skills are Norway-centric)
2. No schema markup generation capability
3. No content brief automation
4. No automated internal linking suggestions

**Recommended Actions:**
1. Update 3 existing skills with France/dual-market support
2. Create 2 new skills (schema generator, content brief)
3. Add prompt libraries for n8n AI nodes
4. Document review automation patterns

---

## Existing Skills Inventory

### Getaround-Specific Skills

| Skill | Purpose | Market Coverage | Workflow Fit |
|-------|---------|-----------------|--------------|
| `getaround-seo-content-optimizer` | Article creation/optimization | Norway only | WF3: Writing |
| `getaround-seo-aeo-analyst` | GSC/performance analysis | Norway focused | WF1: Research, WF5: Monitoring |
| `getaround-translator` | Multi-language translation | NO/EN/FR | WF3: Writing |
| `gsc-analysis` | Comprehensive GSC analysis | Multi-language | WF1: Research, WF5: Monitoring |
| `seo-content-analyzer` | Content SEO scoring | Generic | WF4: Review |

### n8n Skills

| Skill | Purpose | Workflow Fit |
|-------|---------|--------------|
| `n8n-workflow-patterns` | Architectural patterns | All workflows |
| `n8n-code-javascript` | Code node JS helpers | WF1-5 |
| `n8n-code-python` | Code node Python helpers | WF1-5 |
| `n8n-expression-syntax` | Expression validation | WF1-5 |
| `n8n-mcp-tools-expert` | MCP tool usage | All |
| `n8n-node-configuration` | Node configuration | All |
| `n8n-validation-expert` | Workflow validation | All |

### Other Skills

| Skill | Purpose | Relevance |
|-------|---------|-----------|
| `getaround-bokforing` | Accounting (Fiken) | Not relevant |
| `breakdown-assistance-v2` | Task breakdown | General utility |
| `shadcn-ui-design` | UI design | Not relevant |

---

## Gap Analysis

### GAP 1: France Market Coverage (CRITICAL)

**Current State:**
- `getaround-seo-content-optimizer` references only Norway
- `getaround-seo-aeo-analyst` benchmarks are Norway-specific
- No France-specific content patterns documented

**Impact on Workflows:**
- WF2 (Planning): Cannot generate France-appropriate topics
- WF3 (Writing): Cannot create B2B/professional content for France
- WF4 (Review): No France-specific quality criteria

**Validated Differences (from Phase 0):**

| Aspect | Norway | France |
|--------|--------|--------|
| Audience | B2C (70%) | B2B (45%) |
| Tone | Casual "du" | Formal "vous" |
| Format | Listicles | Professional guides |
| Focus | Activities, road trips | ZFE, regulations, fleet |
| Year-stamping | Optional | Mandatory |

**Required Updates:**

```markdown
# In getaround-seo-content-optimizer

## Market Detection
Before analyzing, detect market from:
1. URL path (/blogg/ = Norway, /blog/ = France)
2. Language in content
3. User specification

## France-Specific Guidelines
- B2B/Professional focus (45% of traffic)
- Year-stamp all regulatory content
- Calculator/guide format preference
- Formal "vous" tone
- ZFE, TVS, fleet management topics

## Norway-Specific Guidelines (existing)
- B2C/Consumer focus (70%)
- Listicle format preference
- Casual "du" tone
- Activities, road trips, outdoor
```

**Effort:** Medium (update existing skill)

---

### GAP 2: Schema Markup Generation (CRITICAL)

**Current State:**
- No skill generates structured data
- `seo-content-analyzer` mentions schema but doesn't generate it
- Manual schema creation required

**Impact on Workflows:**
- WF3 (Writing): Cannot auto-generate FAQPage schema
- WF4 (Review): Cannot validate schema

**Required Capability:**

```javascript
// Schema types needed for workflow
const schemaTypes = {
  FAQPage: "All articles with FAQ section",
  Article: "All blog content",
  HowTo: "Step-by-step guides",
  BreadcrumbList: "All pages"
};

// Auto-extract FAQ from content
function generateFAQSchema(content) {
  // Parse H2/H3 questions
  // Extract following paragraph as answer
  // Generate JSON-LD
}
```

**Recommended Solution:**
Create new skill `schema-markup-generator` or add to `seo-content-analyzer`:

```markdown
# Schema Generation Capability

## Triggers
- "Generate schema for this article"
- "Add FAQPage markup"
- "Create structured data"

## Auto-Detection Rules
- FAQ section present → FAQPage schema
- Numbered steps → HowTo schema
- All blog content → Article schema

## Output Format
JSON-LD ready for insertion in <script> tag
```

**Effort:** Medium (new capability)

---

### GAP 3: Content Brief Generation (HIGH)

**Current State:**
- No standardized brief format
- Manual brief creation in Planning workflow
- No skill automates topic → brief conversion

**Impact on Workflows:**
- WF2 (Planning): Manual brief creation (15+ min per topic)
- WF3 (Writing): Inconsistent brief quality

**Required Capability:**

```markdown
# Content Brief Generator

## Input
- Topic/keyword from research
- Market (France/Norway)
- Content type (new/optimization)

## Output
Standardized brief with:
- Primary keyword + volume estimate
- Search intent classification
- Competitor analysis summary
- Recommended format
- Target word count
- Required sections
- Internal link targets
- Schema requirements
- Business fit validation
```

**France Brief Template:**
```markdown
## Content Brief: [Topic]
Market: France
Type: [Guide/Calculator/Explainer]
Audience: [B2B Professional/Fleet Manager/Business Owner]

### Keyword Strategy
- Primary: [keyword] ([volume] searches/mo)
- Secondary: [2-3 keywords]
- Intent: [Informational/Commercial]

### Content Requirements
- Format: Professional guide with sections
- Tone: Formal "vous", expert voice
- Word count: 1,800-2,500
- Year-stamp: Required (2026)

### Required Sections
1. [Section with regulatory context]
2. [Calculation/comparison section]
3. [Practical application]
4. FAQ (3-5 questions)
5. CTA to Getaround solution

### Schema
- Article
- FAQPage
- [HowTo if step-based]
```

**Norway Brief Template:**
```markdown
## Content Brief: [Topic]
Market: Norway
Type: [Listicle/Guide/Itinerary]
Audience: [Renter/Family/Tourist]

### Keyword Strategy
- Primary: [keyword] ([volume] searches/mo)
- Secondary: [2-3 keywords]
- Intent: [Informational/Inspirational]

### Content Requirements
- Format: Listicle or itinerary
- Tone: Casual "du", inspiring
- Word count: 1,200-2,000
- Seasonal angle: [if applicable]

### Required Sections
1. Hook with highlights
2. Listicle items (5-15)
3. Practical tips section
4. FAQ (3-5 questions)
5. CTA to rent a car

### Schema
- Article
- FAQPage
```

**Effort:** Medium (new skill or major update)

---

### GAP 4: Automated Internal Linking (HIGH)

**Current State:**
- Internal linking is manual
- No content inventory for suggestions
- `seo-content-analyzer` recommends links but cannot suggest specific URLs

**Impact on Workflows:**
- WF3 (Writing): Manual link research (10+ min per article)
- WF4 (Review): Cannot validate link coverage

**Required Capability:**

```markdown
# Internal Link Suggester

## Input
- Article content/topic
- Market (France/Norway)

## Process
1. Extract main topics/entities from content
2. Query content inventory (Google Sheets)
3. Match related articles by topic overlap
4. Return 5-8 link suggestions with:
   - Target URL
   - Anchor text suggestion
   - Relevance score
   - Context (where to place)

## Content Inventory Structure
| URL | Title | Primary Keyword | Topics | Market | Last Updated |
```

**Note:** This requires maintaining a content inventory, which WF5 (Monitoring) should populate.

**Effort:** High (requires content inventory + matching logic)

---

### GAP 5: Review Automation Standards (MEDIUM)

**Current State:**
- `seo-content-analyzer` provides scoring but is generic
- No Getaround-specific quality criteria
- E-E-A-T assessment is manual

**Impact on Workflows:**
- WF4 (Review): Inconsistent quality evaluation
- Human review time not reduced

**Required Updates to `seo-content-analyzer`:**

```markdown
# Getaround-Specific Review Criteria

## Business Fit Check (Critical)
- [ ] Rental intent present
- [ ] Getaround product mentioned naturally
- [ ] CTA leads to conversion action
- Score: Pass/Fail

## Market Alignment Check
France:
- [ ] Formal tone verified
- [ ] Year-stamp present (if regulatory)
- [ ] B2B angle if professional content

Norway:
- [ ] Casual tone verified
- [ ] Activity/experience focus
- [ ] Local relevance (Oslo priority)

## E-E-A-T Signals (Automated Detection)
- [ ] First-hand experience language
- [ ] Specific data/statistics cited
- [ ] Expert quotes (if present)
- [ ] Last updated date
- Score: 0-100

## AEO Readiness
- [ ] FAQ section present (3-5 questions)
- [ ] Direct answer in first paragraph
- [ ] Question-format headers
- [ ] Schema markup ready
- Score: 0-100
```

**Effort:** Medium (update existing skill)

---

### GAP 6: AI Prompt Library (MEDIUM)

**Current State:**
- No standardized prompts for n8n AI nodes
- Market-specific prompting not documented
- Each workflow would need custom prompts

**Impact on Workflows:**
- WF2 (Planning): No topic generation prompts
- WF3 (Writing): No content generation prompts
- Inconsistent AI output quality

**Required Capability:**

Create prompt library file for n8n workflows:

```markdown
# AI Prompt Library for Getaround SEO Workflows

## Topic Generation Prompts

### France B2B Topic Prompt
You are a SEO strategist for Getaround France's professional blog.
Generate 5 content topic suggestions based on this GSC data:
{research_data}

Requirements:
- Focus on B2B/fleet management/professional use cases
- Include regulatory topics (ZFE, TVS) if opportunity exists
- Target transactional or commercial search intent
- Each topic must have clear rental relevance

Output format:
1. Topic title
2. Primary keyword
3. Search intent
4. Business fit rationale
5. Recommended format (guide/calculator/comparison)

### Norway B2C Topic Prompt
You are a SEO strategist for Getaround Norway's lifestyle blog.
Generate 5 content topic suggestions based on this GSC data:
{research_data}

Requirements:
- Focus on activities, road trips, experiences
- Target families, tourists, adventure seekers
- Seasonal relevance if applicable
- Each topic must naturally involve renting a car

Output format:
[Same as France]

## Content Generation Prompts

### France Article System Prompt
You are writing for Getaround France's professional blog.
Tone: Professional, expert, formal "vous"
Audience: Fleet managers, business owners, professionals
Goal: Establish authority and drive B2B inquiries

### Norway Article System Prompt
You are writing for Getaround Norway's lifestyle blog.
Tone: Friendly, inspiring, casual "du"
Audience: Families, tourists, adventure seekers
Goal: Inspire and convert to car rentals
```

**Effort:** Low-Medium (documentation task)

---

### GAP 7: Cross-Market Reporting (LOW)

**Current State:**
- Analysis skills work per-market
- No automated comparison capability
- Manual synthesis required

**Impact on Workflows:**
- WF1 (Research): Cannot auto-compare markets
- WF5 (Monitoring): No cross-market insights

**Required Capability:**

Add to `gsc-analysis` or `getaround-seo-aeo-analyst`:

```markdown
## Cross-Market Comparison Mode

When analyzing both markets:
1. Extract same metrics for both
2. Normalize for market size differences
3. Identify:
   - Universal patterns (apply everywhere)
   - Market-specific patterns (keep separate)
   - Opportunities to replicate success
```

**Effort:** Low (enhancement to existing)

---

## Minor Gaps

### MINOR-1: n8n GSC Integration Pattern

**Issue:** `n8n-workflow-patterns` doesn't include GSC API pattern
**Solution:** Add HTTP Request pattern for GSC SearchAnalytics API
**Effort:** Low

### MINOR-2: Slack Approval Workflow Pattern

**Issue:** No approval workflow pattern documented
**Solution:** Add to `n8n-workflow-patterns` with Slack buttons
**Effort:** Low

### MINOR-3: Google Sheets as Database Pattern

**Issue:** Sheets as data store not fully documented
**Solution:** Add to `n8n-workflow-patterns`
**Effort:** Low

### MINOR-4: Error Notification Pattern

**Issue:** Error handling → Slack alert not standardized
**Solution:** Add error workflow template
**Effort:** Low

### MINOR-5: Rate Limiting Handling

**Issue:** GSC API rate limits not documented
**Solution:** Add retry/backoff pattern to HTTP patterns
**Effort:** Low

---

## Prioritized Action Plan

### Phase 1: Critical Updates (Before WF Implementation)

| Action | Skill | Effort | Impact | Priority |
|--------|-------|--------|--------|----------|
| Add France market support | `getaround-seo-content-optimizer` | Medium | Critical | 1 |
| Add France benchmarks | `getaround-seo-aeo-analyst` | Low | High | 2 |
| Create AI prompt library | New file | Low | High | 3 |

### Phase 2: Workflow Enablers (During WF Implementation)

| Action | Skill | Effort | Impact | Priority |
|--------|-------|--------|--------|----------|
| Add schema generation | `seo-content-analyzer` | Medium | High | 4 |
| Create brief templates | New or update | Medium | High | 5 |
| Add Getaround review criteria | `seo-content-analyzer` | Medium | Medium | 6 |

### Phase 3: Optimization (After WF Launch)

| Action | Skill | Effort | Impact | Priority |
|--------|-------|--------|--------|----------|
| Build content inventory system | New | High | High | 7 |
| Add internal link suggestions | New capability | High | Medium | 8 |
| Add cross-market comparison | `gsc-analysis` | Low | Low | 9 |
| Add n8n GSC pattern | `n8n-workflow-patterns` | Low | Low | 10 |

---

## Implementation Approach

### Option A: Update Existing Skills (Recommended)

**Pros:**
- Faster implementation
- Maintains consistency
- Less maintenance overhead

**Cons:**
- Skills may become too large
- Context loading heavier

**Implementation:**
1. Update `getaround-seo-content-optimizer` with France section
2. Update `getaround-seo-aeo-analyst` with France benchmarks
3. Update `seo-content-analyzer` with schema + Getaround criteria
4. Create `prompts/` directory with n8n prompt files

### Option B: Create Specialized Skills

**Pros:**
- Focused, lean skills
- Market-specific loading

**Cons:**
- More skills to maintain
- Potential duplication

**Implementation:**
1. Create `getaround-seo-france` skill
2. Create `schema-markup-generator` skill
3. Create `content-brief-generator` skill

### Recommendation: Hybrid Approach

1. **Update existing skills** for market support (Option A)
2. **Create new prompt library** as separate files (not skills)
3. **Defer internal linking** until content inventory exists
4. **Add schema generation** to existing seo-content-analyzer

---

## Skill Update Specifications

### Update 1: getaround-seo-content-optimizer

**File:** `/Users/mark/.claude/skills/getaround-seo-content-optimizer/SKILL.md`

**Changes:**
1. Add market detection logic (URL-based)
2. Add France content guidelines section
3. Update workflow to include market branching
4. Add France-specific format patterns
5. Update references with France context

**New References Needed:**
- `references/france_market_context.md`
- `references/france_content_patterns.md`

### Update 2: getaround-seo-aeo-analyst

**File:** `/Users/mark/.claude/skills/getaround-seo-aeo-analyst/SKILL.md`

**Changes:**
1. Add France market context to `references/market_context.md`
2. Add France benchmarks to `references/benchmarks.md`
3. Update analysis workflows for dual-market
4. Add France-specific competitor context

### Update 3: seo-content-analyzer

**File:** `/Users/mark/.claude/skills/seo-content-analyzer/SKILL.md`

**Changes:**
1. Add schema markup generation capability
2. Add Getaround-specific review criteria
3. Add E-E-A-T signal detection
4. Add business fit validation

**New References Needed:**
- `references/schema-templates.md`
- `references/getaround-criteria.md`

---

## New Files Required

### 1. AI Prompt Library

**Location:** `/Users/mark/getaround-seo-automation/prompts/`

**Files:**
- `topic_generation_france.md`
- `topic_generation_norway.md`
- `content_generation_france.md`
- `content_generation_norway.md`
- `review_prompts.md`

### 2. Content Brief Templates

**Location:** `/Users/mark/getaround-seo-automation/templates/`

**Files:**
- `brief_france_b2b.md`
- `brief_france_b2c.md`
- `brief_norway_b2c.md`
- `brief_optimization.md`

### 3. Schema Templates

**Location:** Within `seo-content-analyzer/references/`

**Files:**
- `schema-templates.md` (FAQPage, Article, HowTo, BreadcrumbList)

---

## Success Metrics

After implementing skill enhancements:

| Metric | Before | Target | Measurement |
|--------|--------|--------|-------------|
| France content support | 0% | 100% | Skills detect and handle France |
| Schema auto-generation | 0% | 100% | All articles get schema |
| Brief creation time | 15 min | 2 min | Time per brief |
| Review automation | 50% | 80% | Checks automated |
| Cross-market analysis | Manual | Automated | Single command |

---

## Dependencies

### For Skill Updates
- Access to skill files in `/Users/mark/.claude/skills/`
- France market data (completed in Phase 0)
- Schema markup examples

### For Prompt Library
- None (can create immediately)

### For Content Inventory (deferred)
- Google Sheets structure
- Published URL list
- Topic/keyword mapping

---

## Timeline Recommendation

| Week | Action |
|------|--------|
| 1 | Create prompt library + brief templates |
| 1-2 | Update `getaround-seo-content-optimizer` with France |
| 2 | Update `getaround-seo-aeo-analyst` with France |
| 2-3 | Add schema generation to `seo-content-analyzer` |
| 3+ | Build during workflow implementation |

---

*Skill Enhancements Version: 1.0*
*Last Updated: 2026-01-07*
*Ready for: Implementation during Phase 5*
