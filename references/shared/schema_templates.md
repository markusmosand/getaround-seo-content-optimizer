# Schema Markup Templates for Getaround Content

JSON-LD structured data templates for FAQPage, HowTo, and Article/BlogPosting schema.

---

## Part 1: Schema Markup Overview

### Why Schema Matters (2025-2026)

**Key Statistics:**
- JSON-LD is used by 45+ million domains
- Entity-rich markup can deliver 15x AI search visibility
- Google's preferred format for structured data
- Essential for voice search and AI assistant responses

**Important Notes:**
- FAQPage rich results are now limited to authoritative sites (government, health)
- Schema still helps Google understand content even without rich results
- All content in schema MUST be visible on the page
- Don't add FAQPage just to grab SERP space—only when genuine FAQ content exists

### Schema Types for Getaround Content

| Schema Type | Use When | Priority |
|-------------|----------|----------|
| Article/BlogPosting | Every blog post | Required |
| FAQPage | 3+ Q&A pairs in content | High |
| HowTo | Step-by-step guides | High |
| LocalBusiness | Location-specific pages | Medium |

---

## Part 2: Article/BlogPosting Schema

### When to Use
- Every blog article
- Required for all Getaround blog content

### Template

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[Article Title - max 110 characters]",
  "description": "[Meta description - 150-160 characters]",
  "image": "[Featured image URL]",
  "author": {
    "@type": "Person",
    "name": "[Author Name]",
    "url": "[Author Profile URL if available]"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Getaround",
    "logo": {
      "@type": "ImageObject",
      "url": "https://getaround.com/logo.png"
    }
  },
  "datePublished": "[YYYY-MM-DD]",
  "dateModified": "[YYYY-MM-DD]",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "[Article URL]"
  }
}
```

### Getaround Example (Norwegian Blog)

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Topp 5 aktiviteter for barn i Oslo | 2025 guide",
  "description": "Oppdag de beste aktivitetene for barn i Oslo. Komplett guide med parkering, priser og tips. Planlegg den perfekte familiedagen!",
  "image": "https://getaround.com/blog/images/oslo-barn-aktiviteter.jpg",
  "author": {
    "@type": "Person",
    "name": "Getaround Team"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Getaround Norge",
    "logo": {
      "@type": "ImageObject",
      "url": "https://getaround.com/logo.png"
    }
  },
  "datePublished": "2025-01-15",
  "dateModified": "2025-01-15",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://getaround.com/blogg/topp-5-aktiviteter-barn-oslo"
  }
}
```

### Getaround Example (French Blog)

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Location voiture mariage : Guide complet 2025",
  "description": "Découvrez comment louer la voiture parfaite pour votre mariage. Conseils, prix et options disponibles sur Getaround.",
  "image": "https://getaround.com/blog/images/voiture-mariage.jpg",
  "author": {
    "@type": "Person",
    "name": "Équipe Getaround"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Getaround France",
    "logo": {
      "@type": "ImageObject",
      "url": "https://getaround.com/logo.png"
    }
  },
  "datePublished": "2025-01-15",
  "dateModified": "2025-01-15",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://fr.getaround.com/blog/location-voiture-mariage"
  }
}
```

---

## Part 3: FAQPage Schema

### When to Use
- Article has dedicated FAQ section with 3+ questions
- Questions are visible on the page (not hidden/collapsed)
- Questions are genuine user questions (not promotional)

### Template

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[Question text exactly as shown on page]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[Full answer text exactly as shown on page]"
      }
    },
    {
      "@type": "Question",
      "name": "[Question 2]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[Answer 2]"
      }
    }
  ]
}
```

