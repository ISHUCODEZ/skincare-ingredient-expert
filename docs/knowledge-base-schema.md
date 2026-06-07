# Knowledge Base Schema

## Overview

The knowledge base consists of two databases combined into a single HTML file
(`skincare_knowledge_base.html`) for Botpress ingestion.

---

## Section 1 — Ingredient Encyclopedia

### Schema

| Field | Type | Example | Purpose |
|-------|------|---------|---------|
| Ingredient Name | Text | Niacinamide | Primary identifier |
| Category | Text | Vitamin · Barrier Support | Classification |
| Function | Text | Brightening / Barrier Support | Primary skin function |
| Primary Benefits | Text | Reduces pores, controls oil... | What it does |
| Side Effects | Text | Mild flushing at >5%... | Safety information |
| Pregnancy Safe | Enum | Yes / No / Consult Doctor | Safety classification |
| Comedogenic Rating | Number (0–5) | 0 | Pore-clogging risk scale |
| pH Range | Text | 5.0–7.0 | Optimal efficacy range |
| Skin Types | Text | Oily, Combination, Sensitive | Compatibility |
| Key Interactions | Text | Do NOT mix with Vitamin C... | Combination warnings |
| Scientific Evidence Level | Enum | High / Moderate | Research backing |
| Notes | Text | Expert tips and context | Additional guidance |

### Pregnancy Safe Values
- **Yes** — Safe to use during pregnancy
- **No** — Must avoid during pregnancy
- **Consult Doctor** — Check with healthcare provider before use

