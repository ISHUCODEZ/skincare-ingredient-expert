# Architecture — Kitty AI Skincare Expert

## System Design

Kitty AI is a Retrieval-Augmented Generation (RAG) chatbot built on Botpress Cloud.
The agent retrieves information from a custom knowledge base before generating responses,
ensuring all answers are grounded in curated skincare data.

## Flow Diagram

```
User Input
    │
    ▼
[Botpress Autonomous Node]
    │
    ├── 1. Receives user message
    │
    ├── 2. Searches Knowledge Base
    │        └── skincare_knowledge_base.html
    │                ├── Ingredient Encyclopedia (26 entries)
    │                └── Product Database (31 entries)
    │
    ├── 3. Retrieves relevant chunks (~500 tokens each, ~15 total chunks)
    │
    ├── 4. Constructs response using:
    │        ├── Retrieved KB data
    │        └── System prompt instructions
    │
    └── 5. Returns answer to user
```

## Knowledge Base Architecture

### Why HTML over CSV/Tables for Botpress

Botpress Knowledge Base reads documents as plain text and chunks them into
searchable segments. HTML was chosen over CSV/Tables because:

- **Flat structure**: All content visible in one page — no hidden tabs or JS
- **Semantic labels**: Field labels (Function, Benefits, pH Range, etc.) appear
  inline with values, giving the AI full context per chunk
- **No data loss**: CSV uploaded as a Table requires column mapping that can
  fail; HTML reads like a document and indexes reliably
- **Single file**: One upload covers both ingredient and product databases

### Chunking Strategy

Botpress splits documents into ~500 token chunks for vector search.
The HTML file (~7,537 tokens total) produces approximately 15 chunks,
each containing 1–2 complete ingredient or product entries with all fields.

This means a question like "Is niacinamide safe in pregnancy?" retrieves
the Niacinamide chunk which contains ALL fields including Pregnancy Safe,
Interactions, Benefits, pH Range — giving the AI complete context to answer.

### Data Fields Coverage

#### Per Ingredient (12 fields)
1. Ingredient Name
2. Category
3. Function
4. Primary Benefits
5. Side Effects
6. Pregnancy Safe (Yes / No / Consult Doctor)
7. Comedogenic Rating (0–5)
8. pH Range
9. Skin Types
10. Key Interactions
11. Scientific Evidence Level (High / Moderate)
12. Notes / Expert Tips

#### Per Product (14 fields)
1. Product Name
2. Brand
3. Category
4. Key Ingredients
5. Skin Type
6. Primary Benefits
7. Side Effects / Cautions
8. Rating (out of 5)
9. Price (USD)
10. Pregnancy Safe
11. Routine Step
12. Frequency
13. Key Interactions / Notes
14. Where to Buy

## Botpress Node Configuration

### Standard1 Node
- Type: Standard
- Purpose: Display welcome message on conversation start
- Content: "Hello! I'm Kitty AI, your skincare expert..."

### Autonomous1 Node
- Type: Autonomous (loops until exit condition met)
- Purpose: AI reasoning, KB search, response generation
- Tools enabled: Search Knowledge (1 tool)
- Knowledge Base linked: Cosmetics Ingredient Expert
- Exit condition: After providing a response to the user

## Limitations

- Knowledge base is static — requires manual update for new ingredients/products
- No user session memory between conversations (Botpress free tier)
- Cannot access real-time data (new product launches, price changes)
- Not a substitute for professional dermatological advice
