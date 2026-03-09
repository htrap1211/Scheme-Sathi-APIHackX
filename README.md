# Scheme Sathi
### AI-Powered Government Scheme Matcher for Indian Citizens

> **API Innovate 2026 Submission** — Built with ASI:One (ASI-1 Mini) API
> Helps Indian citizens discover government welfare schemes they qualify for in seconds.

---

## What It Does

A citizen fills a 12-field profile form → the app makes **3 chained calls to the ASI:One API** → returns personalized government schemes they qualify for, with eligibility reasoning, estimated benefits, a step-by-step action plan, and an interactive AI chat for follow-up questions.

**Live Demo:** Just open `index.html` — the API key is pre-configured and ready to use.

---

## Key Features

- **3-Step Chained AI Prompting** — progressive reasoning from profile → eligibility → action plan
- **40 Government Schemes** across 7 categories (Agriculture, Health, Education, Housing, Employment, Women & Children, Senior Citizens)
- **AI Chat Assistant** — ask follow-up questions about any scheme, fully context-aware
- **Printable Document Checklist** — AI generates a personalized document list (4th API call)
- **Bilingual UI** — English and Hindi, with AI responses in the user's chosen language
- **WhatsApp Share** — share results directly via WhatsApp
- **Demo Personas** — try the app instantly with pre-built citizen profiles
- **Impact Counter** — tracks how many citizens have used the tool
- **Mobile-First Design** — Indian tricolor theme, works on any screen size

---

## Setup

### Open & Use Immediately
- Open `index.html` in any modern browser — **no build step, no server, no configuration needed**
- The ASI:One API key is pre-configured — just open and use

### Tech Stack
- **Frontend:** Vanilla HTML/CSS/JavaScript — zero frameworks, zero dependencies
- **AI:** ASI:One (ASI-1 Mini) via REST API at `https://api.asi1.ai/v1/chat/completions`
- **Deployment:** Any static host (GitHub Pages, Netlify, S3) or local file

---

## The 3-Step Chained Prompting Strategy

This is the core innovation — each API call builds on the previous, enabling **progressive AI reasoning** rather than a one-shot query.

### Step 1 — Profile Categorization
**Task:** Classify the user into structured metadata: `income_bracket` (BPL/LIG/MIG/HIG), `primary_demographic_groups`, `vulnerability_score` (1–10), and `key_needs`.

**Why:** ASI-1 creates structured metadata from unstructured profile data, priming the next call with enriched context.

### Step 2 — Eligibility Matching
**Task:** Compare the user profile + Step 1 categorization against all 40 schemes. Returns `eligibility_status`, `confidence_score`, `reason_qualified`, `priority`, and `estimated_benefit` for each.

**Why:** The categorization from Step 1 enriches reasoning. ASI-1 handles edge cases (e.g., "farmer with BPL card under 40 → eligible for both PM-KISAN and PMKMY").

### Step 3 — Action Plan
**Task:** From the top 5 matches, generate a personalized `greeting`, `top_priority_scheme`, `action_steps`, `important_documents`, and `encouragement` in the user's chosen language.

**Why:** Synthesizes everything into immediately actionable guidance, not just a list.

---

## All 40 Government Schemes

### Agriculture (8)
1. PM Kisan Samman Nidhi (PM-KISAN)
2. Kisan Credit Card (KCC)
3. PM Fasal Bima Yojana (PMFBY)
4. PM Krishi Sinchai Yojana (PMKSY)
5. e-National Agriculture Market (e-NAM)
6. Sub Mission on Agriculture Mechanization (SMAM)
7. PM Kisan Maandhan Yojana
8. Agricultural Technology Management Agency (ATMA)

### Women & Children (7)
9. Beti Bachao Beti Padhao (BBBP)
10. Sukanya Samriddhi Yojana (SSY)
11. Janani Suraksha Yojana (JSY)
12. PM Matru Vandana Yojana (PMMVY)
13. Integrated Child Development Services (ICDS)
14. National Creche Scheme
15. Mahila Shakti Kendra Scheme

### Education (6)
16. National Scholarship Portal (NSP)
17. PM Scholarship Scheme (PMSS)
18. Samagra Shiksha Abhiyan
19. Right to Education (RTE) — Free Admission
20. PM Special Scholarship Scheme (NE Students)
21. National Means-cum-Merit Scholarship Scheme (NMMSS)

### Health (6)
22. Ayushman Bharat PM Jan Arogya Yojana (PMJAY)
23. PM Suraksha Bima Yojana (PMSBY)
24. PM Jeevan Jyoti Bima Yojana (PMJJBY)
25. Janani Shishu Suraksha Karyakaram (JSSK)
26. Rashtriya Bal Swasthya Karyakaram (RBSK)
27. National Mental Health Programme (NMHP)

### Employment & Business (7)
28. Mahatma Gandhi NREGA (MGNREGA)
29. PM Mudra Yojana (PMMY)
30. Startup India
31. PM Employment Generation Programme (PMEGP)
32. National Apprenticeship Promotion Scheme (NAPS)
33. PM Kaushal Vikas Yojana (PMKVY)
34. Deendayal Antyodaya Yojana — NULM

### Housing (4)
35. PM Awas Yojana — Urban (PMAY-U)
36. PM Awas Yojana — Gramin (PMAY-G)
37. RERA — Real Estate Regulatory Authority
38. Interest Subsidy Scheme for Housing the Urban Poor (ISHUP)

### Senior Citizens & Disability (5)
39. Indira Gandhi National Old Age Pension Scheme (IGNOAPS)
40. Indira Gandhi National Widow Pension Scheme (IGNWPS)

### Financial Inclusion (3 bonus)
- PM Jan Dhan Yojana (PMJDY)
- Atal Pension Yojana (APY)
- Direct Benefit Transfer (DBT) Portal

---

## File Structure
```
scheme-sathi/
├── index.html       # Complete app (HTML + CSS + JS + Schemes + Translations)
├── thumbnail.png    # App preview image
├── thumbnail.html   # Thumbnail generator
└── README.md        # This file
```

---

## ASI:One API Integration
- **Endpoint:** `https://api.asi1.ai/v1/chat/completions`
- **Model:** `asi1-mini`
- **Calls per session:** 4 (3 for scheme matching + 1 for document checklist)
- **Format:** OpenAI-compatible JSON
- **Temperature:** 0.2 (for consistent, factual responses)

---

*Built for API Innovate 2026 · Powered by ASI:One*
