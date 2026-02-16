---
name: getaround-seo-content-optimizer
description: "Analyze and optimize blog content for Getaround's car-sharing platform in Norway and France, with comprehensive SEO and AEO (Answer Engine Optimization) for both traditional search engines and AI overviews. Use when asked to: (1) Analyze or audit existing blog articles for SEO performance, (2) Optimize or improve blog content, (3) Rewrite articles for better ranking, (4) Create SEO/AEO-optimized content for Getaround, (5) Fix low-performing articles, (6) Validate business fit and conversion potential of content ideas. Triggers include: optimize this article, improve SEO, analyze blog performance, rewrite for better ranking, is this article worth writing, validate business fit, make this AI-overview ready."
---

# Getaround SEO Content Optimizer

Analyze existing blog articles and create optimized content for Getaround's car-sharing platform in Norway and France, with dual focus on traditional SEO and AEO (Answer Engine Optimization) for AI overviews.

## Core Capabilities

1. **Multi-dimensional SEO/AEO analysis** - Evaluate articles across 6 dimensions: keyword/intent, structure, content quality, engagement, AEO-readiness, product-fit
2. **Business fit validation** - Distinguish qualified traffic from vanity traffic using conversion potential assessment
3. **Format-driven optimization** - Apply proven patterns from Getaround data (listicles for activities, how-to for owners)
4. **Comprehensive rewrites** - Create fully optimized content ready for Ghost CMS publication
5. **Dual-audience calibration** - Differentiate tone and approach for renters vs. owners

## Workflow

### Step 0: Market Detection & Context Loading

**CRITICAL: Detect target market FIRST before any analysis.**

#### Market Detection Signals (check in order):

| Signal Type | Norway Indicators | France Indicators |
|-------------|-------------------|-------------------|
| URL pattern | `getaround.no` or `no.getaround.com` | `fr.getaround.com` or `getaround.com/fr/` |
| Article language | Norwegian text | French text |
| Geographic keywords | Oslo, Bergen, Tromsø, Stavanger, Trondheim | Paris, Lyon, Marseille, Bordeaux, Toulouse, Nice |
| User explicit mention | "optimize this Norwegian article" or "for Norway" | "optimize this French article" or "for France" |
| Currency/terminology | NOK/kr | EUR/€ |

#### Once market detected, load appropriate references:

**If NORWAY detected:**
- Read `references/norway/performance_data_no.md`
- Read `references/norway/market_context_no.md`
- Read `references/norway/tone_guide_no.md`
- Read `references/shared/seo_aeo_best_practices.md` (universal)
- **If owner/utleier content:** Also read:
  - `references/shared/owner_content_principles.md` (universal owner guidelines)
  - `references/norway/owner_content_guide_no.md` (NO-specific terminology, examples)

Apply Norwegian calibrations:
- **Tone:** Informal "du" form, warm and friendly
- **Content focus:** Consumer activities (70%), outdoor/nature, family content, activity listicles
- **Top formats:** Numbered listicles "Topp 5/10..." (activities, city guides)
- **Geographic priority:** Oslo >> Tromsø > Bergen > Stavanger
- **Audience split:** 70% consumer renters, 30% owners
- **Engagement benchmarks:** Activities 65-80%, Owner guides 75-90%
- **Typical length:** 1,200-1,800 words
- **Key USPs:** Activity access, Nordic experiences, local availability
- **Competitors:** Hyre (main), traditional rental (secondary)

**If FRANCE detected:**
- Read `references/france/performance_data_fr.md`
- Read `references/france/market_context_fr.md`
- Read `references/france/tone_guide_fr.md`
- Read `references/france/keyword_strategy_fr.md`
- Read `references/shared/seo_aeo_best_practices.md` (universal)
- **If owner/propriétaire content:** Also read:
  - `references/shared/owner_content_principles.md` (universal owner guidelines)
  - `references/france/owner_content_guide_fr.md` (FR-specific terminology, examples)