### Comedogenic Scale
- **0** — Non-comedogenic (won't clog pores)
- **1** — Very low risk
- **2** — Low risk
- **3** — Moderate risk
- **4** — Fairly high risk
- **5** — Highly comedogenic

### Evidence Levels
- **High** — Multiple large-scale clinical studies, well-established
- **Moderate** — Some clinical evidence, growing research base

### Ingredients List (26 total)

| # | Ingredient | Category | Pregnancy Safe | Evidence |
|---|-----------|----------|----------------|----------|
| 1 | Niacinamide | Vitamin | Yes | High |
| 2 | Retinol | Retinoid | No | High |
| 3 | Hyaluronic Acid | Humectant | Yes | High |
| 4 | Salicylic Acid (BHA) | Acid | No | High |
| 5 | Glycolic Acid (AHA) | Acid | Consult | High |
| 6 | Lactic Acid (AHA) | Acid | Consult | High |
| 7 | Vitamin C (L-Ascorbic Acid) | Antioxidant | Yes | High |
| 8 | Ceramides | Lipid | Yes | High |
| 9 | Azelaic Acid | Acid | Yes | High |
| 10 | Benzoyl Peroxide | Antibacterial | Consult | High |
| 11 | Peptides | Amino Acid | Yes | Moderate |
| 12 | Tranexamic Acid | Brightening | Consult | Moderate |
| 13 | Alpha Arbutin | Brightening | Consult | Moderate |
| 14 | Centella Asiatica | Plant Extract | Yes | Moderate |
| 15 | Bakuchiol | Plant-derived | Yes | Moderate |
| 16 | Squalane | Lipid | Yes | High |
| 17 | Glycerin | Humectant | Yes | High |
| 18 | Ferulic Acid | Antioxidant | Yes | High |
| 19 | SPF / Sunscreen | UV Filter | Yes (mineral) | High |
| 20 | Kojic Acid | Brightening | No | Moderate |
| 21 | Snail Secretion Filtrate | Biological | Yes | Moderate |
| 22 | Mandelic Acid (AHA) | Acid | Consult | Moderate |
| 23 | Tea Tree Oil | Essential Oil | Consult | Moderate |
| 24 | Zinc PCA | Mineral | Yes | Moderate |
| 25 | Resveratrol | Antioxidant | Yes | Moderate |
| 26 | Polyglutamic Acid | Polypeptide | Yes | Moderate |

---

## Section 2 — Product Database

### Schema

| Field | Type | Example | Purpose |
|-------|------|---------|---------|
| Product Name | Text | CeraVe Moisturizing Cream | Primary identifier |
| Brand | Text | CeraVe | Brand classification |
| Category | Text | Moisturizer | Product type |
| Key Ingredients | Text | Ceramides 1/3/6-II, HA | Active ingredients |
| Skin Type | Text | Dry, Sensitive, Normal | Compatibility |
| Primary Benefits | Text | Barrier repair, hydration | What it does |
| Side Effects / Cautions | Text | Petrolatum may feel heavy... | Warnings |
| Rating | Number (0–5) | 4.8 | User satisfaction score |
| Price (USD) | Currency | $17 | Approximate retail price |
| Pregnancy Safe | Enum | Yes / No / Consult | Safety classification |
| Routine Step | Text | Moisturizer | Where in routine |
| Frequency | Text | AM + PM | How often to use |
| Notes | Text | Fragrance-free; derm recommended | Expert tips |
| Where to Buy | Text | Drugstore, Amazon | Retail channels |

### Routine Steps (in order)
1. Cleanser
2. Toner
3. Essence
4. Exfoliant (2–3x/week, not daily)
5. Serum / Treatment
6. Facial Oil
7. Moisturizer
8. SPF (AM only, final step)
9. Spot Treatment (as needed)

### Categories Covered
- Serum
- Moisturizer
- Cleanser
- Sunscreen
- Retinol / Retinoid
- Exfoliant (AHA/BHA)
- Spot Treatment
- Toner
- Essence
- Facial Oil
- Occlusive / Healing

### Price Range Distribution
- Under $15: 8 products (budget)
- $15–$35: 10 products (mid-range)
- $35–$75: 8 products (premium)
- Over $75: 5 products (luxury)

### Products List (31 total)

| # | Product | Brand | Category | Rating | Price |
|---|---------|-------|----------|--------|-------|
| 1 | Niacinamide 10% + Zinc 1% | The Ordinary | Serum | 4.4 | $6 |
| 2 | Hyaluronic Acid 2% + B5 | The Ordinary | Serum | 4.5 | $7 |
| 3 | Moisturizing Cream | CeraVe | Moisturizer | 4.8 | $17 |
| 4 | Foaming Facial Cleanser | CeraVe | Cleanser | 4.6 | $14 |
| 5 | Toleriane Double Repair | La Roche-Posay | Moisturizer | 4.7 | $22 |
| 6 | 2% BHA Liquid Exfoliant | Paula's Choice | Exfoliant | 4.7 | $34 |
| 7 | C E Ferulic | SkinCeuticals | Vitamin C Serum | 4.8 | $182 |
| 8 | T.L.C. Framboos Night Serum | Drunk Elephant | AHA/BHA Serum | 4.5 | $90 |
| 9 | Retinol 0.5% in Squalane | The Ordinary | Retinol | 4.3 | $10 |
| 10 | Adapalene Gel 0.1% | Differin | Retinoid | 4.6 | $32 |
| 11 | Gentle Skin Cleanser | Cetaphil | Cleanser | 4.6 | $14 |
| 12 | Hydro Boost Water Gel | Neutrogena | Moisturizer | 4.5 | $22 |
| 13 | UV Clear SPF 46 | EltaMD | Sunscreen | 4.8 | $40 |
| 14 | Advanced Snail 96 Mucin Essence | COSRX | Essence | 4.7 | $25 |
| 15 | Acne Pimple Master Patch | COSRX | Spot Treatment | 4.8 | $11 |
| 16 | Good Genes Lactic Acid | Sunday Riley | AHA Serum | 4.6 | $85 |
| 17 | Hyaluronic Acid Toner | Isntree | Toner | 4.7 | $22 |
| 18 | Aquaphor Healing Ointment | Beiersdorf | Occlusive | 4.8 | $14 |
| 19 | The Water Cream | Tatcha | Moisturizer | 4.5 | $72 |
| 20 | Effaclar Duo | La Roche-Posay | Spot Treatment | 4.5 | $30 |
| 21 | Regenerist Micro-Sculpting Cream | Olay | Moisturizer | 4.5 | $25 |
| 22 | Low pH Good Morning Gel Cleanser | COSRX | Cleanser | 4.5 | $12 |
| 23 | Alpha Arbutin 2% + HA | The Ordinary | Serum | 4.4 | $10 |
| 24 | Ultra Repair Cream | First Aid Beauty | Moisturizer | 4.7 | $38 |
| 25 | Watermelon Niacinamide Dew Drops | Glow Recipe | Serum | 4.4 | $42 |
| 26 | Retinol Youth Renewal Serum | Murad | Retinol Serum | 4.5 | $102 |
| 27 | Squalane + Vitamin C Rose Oil | Biossance | Facial Oil | 4.4 | $72 |
| 28 | Salicylic Acid Daily Cleanser | COSRX | Cleanser | 4.4 | $14 |
| 29 | Retinol Serum | The INKEY List | Retinol | 4.3 | $11 |
| 30 | Futuredew | Glossier | Serum-Oil | 4.3 | $38 |
| 31 | Moisturizing Lotion | Cetaphil | Moisturizer | 4.5 | $13 |
