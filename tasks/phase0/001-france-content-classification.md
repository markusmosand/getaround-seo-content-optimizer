# Task 001: France Blog - Content Classification

## Status: [ ] Todo

## Prerequisite
- Task 000 (GSC extraction) completed
- Top 100 pages data available

## Objective
Classify the top 100 France blog articles by content type and format to understand what's actually performing.

---

## Classification Taxonomy

### Content Type Categories
Classify each article into ONE primary category:

| Category | Trigger Keywords (in URL or title) |
|----------|-----------------------------------|
| **B2B/Professional** | entreprise, professionnel, déplacement, flotte, TVS, corporate |
| **B2C/Consumer** | vacances, weekend, famille, road trip, voyage, loisir |
| **Regulatory** | ZFE, Crit'Air, vignette, amende, loi, réglementation, contravention |
| **City Guides** | Paris, Lyon, Marseille, Bordeaux, que faire, visiter, découvrir |
| **How-to/Practical** | comment, guide, conseil, astuce, tutoriel |
| **Comparison** | vs, comparatif, meilleur, alternative, différence |
| **Owner/Supply** | propriétaire, louer sa voiture, revenus, mettre en location |
| **Product Features** | livraison, Connect, longue durée, assurance, Getaround |
| **Pricing** | prix, tarif, coût, budget, économiser |
| **Seasonal** | été, hiver, Noël, vacances scolaires, été 2025 |

### Format Categories
Classify each article into ONE format:

| Format | Pattern |
|--------|---------|
| **Listicle** | "X choses", "Top X", "Les X meilleurs" |
| **Comprehensive Guide** | "Guide complet", "Tout savoir sur" |
| **How-to** | "Comment..." |
| **Comparison** | "X vs Y", "Comparatif" |
| **Year-stamped** | Contains 2024, 2025, or year reference |
| **Question-based** | Title starts with question word |
| **News/Update** | "Nouveau", "Mise à jour", "Annonce" |
| **Standard Article** | None of the above |

---

## Classification Process

### Step 1: Load Top 100 Pages
From `analysis/france_raw/pages_full_year.json`, extract top 100 by impressions.

### Step 2: Classify Each Page
For each URL, determine:
1. **Content Type** (single category)
2. **Format** (single format)
3. **Business Fit Score** (1-5): Does this attract car rental intent?
   - 5 = High intent ("road trip rentals", "rent car Paris")
   - 3 = Medium intent ("things to do in Lyon" - may need car)
   - 1 = Low intent ("car maintenance", "traffic regulations")

### Step 3: Create Classification Table

```markdown
| Rank | URL | Title | Content Type | Format | Biz Fit | Impressions | Clicks | CTR |
|------|-----|-------|--------------|--------|---------|-------------|--------|-----|
| 1 | /blog/... | ... | B2C/Consumer | Listicle | 4 | ... | ... | ... |
```

---

## Output Format

Add to `analysis/FRANCE_BLOG_ANALYSIS_2025.md`:

```markdown
## Content Classification Results

### Content Type Distribution
| Content Type | # Articles | % of Top 100 | Total Impressions | Avg CTR |
|--------------|------------|--------------|-------------------|---------|
| B2B/Professional | | | | |
| B2C/Consumer | | | | |
| Regulatory | | | | |
| City Guides | | | | |
| How-to | | | | |
| Comparison | | | | |
| Owner/Supply | | | | |
| Product Features | | | | |
| Pricing | | | | |
| Seasonal | | | | |

### Format Distribution
| Format | # Articles | % of Top 100 | Avg Impressions | Avg CTR |
|--------|------------|--------------|-----------------|---------|
| Listicle | | | | |
| Comprehensive Guide | | | | |
| How-to | | | | |
| Comparison | | | | |
| Year-stamped | | | | |
| Question-based | | | | |
| Standard Article | | | | |

### Business Fit Distribution
| Score | # Articles | Description |
|-------|------------|-------------|
| 5 | | High rental intent |
| 4 | | Good rental intent |
| 3 | | Medium intent |
| 2 | | Low intent |
| 1 | | Vanity traffic |

### Top 10 by Content Type (Best Performer per Category)
[Table showing best performing article from each category]

### Classification Data
Full classification saved to: `analysis/france_raw/content_classification.csv`
```

---

## Key Questions to Answer

After classification, document answers to:

1. **What % is B2B vs B2C content?**
   - Assumption: B2B is 60% → Actual: ____%

2. **What % is regulatory content?**
   - Expected to be significant for France → Actual: ____%

3. **Which content type has highest CTR?**
   - Assumption: Professional guides → Actual: ____

4. **Which format performs best?**
   - Does "Guide complet" outperform listicles? → Actual: ____

5. **What's the business fit of top performers?**
   - Are high-traffic articles actually relevant to rentals?

---

## Completion Checklist
- [ ] All 100 articles classified
- [ ] Distribution tables created
- [ ] Key questions answered
- [ ] Surprising findings documented
- [ ] ROADMAP.md updated

## Notes & Observations
[Add findings that challenge assumptions here]
