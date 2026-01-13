---
name: getaround-seo-content-optimizer
description: "Analyze and optimize blog content for Getaround's car-sharing platform, with comprehensive SEO and AEO (Answer Engine Optimization) for both traditional search engines and AI overviews. Use when asked to: (1) Analyze or audit existing blog articles for SEO performance, (2) Optimize or improve blog content, (3) Rewrite articles for better ranking, (4) Create SEO/AEO-optimized content for Getaround, (5) Fix low-performing articles, (6) Validate business fit and conversion potential of content ideas. Triggers include: optimize this article, improve SEO, analyze blog performance, rewrite for better ranking, is this article worth writing, validate business fit, make this AI-overview ready."
---

# Getaround SEO Content Optimizer

Analyze existing blog articles and create optimized content for Getaround's car-sharing platform in Norway, with dual focus on traditional SEO and AEO (Answer Engine Optimization) for AI overviews.

## Core Capabilities

1. **Multi-dimensional SEO/AEO analysis** - Evaluate articles across 6 dimensions: keyword/intent, structure, content quality, engagement, AEO-readiness, product-fit
2. **Business fit validation** - Distinguish qualified traffic from vanity traffic using conversion potential assessment
3. **Format-driven optimization** - Apply proven patterns from Getaround data (listicles for activities, how-to for owners)
4. **Comprehensive rewrites** - Create fully optimized content ready for Ghost CMS publication
5. **Dual-audience calibration** - Differentiate tone and approach for renters vs. owners

## Workflow

### Step 1: Context Loading & Audience Identification

**Before analyzing any article, load context:**

Read all three reference documents to understand:
- `getaround_master_context.md` - Getaround products, USPs, competitors, search behavior, tone of voice
- `blog_performance_insights.md` - What content types perform well/poorly, engagement benchmarks, proven formats
- `seo_aeo_best_practices.md` - Technical SEO requirements, AEO optimization, Getaround-specific integration guidelines

**Identify target audience:**
- Renter content: Friendly, inspiring, practical (activities, travel, use-cases)
- Owner content: Professional, data-driven, concrete (income, optimization, how-to)

This differentiation is CRITICAL - tone, data usage, and CTA strength vary dramatically.

### Step 2: Business Fit Validation (CRITICAL)

**Before proceeding with optimization, validate business fit to avoid "vanity traffic":**

Ask three validation questions:

1. **Search Intent Alignment** - Do people search this BECAUSE they need to rent a car?
   - ✅ Good: "aktiviteter i Oslo" (planning trip → needs car)
   - ✅ Good: "leie ut bil" (considering becoming owner)
   - ❌ Bad: "skifte til vinterdekk" (maintenance on own car, not rental)
   - ❌ Bad: "sikring av barn i bil" (general child safety, not rental-specific)

2. **Conversion Potential** - Can this drive bookings or owner registrations?
   - ✅ High: Specific use-case (wedding car, moving van, long-term rental)
   - ✅ Medium: Activities/travel inspiration (indirect booking driver)
   - ✅ High: Owner guides with income data (direct owner recruitment)
   - ❌ Low: Generic information applicable to any car

3. **Product-Content Fit** - Does content naturally link to Getaround products?
   - ✅ Good: Content mentions Connect, delivery, long-term rental, specific car types
   - ❌ Bad: Content about general car ownership, maintenance, or driving tips

**If business fit is WEAK:**
- Flag concern to user immediately
- Explain why this is "vanity traffic" (high impressions but zero business value)
- Suggest either: (a) pivot angle to Getaround relevance, or (b) skip optimization
- Example: "Skifte til vinterdekk" → pivot to "Leie bil med vinterdekk - hva du må vite"

**Only proceed with full analysis/optimization if business fit is VALIDATED.**

### Step 3: Six-Dimensional Analysis

Analyze article across six dimensions (reference `seo_aeo_best_practices.md` for detailed criteria):

**A) Keyword & Search Intent Alignment**
- Identify primary and secondary keywords
- Assess if content matches search intent (informational/transactional/navigational/commercial)
- Check keyword placement (H1, intro, headers, conclusion, meta)
- Evaluate keyword density and natural usage

**B) Structure & Readability**
- Audit header hierarchy (H1 → H2 → H3 logic)
- Assess paragraph length (mobile-friendly: 2-4 sentences)
- Check scannability (headers + bold text should tell story)
- Identify internal linking opportunities

**C) Content Quality & Depth**
- Evaluate comprehensiveness for target keyword
- Identify content gaps vs. competitors
- Check if Getaround USPs are integrated naturally
- Verify practical information (prices, parking, tips)

