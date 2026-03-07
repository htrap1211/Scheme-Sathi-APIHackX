# Scheme Sathi 🇮🇳
### AI-Powered Government Scheme Matcher for Indian Citizens

> **Hackathon Project** — Built with ASI-1 Mini API
> Helps Indian citizens discover government welfare schemes they qualify for in seconds.

---

## What It Does

A citizen fills a 12-field profile form → the app makes **3 chained calls to ASI-1 API** → returns personalized government schemes they qualify for, with eligibility reasoning, estimated benefits, and a step-by-step action plan.

---

## Screenshots

| Form | Loading | Results |
|------|---------|---------|
| *(Profile form with tricolor design)* | *(3-step animated progress)* | *(AI-matched scheme cards)* |

---

## Setup Instructions

### 1. Get Your ASI-1 API Key
- Obtain your API key from the ASI-1 platform
- No registration needed beyond your API key

### 2. Open the App
- Simply open `index.html` in any modern browser — **no build step, no server needed**
- The app is a single self-contained HTML file

### 3. Add Your API Key
- Click the **⚙️ gear icon** in the top-right header
- Paste your ASI-1 API key in the modal
- Click **Save Key**
- The key is stored in memory only (cleared on page refresh — by design for security)

### 4. Use the App
1. Fill in your profile (age, income, occupation, caste, state, etc.)
2. Click **"Find My Schemes →"**
3. Watch the 3-step AI analysis run
4. Browse your personalized scheme matches and action plan

---

## The 3-Step Prompting Strategy (Core Innovation)

This is what makes Scheme Sathi different from a simple rule-based filter. Each step builds on the previous, enabling **progressive AI reasoning**:

### Step 1 — Profile Categorization
**System:** Expert in Indian government welfare schemes
**Task:** Classify the user into `income_bracket` (BPL/LIG/MIG/HIG), `primary_demographic_groups` (rural-farmer, woman, student, etc.), `vulnerability_score` (1-10), and `key_needs` (housing, health, education, etc.)

**Why this works:** ASI-1 creates structured metadata from unstructured profile data, which primes subsequent reasoning.

### Step 2 — Eligibility Matching
**System:** Precise scheme eligibility expert
**Task:** Compare the user profile + Step 1 categorization against all 40 schemes. For each: `eligibility_status`, `confidence_score`, `reason_qualified`, `priority`, `estimated_benefit`

**Why this works:** The categorization from Step 1 enriches the context. ASI-1 reasons about edge cases (e.g., "farmer with BPL card under 40 → eligible for both PM-KISAN and PMKMY").

### Step 3 — Action Plan
**System:** Friendly, warm government scheme advisor
**Task:** From the top 5 matches, generate a personalized `greeting`, `top_priority_scheme`, `action_steps`, `important_documents`, and `encouragement` — in the user's chosen language (English or Hindi)

**Why this works:** The final call synthesizes everything into actionable guidance rather than just a list, making the output immediately useful to citizens.

---

## All 40 Government Schemes Covered

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

## Tech Stack
- **Frontend:** Vanilla HTML/CSS/JavaScript — zero frameworks, zero build tools
- **AI Backend:** ASI-1 Mini via REST API (OpenAI-compatible format)
- **Design:** Mobile-first, Indian tricolor theme (saffron/white/green)
- **Deployment:** Any static host (GitHub Pages, Netlify, S3) or local file

---

## File Structure
```
scheme-sathi/
├── index.html       # Complete app (HTML + CSS + JS + Schemes + Translations)
├── .env.example     # API key reference (key entered via UI, not file)
└── README.md        # This file
```

---

## ASI-1 API Integration
- **Endpoint:** `https://api.asi1.ai/v1/chat/completions`
- **Model:** `asi1-mini`
- **Auth:** Bearer token (entered via in-app settings modal)
- **Format:** OpenAI-compatible JSON

---

*Powered by ASI-1 Mini | Built for the ASI-1 API Hackathon 2026*
