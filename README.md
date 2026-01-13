# Getaround SEO Content Optimizer

A Claude AI skill for analyzing and optimizing blog content for car-sharing platforms, with dual focus on traditional SEO and AEO (Answer Engine Optimization) for AI overviews.

## Overview

This skill enables Claude to:
- **Analyze** existing blog articles across 6 SEO/AEO dimensions
- **Validate** business fit to avoid "vanity traffic" 
- **Optimize** content for both search engines and AI overviews
- **Create** fully optimized articles ready for CMS publication
- **Calibrate** tone and approach for different markets and audiences

## Multi-Market Support

| Market | Tone | Focus | Top Formats |
|--------|------|-------|-------------|
| 🇳🇴 Norway | Informal "du" | Consumer activities (70%) | Listicles, city guides |
| 🇫🇷 France | Formal "vous" | B2B/professional (60%) | Regulatory guides, TCO calculators |

## Installation

### For Claude Desktop / Claude.ai

1. Copy the skill folder to your skills directory:
   ```bash
   cp -r getaround-seo-content-optimizer /path/to/skills/user/
   ```

2. The skill will be automatically detected when Claude loads skills.

### Skill Structure

```
getaround-seo-content-optimizer/
├── SKILL.md                    # Main skill definition
├── README.md                   # This file
└── references/
    ├── norway/                 # Norwegian market context
    │   ├── market_context_no.md
    │   ├── performance_data_no.md
    │   ├── tone_guide_no.md
    │   └── owner_content_guide_no.md
    ├── france/                 # French market context
    │   ├── market_context_fr.md
    │   ├── performance_data_fr.md
    │   ├── tone_guide_fr.md
    │   ├── keyword_strategy_fr.md
    │   └── owner_content_guide_fr.md
    └── shared/                 # Universal guidelines
        ├── seo_aeo_best_practices.md
        ├── owner_content_principles.md
        ├── product_glossary.json
        └── country_config.json
```

## Usage

### Trigger Phrases

- "Optimize this article"
- "Analyze blog performance"
- "Rewrite for better ranking"
- "Is this article worth writing?"
- "Make this AI-overview ready"

### Example Prompts

**Analysis:**
```
Analyze this Norwegian blog article for SEO performance:
[paste article URL or content]
```

**Optimization:**
```
Optimize this French B2B article for ZFE compliance keywords:
[paste content]
```

**Validation:**
```
Is this topic worth writing about for Getaround Norway?
Topic: "Best winter activities in Oslo with a rental car"
```

## Core Workflow

1. **Market Detection** - Automatically identifies Norway vs France based on URL, language, or explicit mention
2. **Context Loading** - Loads market-specific references (tone, performance data, keywords)
3. **Business Fit Validation** - Ensures content drives conversions, not vanity traffic
4. **Six-Dimensional Analysis**:
   - Keyword & Search Intent Alignment
   - Structure & Readability
   - Content Quality & Depth
   - Engagement Signals
   - AEO-Readiness
   - Product-Content Fit

5. **Optimization Output** - Full Markdown article ready for Ghost CMS

## Quality Standards

Every optimization achieves:
- ✅ Business fit validated
- ✅ Search intent matched
- ✅ Keywords properly placed
- ✅ Structure optimized for mobile
- ✅ AEO-ready (FAQ, E-E-A-T signals)
- ✅ Getaround USPs integrated naturally
- ✅ Tone calibrated for market
- ✅ Proven format applied

## Customization

### Adapting for Other Brands

To adapt this skill for another brand:

1. **Replace references/** with your market data
2. **Update product_glossary.json** with your terminology
3. **Modify country_config.json** for your markets
4. **Adjust SKILL.md** triggers and brand mentions

### Adding New Markets

1. Create new folder in `references/` (e.g., `references/spain/`)
2. Add market-specific files following the Norway/France pattern
3. Update market detection logic in SKILL.md

## Contributing

Contributions welcome! Please ensure:
- Market-specific content goes in the appropriate `references/` subfolder
- Universal guidelines go in `references/shared/`
- Update the workflow in SKILL.md if adding new capabilities

## License

MIT License - see [LICENSE](LICENSE) for details.

## Author

Built for [Getaround](https://getaround.com) by August @ Getaround Norway.

---

*This skill is designed for use with Claude AI and follows the Claude Skills format.*