**D) Engagement Signals**
- Assess hook strength (first paragraph)
- Check CTA clarity and placement
- Evaluate if content provides value to target audience
- Compare against benchmarks from `blog_performance_insights.md`:
  - Activities (renter): 65-80% engagement, 25-40 sec
  - Owner guides: 75-90% engagement, 45-85 sec
  - Use-cases: 80-90% engagement, 15-25 sec

**E) AEO/AI-Overview Readiness**
- Check for FAQ section (3-7 questions)
- Assess Q&A structure (headers as questions)
- Identify E-E-A-T signals (expertise, experience, authority, trust)
- Look for unique data points or expert quotes
- Evaluate semantic richness and freshness signals

**F) Getaround Product-Content Fit**
- Verify natural integration of Getaround products (Connect, long-term, B2B)
- Assess conversion opportunities
- Check geographic relevance (Oslo > Tromsø > Bergen priority)
- Validate format matches proven patterns from data insights

### Step 4: Issue Identification & Prioritization

Based on analysis, categorize issues into three priority levels:

**CRITICAL (Red Flag)** - Issues actively harming performance:
- Content-product mismatch (vanity traffic)
- Missing or wrong primary keyword
- Severely broken structure (no headers, walls of text)
- No CTA or conversion path
- Completely wrong tone for audience

**HIGH-IMPACT (Orange)** - Issues preventing article from reaching potential:
- Weak title tag or meta description (CTR gap)
- Position collapse (good content, bad ranking) - likely missing backlinks or internal links
- Missing FAQ section (AEO opportunity)
- No unique data points (weak E-E-A-T)
- Moderate structure problems (header hierarchy issues)

**OPTIMIZATION (Green)** - Fine-tuning for marginal gains:
- Secondary keyword integration
- Sentence/paragraph length optimization
- Additional internal links
- Image alt text improvements
- Semantic richness enhancements

For each issue, provide:
- Specific description of problem
- Estimated impact (high/medium/low)
- Concrete fix recommendation

### Step 5: Optimization Proposal

Create structured proposal with seven components:

**A) Structural Changes**
- Header reorg (before/after visualization)
- Format shift (e.g., narrative → listicle)
- Section additions/removals
- FAQ placement

**B) Content Additions**
- New sections to add
- Specific data points needed
- Expert quotes to include
- Internal linking targets (link FROM this article to 3-5 related articles)

**C) Content Removals**
- Irrelevant sections to delete
- Redundant paragraphs
- Off-topic tangents

**D) SEO Technical**
- New title tag (50-60 chars with keyword)
- New meta description (150-160 chars with CTA)
- URL slug optimization
- Internal link strategy

**E) AEO Header Optimization** (Reference: `aeo_header_patterns.md`)
- Convert headers to question format where appropriate
- Add 40-60 word answer blocks after question headers
- Structure for featured snippet optimization (paragraph/list/table)
- Implement semantic chunking (one question per section)

**F) CTA Strategy** (Reference: `cta_framework.md`)
- Select CTA strength based on content type and intent
- Choose appropriate CTA trigger (value/urgency/exclusivity/clarity)
- Determine placement (end only vs middle + end)
- Draft specific CTA copy using power words and templates

**G) Schema Markup** (Reference: `schema_templates.md`)
- Determine required schema types (Article always, FAQPage if 3+ Q&As, HowTo if step-by-step)
- Generate JSON-LD markup
- Validate against checklist

### Step 6: Execution (If Requested)

If user requests full rewrite, produce:

**Complete optimized article in Markdown format, ready for Ghost CMS:**

Include:
1. **Engaging hook** (first paragraph) - sensory, immersive, draw reader in
2. **Clear promise** - what user will learn/get from article
3. **AEO-optimized headers** - use question format for 50%+ of H2s (reference `aeo_header_patterns.md`)
4. **Answer-first paragraphs** - 40-60 word direct answer after each question header
5. **Structured body** with proper header hierarchy
6. **Natural USP integration** (reference 7 USPs in `getaround_master_context.md`)
7. **Practical information** (prices, parking, tips, season)
8. **FAQ section** (3-7 questions with 40-60 word answers each)
9. **Strategic CTA** - selected using `cta_framework.md` (type, trigger, placement, copy)
10. **Complete metadata footer** - using template from `seo_aeo_best_practices.md` Part 8

**Tone calibration:**
- Renter content: Warm, inspiring, evoke feelings. Paint pictures with sensory language.
- Owner content: Professional, data-driven, concrete. Focus on ROI, optimization, numbers.