### Getaround Example (Norwegian)

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Hvor mye koster det å leie bil i Oslo?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Billeie i Oslo koster typisk 200-800 kr per dag, avhengig av biltype og sesong. En kompakt elbil starter på rundt 200-350 kr/dag, mens premium-biler som Tesla Model 3 ligger på 500-800 kr/dag. Langtidsleie over 7 dager gir ofte 20-30% rabatt."
      }
    },
    {
      "@type": "Question",
      "name": "Er forsikring inkludert i leieprisen?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Ja, full forsikring er inkludert i alle Getaround-bookinger. Standarddekningen omfatter ansvarsforsikring og kasko med 8000 kr egenandel. Du kan oppgradere til redusert egenandel (3000 kr eller 0 kr) mot et daglig tillegg."
      }
    },
    {
      "@type": "Question",
      "name": "Hvordan fungerer Getaround Connect?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Med Getaround Connect låser du opp og starter bilen direkte med appen - ingen fysisk nøkkelutveksling. Bilen har en installert boks som kommuniserer med telefonen din. Du får tilgang til bilen fra det øyeblikket leieperioden starter."
      }
    }
  ]
}
```

### Getaround Example (French)

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Combien coûte la location d'une voiture à Paris ?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "La location d'une voiture à Paris coûte généralement entre 30€ et 120€ par jour, selon le type de véhicule et la saison. Une citadine électrique commence à environ 30-50€/jour, tandis que les véhicules premium comme la Tesla Model 3 coûtent entre 80-120€/jour."
      }
    },
    {
      "@type": "Question",
      "name": "L'assurance est-elle incluse dans le prix de location ?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Oui, une assurance complète est incluse dans toutes les réservations Getaround. La couverture standard comprend l'assurance responsabilité civile et tous risques avec une franchise de 800€. Vous pouvez opter pour une franchise réduite (300€ ou 0€) moyennant un supplément journalier."
      }
    },
    {
      "@type": "Question",
      "name": "Comment fonctionne Getaround Connect ?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Avec Getaround Connect, vous déverrouillez et démarrez la voiture directement avec l'application - sans échange de clés. La voiture est équipée d'un boîtier qui communique avec votre téléphone. Vous avez accès au véhicule dès le début de votre période de location."
      }
    }
  ]
}
```

---

## Part 4: HowTo Schema

### When to Use
- Step-by-step guides (booking process, owner signup, etc.)
- Content has clear sequential steps
- At least 3 steps in the process

### Template

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "[How to achieve result]",
  "description": "[Brief description of what this guide helps achieve]",
  "totalTime": "PT[X]M",
  "estimatedCost": {
    "@type": "MonetaryAmount",
    "currency": "[NOK/EUR]",
    "value": "[amount or range]"
  },
  "step": [
    {
      "@type": "HowToStep",
      "name": "[Step 1 title]",
      "text": "[Step 1 detailed instructions]",
      "url": "[URL to this step if applicable]",
      "image": "[Step image URL if available]"
    },
    {
      "@type": "HowToStep",
      "name": "[Step 2 title]",
      "text": "[Step 2 detailed instructions]"
    }
  ]
}
```

### Getaround Example: How to Book a Car (Norwegian)

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "Hvordan booke bil på Getaround",
  "description": "Komplett guide til å booke leiebil på Getaround - fra søk til nøkkelfri tilgang.",
  "totalTime": "PT5M",
  "step": [
    {
      "@type": "HowToStep",
      "name": "Søk etter biler",
      "text": "Åpne Getaround-appen eller gå til getaround.com. Skriv inn stedet du ønsker å hente bilen, samt dato og tidspunkt for leieperioden."
    },
    {
      "@type": "HowToStep",
      "name": "Velg bil",
      "text": "Bla gjennom tilgjengelige biler og filtrer etter biltype, pris eller funksjoner. Sjekk bilder, beskrivelse og anmeldelser fra tidligere leietakere."
    },
    {
      "@type": "HowToStep",
      "name": "Bekreft booking",
      "text": "Klikk 'Book nå' og fullfør betalingen. Du mottar bekreftelse på e-post og i appen med alle detaljer om bilen og henting."
    },
    {
      "@type": "HowToStep",
      "name": "Lås opp bilen",
      "text": "Når leieperioden starter, gå til bilen og bruk 'Lås opp'-knappen i appen. Med Connect-biler får du tilgang uten fysisk nøkkel."
    },
    {
      "@type": "HowToStep",
      "name": "Kjør og lever tilbake",
      "text": "Bruk bilen i leieperioden. Ved slutten parkerer du på avtalt sted, låser via appen, og tar bilde av bilen som dokumentasjon."
    }
  ]
}
```