Apply French calibrations:
- **Tone:** Formal "vous" form with strategic warmth (L'Adventure Lab standard)
- **Content focus:** B2B/professional (60%), regulatory compliance, fiscal topics, professional vehicle guides
- **Top formats:** Professional guides "Guide complet...", regulatory explainers "Tout savoir sur... en [Year]", TCO calculators
- **Geographic priority:** Paris, Lyon, Marseille (major metros)
- **Audience split:** 60% B2B/professional, 40% consumer
- **Engagement benchmarks:** B2B guides 70-85%, Regulatory 65-80%
- **Typical length:** 1,800-2,500 words (longer, more comprehensive)
- **Critical elements:** Year-stamping mandatory ("2025"), regulatory citations, data tables
- **Key USPs:** ZFE compliance, professional solutions, cross-border travel, fiscal optimization
- **Competitors:** Turo (main), traditional rental (strong)
- **Unique opportunities:** Regulatory content (ZFE, TVS, Crit'Air), professional fleet optimization

**If market unclear:**
Ask user to clarify: "I see content that could be for Norway or France. Which market should I optimize for?"
Wait for confirmation before proceeding.

#### Context validation checkpoint:
Before proceeding to analysis, confirm you have:
- ✅ Identified correct market (Norway or France)
- ✅ Loaded market-specific references (3-4 files)
- ✅ Noted tone guidelines (du vs vous)
- ✅ Understood content focus (consumer vs B2B)
- ✅ Identified proven formats for this market
- ✅ Know geographic and audience priorities

### Step 1: Audience Identification (After Market Detection)

**Identify target audience within the detected market:**

**Renter content:** Inspiring, practical (activities, travel, use-cases)
- Norway: Warm, friendly "du" tone
- France: Professional "vous" but warmer for consumer content (L'Adventure Lab style)

**Owner content:** Professional, data-driven, concrete (income, optimization, how-to)
- Norway: Friendly but concrete
- France: Formal, analytical, fiscal focus

This differentiation is CRITICAL - tone, data usage, and CTA strength vary dramatically between markets AND audiences.

### Step 2: Business Fit Validation (CRITICAL)

**Before proceeding with optimization, validate business fit to avoid "vanity traffic":**

Ask three validation questions:

**1. Search Intent Alignment** - Do people search this BECAUSE they need to rent a car?
- ✅ Good (Norway): "aktiviteter i Oslo" (planning trip → needs car)
- ✅ Good (Norway): "leie ut bil" (considering becoming owner)
- ✅ Good (France): "déplacement professionnel" (business travel → vehicle need)
- ✅ Good (France): "ZFE Paris 2025" (compliance → must rent ZFE-eligible vehicle)
- ❌ Bad (Norway): "skifte til vinterdekk" (maintenance on own car, not rental)
- ❌ Bad (Both): "sikring av barn i bil" (general child safety, not rental-specific)

**2. Conversion Potential** - Can this drive bookings or owner registrations?
- ✅ High: Specific use-case (wedding car, moving van, long-term rental, professional vehicle)
- ✅ Medium: Activities/travel inspiration (indirect booking driver)
- ✅ High: Owner guides with income data (direct owner recruitment)
- ✅ High (France): Regulatory compliance content (ZFE, professional tax optimization)
- ❌ Low: Generic information applicable to any car

**3. Product-Content Fit** - Does content naturally link to Getaround products?
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
- Compare against benchmarks from market-specific `performance_data` file

**E) AEO/AI-Overview Readiness**
- Check for FAQ section (3-7 questions)
- Assess Q&A structure (headers as questions)
- Identify E-E-A-T signals (expertise, experience, authority, trust)
- Look for unique data points or expert quotes
- Evaluate semantic richness and freshness signals

**F) Getaround Product-Content Fit**
- Verify natural integration of Getaround products (Connect, long-term, B2B)
- Assess conversion opportunities
- Check geographic relevance (market-specific priorities)
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

Create structured proposal with five components:

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

**E) AEO Enhancements**
- FAQ schema implementation (content must be FAQ-formatted)
- Q&A structure conversion
- E-E-A-T signal additions
- Unique data point integration

**F) AEO Header Optimization** (reference `aeo_header_patterns.md`)
- Convert H2s to question format matching search queries
- Plan 40-60 word answer-first paragraphs after each question header
- Identify H2 injection opportunities for related high-volume queries
- Apply PAA/Featured Snippet alignment (title tag, slug, H1, first sentence match query)

**G) CTA Strategy** (reference `cta_framework.md`)
- Select CTA strength based on content type and intent:
  | Content Type | CTA Strength | Example |
  |--------------|--------------|---------|
  | Activity guides | Soft | "Utforsk flere tips" / "Découvrir plus" |
  | Use-case articles | Medium | "Se tilgjengelige biler" / "Voir les voitures" |
  | Owner guides | Strong | "Start å tjen i dag" / "Commencer à gagner" |
- Choose appropriate power words for market (NO/FR)
- Determine placement (end only for soft, middle+end for medium/strong)

**H) Schema Markup Planning** (reference `schema_templates.md`)
- Select schema types: Article (always) + FAQPage (if 3+ Q&A) + HowTo (if step-by-step)
- Plan FAQ questions for schema extraction
- Note HowTo steps if applicable