**Format selection based on proven patterns:**
- Activities → Listicle (Topp 5-10) with 150-200 words per item
- Owner guides → How-to with comprehensive depth (1,800-2,500 words)
- Use-cases → Problem-solution (800-1,200 words)
- City guides → Comprehensive listicle (20-30 items, 2,000-3,000 words)

Reference `blog_performance_insights.md` for format-specific best practices.

### Step 7: Metadata Footer Generation

**REQUIRED for all optimized content.** Generate the complete metadata footer using the template in `seo_aeo_best_practices.md` Part 8.

The metadata footer must include:

**Core SEO Section:**
- Title tag (50-60 chars)
- Meta description (150-160 chars with CTA)
- Slug
- Primary and secondary keywords

**Content Structure Section:**
- H1, H2 count
- Question headers listed
- Answer-first section count
- Word count, FAQ question count

**CTA Details Section:**
- Exact CTA text
- CTA type (soft/medium/strong)
- CTA trigger (value/urgency/exclusivity/clarity)
- Placement and target URL

**AEO Readiness Section:**
- FAQ section presence
- Featured snippet optimization status
- AI Overview readiness
- Schema types to implement

**Business & Tracking Section:**
- Content type, target audience, market
- Business fit score (1-5)
- Predicted engagement
- Internal linking opportunities

**JSON-LD Schema Section:**
- Complete, validated schema markup
- Article schema (always)
- FAQPage schema (if 3+ Q&As)
- HowTo schema (if step-by-step guide)

## Using Bundled References

### getaround_master_context.md
**Read FIRST** (always) - Contains:
- Getaround products and delivery methods
- Competitors and market positioning
- USPs (7 key USPs to integrate)
- Search behavior (renter vs. owner queries)
- Tone of voice guidelines (renter vs. owner differentiation)
- Key terminology

**Use for:**
- Understanding Getaround's offerings
- Calibrating tone for audience
- Identifying USPs to weave naturally
- Validating product-content fit

### blog_performance_insights.md
**Read FIRST** (always) - Contains:
- What content types perform well (listicles, owner guides)
- What fails (case studies without data, content-product mismatch)
- Engagement benchmarks by content type
- Geographic priorities (Oslo >> Tromsø > Bergen)
- Proven format patterns
- Business fit validation framework

**Use for:**
- Selecting optimal format (listicle vs. guide vs. use-case)
- Setting engagement targets
- Validating business fit
- Understanding what Getaround data shows works/doesn't work

### seo_aeo_best_practices.md
**Read AS NEEDED** (reference during optimization) - Contains:
- Traditional SEO fundamentals (keywords, titles, meta, internal linking)
- AEO optimization (FAQ schema, Q&A structure, E-E-A-T, unique data)
- Getaround-specific integration (USP weaving, CTA guidelines, tone calibration)
- Markdown formatting for Ghost CMS
- Quality checklists (SEO, AEO, content, format, Getaround-specific)
- Common mistakes to avoid
- **NEW: Part 7** - Cross-references to advanced guides
- **NEW: Part 8** - Metadata footer template

**Use for:**
- Technical SEO requirements during optimization
- AEO enhancement guidelines
- Output formatting standards
- Quality validation
- **Metadata footer generation** (Part 8 - required for all content)

**Structure:** This reference is comprehensive (8 parts). Use search/grep to find specific sections:
- Part 1: Traditional SEO
- Part 2: AEO
- Part 3: Getaround Integration
- Part 4: Markdown Formatting
- Part 5: Quality Checklist
- Part 6: Common Mistakes
- Part 7: Advanced Reference Guides (cross-links)
- Part 8: Metadata Footer Template

### cta_framework.md (NEW)
**Read when selecting/writing CTAs** - Contains:
- CTA psychology principles (clarity, urgency, value, exclusivity)
- CTA strength matrix by content type and intent
- Power words for car-sharing (Norwegian + French)
- CTA templates library with examples
- Placement rules and strategic patterns
- CTA testing checklist and quality scoring

**Use for:**
- Selecting appropriate CTA strength (soft/medium/strong)
- Choosing CTA trigger (value/urgency/exclusivity/clarity)
- Writing CTA copy with power words
- Determining CTA placement
- Adapting CTAs for NO vs FR markets

### aeo_header_patterns.md (NEW)
**Read when structuring headers** - Contains:
- Question-format header templates
- Answer-first paragraph structure (40-60 word format)
- Header formulas by content type
- Featured snippet optimization (paragraph/list/table)
- Semantic chunking guidelines
- Before/after transformation examples