### Getaround Example: How to List Your Car (Owner - Norwegian)

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "Hvordan leie ut bilen din på Getaround",
  "description": "Steg-for-steg guide til å registrere bilen din på Getaround og begynne å tjene penger.",
  "totalTime": "PT10M",
  "estimatedCost": {
    "@type": "MonetaryAmount",
    "currency": "NOK",
    "value": "0"
  },
  "step": [
    {
      "@type": "HowToStep",
      "name": "Opprett konto",
      "text": "Gå til getaround.com/owner og registrer deg med e-post eller Facebook. Verifiser identiteten din med BankID."
    },
    {
      "@type": "HowToStep",
      "name": "Legg til bilen din",
      "text": "Fyll inn bilens registreringsnummer, merke, modell og årsmodell. Last opp minst 6 bilder av bilen fra ulike vinkler."
    },
    {
      "@type": "HowToStep",
      "name": "Sett pris og tilgjengelighet",
      "text": "Velg dagspris basert på Getarounds prisforslag. Angi hvilke dager og tider bilen er tilgjengelig i kalenderen."
    },
    {
      "@type": "HowToStep",
      "name": "Installer Connect",
      "text": "Bestill gratis Connect-boksen som monteres i bilen. Dette lar leietakere låse opp bilen med telefonen - ingen nøkkelutveksling."
    },
    {
      "@type": "HowToStep",
      "name": "Start å tjene",
      "text": "Når bilen er godkjent og Connect installert, blir den synlig for leietakere. Godkjenn bookinger og motta utbetaling automatisk."
    }
  ]
}
```

---

## Part 5: Combined Schema Example

### Article + FAQPage (Most Common)

When an article includes an FAQ section, combine both schemas:

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Article",
      "headline": "Topp 5 aktiviteter for barn i Oslo | 2025 guide",
      "description": "Oppdag de beste aktivitetene for barn i Oslo. Komplett guide med parkering, priser og tips.",
      "image": "https://getaround.com/blog/images/oslo-barn-aktiviteter.jpg",
      "author": {
        "@type": "Person",
        "name": "Getaround Team"
      },
      "publisher": {
        "@type": "Organization",
        "name": "Getaround Norge",
        "logo": {
          "@type": "ImageObject",
          "url": "https://getaround.com/logo.png"
        }
      },
      "datePublished": "2025-01-15",
      "dateModified": "2025-01-15",
      "mainEntityOfPage": {
        "@type": "WebPage",
        "@id": "https://getaround.com/blogg/topp-5-aktiviteter-barn-oslo"
      }
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {
          "@type": "Question",
          "name": "Hvor mye koster det å besøke attraksjonene i Oslo?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Prisene varierer fra gratis (flere parker og utendørsområder) til ca 400 kr for voksne på Tusenfryd. De fleste museer tilbyr gratis inngang for barn under 18 år."
          }
        },
        {
          "@type": "Question",
          "name": "Trenger vi bil for å besøke attraksjonene?",
          "acceptedAnswer": {
            "@type": "Answer",
            "text": "Mange attraksjoner i Oslo sentrum er tilgjengelig med kollektivtransport, men leiebil gir mer fleksibilitet, spesielt for å besøke Bygdøy-museene, Tusenfryd eller Holmenkollen på samme dag."
          }
        }
      ]
    }
  ]
}
```