### Step 6: Execution (If Requested)

If user requests full rewrite, produce:

**Complete optimized article in Markdown format, ready for Ghost CMS:**

Include:
1. **Engaging hook** (first paragraph) - sensory, immersive, draw reader in
2. **Clear promise** - what user will learn/get from article
3. **Structured body** with proper header hierarchy
4. **Natural USP integration** (reference market-specific context file)
5. **Practical information** (prices, parking, tips, season)
6. **FAQ section** (3-7 questions with brief answers)
7. **Appropriate CTA** (strength matches content type)
8. **SEO metadata section** at end with title tag, meta description, slug, keywords, internal link suggestions

#### Tone calibration by market:

**Norway:**
- Renter content: Warm, inspiring, informal "du" tone. Paint pictures with sensory language. Evoke feelings of adventure and nature.
- Owner content: Friendly but concrete, informal "du" tone. Focus on practical income examples, optimization tips.

**France:**
- Renter content (B2B): Professional, authoritative, formal "vous" tone. Data-driven, clear benefits. Regulatory accuracy.
- Renter content (Consumer): Warmer but still formal "vous" (L'Adventure Lab style). Inspiring but practical. Professional credibility maintained.
- Owner content: Analytical, formal "vous" tone. Focus on ROI, fiscal implications, concrete numbers. Professional skepticism requires data.

**Critical French typography:**
- Space before: ! ? ; :
- Guillemets: « texte »
- Numbers: 10 000 (space for thousands)
- Dates: 21 novembre 2025

#### Format selection based on proven patterns:

**Norway:**
- Activities → Listicle "Topp 5-10..." (150-200 words per item, 1,200-1,800 total)
- Owner guides → How-to with comprehensive depth (1,800-2,500 words)
- Use-cases → Problem-solution (800-1,200 words)
- City guides → Comprehensive listicle (20-30 items, 2,000-3,000 words)

**France:**
- Professional guides → "Guide complet : [Topic] en 2025" (1,800-2,500 words)
- Regulatory explainers → "Tout savoir sur [Regulation] en 2025" (2,000-3,000 words)
- TCO calculators → "[Option A] vs [Option B] : coût réel" (1,500-2,000 words)
- Consumer inspiration → L'Adventure Lab style narrative (1,500-2,000 words)
- City guides → Geographic + compliance focus (2,000-3,000 words)

Reference market-specific `performance_data` files for format-specific best practices.

### Step 7: Metadata Footer Generation (REQUIRED)

**Every optimized article must include a structured metadata footer for tracking.**

Reference `seo_aeo_best_practices.md` Part 8 for full template. Output format:

```markdown
---

## SEO/AEO Metadata

### Core SEO
| Field | Value |
|-------|-------|
| Title Tag | [50-60 chars with primary keyword] |
| Meta Description | [150-160 chars with CTA] |
| Slug | [url-friendly-slug-with-keyword] |
| Primary Keyword | [main target keyword] |
| Secondary Keywords | [keyword 1, keyword 2, keyword 3] |

### Content Structure
| Field | Value |
|-------|-------|
| H1 | [exact article title] |
| H2 Count | [number of H2 sections] |
| Question Headers | [list of H2s phrased as questions] |
| Answer-First Sections | [Yes/No, count of 40-60 word answer blocks] |
| Word Count | [total] |

### CTA Details
| Field | Value |
|-------|-------|
| Primary CTA | [exact CTA text] |
| CTA Type | [soft / medium / strong] |
| CTA Placement | [end only / middle + end] |

### AEO Readiness
| Field | Value |
|-------|-------|
| FAQ Section | [Yes/No, question count] |
| Featured Snippet Optimized | [Yes/No] |
| Schema Types | [Article, FAQPage, HowTo] |

### Business & Tracking
| Field | Value |
|-------|-------|
| Content Type | [listicle / guide / use-case / city guide] |
| Target Audience | [renter / owner] |
| Market | [NO / FR] |
| Business Fit Score | [1-5] |

### JSON-LD Schema
[Include generated schema code from schema_templates.md]
```

## Using Bundled References

### Reference structure:
```
references/
├── shared/
│   ├── seo_aeo_best_practices.md     # Universal SEO/AEO guidelines (Parts 1-10)
│   ├── aeo_header_patterns.md        # AEO header optimization, answer-first structure
│   ├── cta_framework.md              # CTA psychology, strength matrix, power words
│   ├── schema_templates.md           # JSON-LD templates (Article, FAQPage, HowTo)
│   ├── owner_content_principles.md   # Universal owner content guidelines
│   ├── product_glossary.json         # Multilingual product terminology
│   └── country_config.json           # Structured country configuration
├── norway/
│   ├── market_context_no.md          # Norwegian market specifics + fleet data
│   ├── tone_guide_no.md              # Norwegian tone patterns ("du")
│   ├── performance_data_no.md        # Norwegian blog benchmarks
│   └── owner_content_guide_no.md     # NO-specific owner content guide
└── france/
    ├── market_context_fr.md          # French market specifics + fleet data
    ├── tone_guide_fr.md              # French tone (L'Adventure Lab + "vous")
    ├── performance_data_fr.md        # French blog benchmarks (B2B data)
    ├── keyword_strategy_fr.md        # 7 keyword pillars with volumes
    └── owner_content_guide_fr.md     # FR-specific owner content guide
```

After market detection (Step 0), load market-specific references.

### Norway References

**norway/market_context_no.md** - Contains:
- Getaround products and delivery methods (Norway focus)
- Fleet data (~6,800 active cars, top regions)
- Product details (Connect 290 kr/mnd, If insurance, max value 1M NOK)
- Norway-exclusive features (Native Connect, Langtidsleie, Bobil)
- Norwegian competitors (Hyre, traditional rental)
- USPs for Norwegian market
- Norwegian search behavior patterns
- Norwegian terminology

**norway/performance_data_no.md** - Contains:
- What works in Norway (activity listicles dominate)
- What fails (case studies without data)
- Engagement benchmarks for Norway (65-80% activities, 75-90% owner guides)
- Geographic priorities (Oslo >> Tromsø > Bergen > Stavanger)
- Proven Norwegian formats ("Topp 5/10..." listicles)

**norway/tone_guide_no.md** - Contains:
- "Du" form guidelines
- Warm, adventurous vocabulary
- Norwegian expressions and idioms
- Reader-first principle guidelines
- CTA patterns for Norwegian audience

**norway/owner_content_guide_no.md** - Contains (load for owner content only):
- Connect terminology in Norwegian ("låse opp via Getaround-appen")
- Native Connect formulation
- SmartPrising, Instant booking in Norwegian
- Income examples in NOK by car type and city
- Tax references (Skatteetaten)
- Insurance reference (If)
- Norway-specific checklist

### France References

**france/market_context_fr.md** - Contains:
- Getaround products and delivery methods (France focus)
- Fleet data (~23,200 active vehicles, top cities)
- Product details (Connect 29€/mnd, AXA insurance, max value 50k€)
- Features NOT available in France (Native Connect, Long-term, Motorhome)
- French competitors (Turo main, traditional strong)
- USPs for French market (ZFE compliance, professional solutions, cross-border)
- French search behavior patterns (B2B/professional dominant)
- French terminology and glossary

**france/performance_data_fr.md** - Contains:
- What works in France (B2B/professional guides dominate)
- Top performers (Déplacement professionnel, Redevance, regulatory content)
- Engagement benchmarks for France (70-85% B2B, 65-80% regulatory)
- Geographic priorities (Paris, Lyon, Marseille focus)
- Proven French formats (Professional guides, regulatory explainers, TCO calculators)

**france/keyword_strategy_fr.md** - Contains:
- 7 keyword pillars with volumes and priorities
- Professional/B2B keywords (top priority)
- Regulatory keywords (ZFE, Crit'Air, TVS)
- Vehicle type keywords, city keywords, international travel
- Quick win opportunities

**france/tone_guide_fr.md** - Contains:
- L'Adventure Lab tone patterns (gold standard for consumer content)
- 5 core principles: Invite don't sell, Accessible aspiration, Authentic French voice, Strategic warmth, Practical poetry
- "Vous" form with warmth guidelines
- Reader-first principle guidelines (« Lecteur d'abord »)
- French vocabulary banks by content type
- Opening hooks and CTA formulas
- Typography rules

**france/owner_content_guide_fr.md** - Contains (load for owner content only):
- Connect terminology in French ("déverrouiller via l'application Getaround")
- Tarification intelligente (SmartPrising)
- Income examples in EUR by car type and city
- Tax references (impots.gouv.fr, URSSAF)
- Insurance reference (AXA)
- ZFE context for owner content (Crit'Air advantage)
- Entrepreneurs program details
- France-specific checklist

### Universal References (Shared)

**shared/seo_aeo_best_practices.md** - Contains (Parts 1-10):
- Part 1-6: Traditional SEO fundamentals (keywords, titles, meta, internal linking)
- Hybrid headline strategy (H2=questions, H3=statements with data)
- External reference guidelines (volatile vs stable data handling)
- AEO optimization (FAQ schema, Q&A structure, E-E-A-T, unique data)
- Getaround-specific integration (USP weaving, CTA guidelines)
- Markdown formatting for Ghost CMS
- Quality checklists (SEO, AEO, content, format)
- Common mistakes to avoid
- Part 7: Cross-references to advanced guides
- Part 8: Metadata Footer Template (for spreadsheet tracking)
- Part 9: AI "Interview" Method for unique content
- Part 10: Internal Linking Strategy with prompt template

**shared/aeo_header_patterns.md** - Contains (load for AEO optimization):
- Part 1-4: Why header structure matters for AI Overviews
- Question-format header templates (Hva/Hvordan/Hvor mye, Qu'est-ce que/Comment/Combien)
- Answer-first paragraph structure (40-60 word format)
- Featured snippet optimization (paragraph, list, table types)
- Part 5: Semantic chunking and PAA/Featured Snippet alignment
- Part 6-8: Header hierarchy best practices, Getaround examples, transformations
- Part 9: H2 Content Injection technique for capturing related queries

**shared/cta_framework.md** - Contains (load for content creation):
- Part 1-2: CTA psychology principles (Clarity, Urgency, Value, Exclusivity)
- CTA strength matrix by content type and intent
- Part 3: Power words for car-sharing (NO/FR)
- Part 4-5: CTA placement rules and templates library
- Part 6-8: CTA copywriting formulas, testing checklist, common mistakes

**shared/schema_templates.md** - Contains (load for schema generation):
- Part 1: Article/BlogPosting JSON-LD template
- Part 2: FAQPage JSON-LD template with Getaround examples
- Part 3: HowTo JSON-LD template
- Part 4: Combined schema examples
- Part 5: Validation checklist (Google Rich Results Test)
- Part 6: Ghost CMS integration instructions

**shared/owner_content_principles.md** - Contains (load for owner content only):
- Information Hierarchy Rule (Answer First, Explain After)
- Headline Strategy (H2 questions, H3 statements)
- Reader-First Principle (situation, search, concerns)
- External Reference Guidelines (volatile vs stable data)
- Technical Term Handling (define at first use)
- Article Structure Template (owner guides)
- Quality checklist for owner content

**shared/product_glossary.json** - Contains (reference as needed):
- Multilingual product terminology (EN/NO/FR)
- Correct term translations and definitions
- "Do not translate" markers for brand terms
- Market availability indicators

**shared/country_config.json** - Contains (reference as needed):
- Structured country configuration
- Feature availability matrix
- Fleet data by country
- Pricing and limits per market

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
✅ **Tone calibrated** - Matches market (du/vous) and audience (renter/owner)
✅ **Format proven** - Uses patterns from market-specific performance data
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
- Norway: Bergen/Stavanger/Trondheim have good engagement but low volume vs Oslo
- France: Secondary cities (Nice, Toulouse, Bordeaux) lower priority than Paris/Lyon/Marseille
- Validate if worth optimizing based on market priority
- Consider clustering strategy if appropriate

**Case 5: Existing good performers**
- Focus on AEO enhancements (FAQ, unique data, E-E-A-T)
- Don't over-optimize (if it works, minor tweaks only)
- Protect rankings with freshness updates
- France: Annual updates mandatory for regulatory content (year-stamp 2025 → 2026)

## Critical Reminders

⚠️ **ALWAYS detect market FIRST (Step 0)** - Norway vs France requires completely different approach
⚠️ **ALWAYS validate business fit BEFORE optimizing** - Avoid vanity traffic
⚠️ **Load market-specific references** - Norway needs 3 files, France needs 4 files, plus universal SEO guide
⚠️ **Apply correct tone** - Norway: informal "du", France: formal "vous" with warmth
⚠️ **Apply correct content focus** - Norway: consumer activities, France: B2B/professional
⚠️ **Use proven formats from data** - Norway: listicles, France: professional guides/regulatory
⚠️ **Balance SEO and AEO** - Optimize for both traditional search AND AI overviews
⚠️ **Be actionable** - Every recommendation must be concrete and implementable
⚠️ **Prioritize ruthlessly** - Don't overwhelm user with 50 issues

**Success metrics by market:**
- Norway: 65-80% engagement (activities), 75-90% (owner guides), 1,200-1,800 words typical
- France: 70-85% engagement (B2B), 65-80% (regulatory), 1,800-2,500 words typical
- Both: Drive measurable conversions (bookings or owner registrations)