**Use for:**
- Converting headers to question format
- Writing 40-60 word answer blocks
- Optimizing for featured snippets
- Structuring content for AI Overview citation
- Applying the right header formula for content type

### schema_templates.md (NEW)
**Read when generating schema markup** - Contains:
- Article/BlogPosting JSON-LD template (required for all)
- FAQPage JSON-LD template (for 3+ Q&A sections)
- HowTo JSON-LD template (for step-by-step guides)
- Combined schema examples
- Validation checklist
- Ghost CMS integration instructions

**Use for:**
- Generating JSON-LD schema markup
- Combining multiple schema types
- Validating schema before publication
- Adding schema to Ghost CMS

## Output Requirements

### For Analysis Reports

Provide:
1. **Executive Summary** (3-5 bullets)
   - Biggest issues identified
   - Biggest opportunities
   - Business fit assessment

2. **Six-Dimensional Analysis** (concise)
   - One paragraph per dimension
   - Key findings only, not exhaustive

3. **Prioritized Issue List**
   - Critical issues (address immediately)
   - High-impact issues (address soon)
   - Optimization opportunities (nice-to-have)

4. **Quick Wins** (top 3-5)
   - High impact, low effort fixes
   - Specific, actionable

### For Optimized Content

Provide:
1. **Full article in Markdown** (ready to paste into Ghost CMS)
2. **Inline comments** explaining key SEO/AEO decisions (use HTML comments: `<!-- Comment -->`)
3. **SEO metadata section** at end
4. **Before/after comparison** (brief) highlighting key improvements

**Format checklist:**
- Valid Markdown syntax
- Proper header hierarchy (# → ## → ###)
- Paragraphs 2-4 sentences
- FAQ section included
- SEO metadata at end
- No lorem ipsum or placeholders

## Quality Standards

**Every optimization must achieve:**

✅ **Business fit validated** - Not vanity traffic  
✅ **Search intent matched** - Content answers what user searched for  
✅ **Keywords properly placed** - H1, intro, headers, conclusion, meta  
✅ **Structure optimized** - Scannable, mobile-friendly, proper hierarchy  
✅ **AEO-ready** - FAQ section, Q&A structure, E-E-A-T signals  
✅ **Getaround-integrated** - USPs woven naturally, not pushy  
✅ **Tone calibrated** - Matches audience (renter vs. owner)  
✅ **Format proven** - Uses patterns from blog_performance_insights.md  
✅ **Actionable** - User can implement recommendations immediately  

**Balance principle:** Always optimize for BOTH search engines AND humans. Never sacrifice readability for SEO.

## Edge Cases & Special Considerations

**Case 1: High-traffic but low-engagement article**
- Likely content-product mismatch (e.g., "Skifte til vinterdekk")
- Assess if pivot possible (change angle to Getaround relevance)
- If no pivot: recommend pruning/redirecting

**Case 2: Low-traffic but high-engagement article**  
- Content is good, ranking is the issue
- Focus on: backlinks, internal links, on-page SEO
- Don't rewrite content, fix distribution/visibility

**Case 3: Seasonal content**
- Note timing in analysis (e.g., winter content analyzed in summer)
- Recommend publication timing (4-6 weeks before season peak)
- Consider annual update strategy

**Case 4: Geographic mismatch**
- Bergen/Stavanger/Trondheim: Good engagement, but low volume compared to Oslo
- Validate if worth optimizing based on market priority
- Consider clustering (one comprehensive "activities in Norway" with city sections)

**Case 5: Existing good performers**
- Focus on AEO enhancements (FAQ, unique data, E-E-A-T)
- Don't over-optimize (if it works, minor tweaks only)
- Protect rankings with freshness updates

## Critical Reminders

⚠️ **ALWAYS validate business fit BEFORE optimizing** - Avoid vanity traffic  
⚠️ **Load all three references at start** - Context is essential  
⚠️ **Differentiate renter vs. owner content** - Tone and approach vary dramatically  
⚠️ **Use proven formats from data** - Listicles work, case studies don't  
⚠️ **Balance SEO and AEO** - Optimize for both traditional search AND AI overviews  
⚠️ **Be actionable** - Every recommendation must be concrete and implementable  
⚠️ **Prioritize ruthlessly** - Don't overwhelm user with 50 issues  

**Success metric:** Optimized content should achieve 65-90% engagement rate (depending on type) and drive measurable conversions (bookings or owner registrations).