### Article + HowTo (For Guide Content)

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Article",
      "headline": "Hvordan booke bil på Getaround: Komplett guide",
      "description": "Lær hvordan du booker leiebil på Getaround på under 5 minutter. Steg-for-steg guide med tips.",
      "author": {
        "@type": "Person",
        "name": "Getaround Team"
      },
      "publisher": {
        "@type": "Organization",
        "name": "Getaround Norge"
      },
      "datePublished": "2025-01-15"
    },
    {
      "@type": "HowTo",
      "name": "Book bil på Getaround",
      "totalTime": "PT5M",
      "step": [
        {
          "@type": "HowToStep",
          "name": "Søk etter biler",
          "text": "Åpne appen og søk etter biler i ditt område."
        },
        {
          "@type": "HowToStep",
          "name": "Velg og book",
          "text": "Velg ønsket bil og fullfør bookingen med betaling."
        },
        {
          "@type": "HowToStep",
          "name": "Lås opp og kjør",
          "text": "Bruk appen til å låse opp bilen når leieperioden starter."
        }
      ]
    }
  ]
}
```

---

## Part 6: Validation Checklist

### Before Adding Schema

- [ ] All content in schema is visible on the page
- [ ] No hidden or collapsed content in FAQ answers
- [ ] Questions are genuine user questions (not promotional)
- [ ] Answers are comprehensive and helpful
- [ ] HowTo steps are in correct sequential order
- [ ] Dates are in correct format (YYYY-MM-DD)
- [ ] URLs are absolute (not relative)
- [ ] Image URLs are accessible

### Schema Validation Tools

1. **Google Rich Results Test**
   - URL: https://search.google.com/test/rich-results
   - Tests if schema is valid and eligible for rich results

2. **Schema.org Validator**
   - URL: https://validator.schema.org/
   - Validates JSON-LD syntax

3. **JSON-LD Playground**
   - URL: https://json-ld.org/playground/
   - Tests JSON-LD structure

### Common Validation Errors

| Error | Cause | Fix |
|-------|-------|-----|
| Missing required field | Incomplete schema | Add all required fields |
| Invalid date format | Wrong date format | Use YYYY-MM-DD |
| Invalid URL | Relative URL used | Use absolute URLs |
| Content not visible | Schema has hidden content | Only include visible content |
| Duplicate schema | Multiple identical schemas | Use @graph for combining |

---

## Part 7: Ghost CMS Integration

### Where to Add Schema

**Option 1: Code Injection (Site-wide header)**
- Ghost Admin → Settings → Code injection → Site Header
- Good for: Publisher schema, organization info

**Option 2: Post Code Injection**
- Ghost Admin → Post → Settings → Code injection
- Good for: Article-specific schema (FAQPage, HowTo)

### Adding Schema in Ghost

1. Go to the post in Ghost Admin
2. Click the settings gear icon
3. Scroll to "Code injection"
4. Paste the JSON-LD in the "Post Header" field:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [...]
}
</script>
```

### Schema Template for Ghost Posts

When creating content, include this at the end of the metadata section:

```markdown
### JSON-LD Schema (Copy to Ghost Code Injection)

```html
<script type="application/ld+json">
[SCHEMA JSON HERE]
</script>
```
```

---

## Part 8: Quick Reference Templates

### Minimal Article Schema (Copy-Paste Ready)

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "[TITLE]",
  "description": "[META DESCRIPTION]",
  "author": {"@type": "Person", "name": "Getaround Team"},
  "publisher": {"@type": "Organization", "name": "Getaround"},
  "datePublished": "[YYYY-MM-DD]"
}
</script>
```

### Minimal FAQPage Schema (Copy-Paste Ready)

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[Q1]",
      "acceptedAnswer": {"@type": "Answer", "text": "[A1]"}
    },
    {
      "@type": "Question",
      "name": "[Q2]",
      "acceptedAnswer": {"@type": "Answer", "text": "[A2]"}
    },
    {
      "@type": "Question",
      "name": "[Q3]",
      "acceptedAnswer": {"@type": "Answer", "text": "[A3]"}
    }
  ]
}
</script>
```

### Minimal HowTo Schema (Copy-Paste Ready)

```json
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "[HOW TO TITLE]",
  "step": [
    {"@type": "HowToStep", "name": "[Step 1]", "text": "[Instructions 1]"},
    {"@type": "HowToStep", "name": "[Step 2]", "text": "[Instructions 2]"},
    {"@type": "HowToStep", "name": "[Step 3]", "text": "[Instructions 3]"}
  ]
}
</script>
```

---

## Schema Decision Flowchart

```
Does the article have an FAQ section with 3+ questions?
├─ Yes → Add FAQPage schema
└─ No → Skip FAQPage

Does the article explain a step-by-step process?
├─ Yes → Add HowTo schema
└─ No → Skip HowTo

All articles get:
└─ Article/BlogPosting schema (always)
```
