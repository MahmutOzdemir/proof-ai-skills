---
name: eu-market-fit-evaluator
description: >
  Evaluate one or more startups (or product ideas) for EU market fit across three dimensions:
  problem urgency in the EU, solution innovativeness, and competitive whitespace in the EU market.
  Produces a scored, tiered analysis with investor- and customer-facing rationale for each startup.

  Use this skill whenever someone shares a list of startups and asks about EU fit, EU market
  opportunity, EU investor interest, or EU go-to-market readiness. Also trigger when a single
  startup description is shared alongside questions like "would this work in Europe?", "is there
  an EU market for this?", "which of these should we focus on for Europe?", "EU customer
  interest", "EU investor thesis", or "European market analysis". Always use this skill when
  the task is to rank or compare startups on EU market merit — even if phrased casually.
---

# EU Market Fit Evaluator

Evaluate startups against the EU market across three scored dimensions, then tier and
visualize the results with investor-grade rationale.

---

## Inputs

Accept any of:
- A list of startup descriptions (name + one-line summary)
- A single startup description
- A pitch deck summary or product overview
- A portfolio list with brief descriptions

If key information is missing (e.g., no sector context), make reasonable inferences and
flag assumptions — do not ask for clarification unless the input is too vague to score at all.

---

## Scoring Framework

Score each startup on **three dimensions**, each 1–5:

### 1. Problem Urgency in EU (1–5)
How acute and EU-specific is the problem this startup addresses?

| Score | Meaning |
|-------|---------|
| 5 | EU regulation or policy directly mandates this solution (e.g., GDPR, EU AI Act, CBAM, EPR, NIS2, EU Taxonomy) OR a structural EU market condition (e.g., offshore wind fleet, industrial energy costs) makes the problem uniquely severe here |
| 4 | Strong EU tailwind — regulation, demographic, or infrastructure reality makes the problem more acute in EU than globally |
| 3 | Problem exists in EU but is not EU-specific; similar urgency globally |
| 2 | Problem is less acute in EU than in other markets (e.g., US or Asia have stronger demand) |
| 1 | Problem is weak or largely irrelevant in EU context |

**Key EU regulatory anchors to check:**
- Data & AI: GDPR, ePrivacy Directive, EU AI Act, Schrems II, Data Act
- Environment: EU Taxonomy, CBAM (Carbon Border Adjustment), EPR (Extended Producer Responsibility), CSRD, EU ETS, Net Zero Industry Act, Critical Raw Materials Act
- Industrial: NIS2 (cybersecurity), DORA (financial resilience), EU Chips Act
- Health: European Medicines Agency, EU Rare Disease Strategy, European Reference Networks
- Mobility: 2035 ICE phase-out, Alternative Fuels Infrastructure Regulation (AFIR)
- Energy: REPowerEU, EU Hydrogen Strategy, Energy Efficiency Directive

### 2. Solution Innovativeness (1–5)
How novel is the approach relative to what exists globally and in the EU?

| Score | Meaning |
|-------|---------|
| 5 | Creates a new category or uses a fundamentally new technical approach (e.g., cryptographic proof of AI data deletion, swarm robotics for inspection) |
| 4 | Meaningfully differentiated — clear technical or methodological leap over incumbents |
| 3 | AI-native or modernized take on an established category; incremental but real improvement |
| 2 | Feature differentiation only; well-trodden category with many similar solutions |
| 1 | Commodity product; no meaningful differentiation |

### 3. Competitive Whitespace in EU (1–5)
How much room exists in the EU market — are incumbents weak or absent?

| Score | Meaning |
|-------|---------|
| 5 | No direct EU competitor; global leaders haven't localized; regulatory moat blocks US SaaS entry |
| 4 | Few credible competitors; EU customers actively seeking alternatives to US vendors (data sovereignty, compliance) |
| 3 | Some established players but room for a focused entrant, especially with EU-native compliance positioning |
| 2 | Competitive market; requires a very sharp wedge to gain traction |
| 1 | Dominated by global incumbents with deep EU presence; almost no whitespace |

**EU whitespace accelerators** (factors that create whitespace even in crowded categories):
- GDPR/Schrems II makes US SaaS legally risky → EU-native alternative has structural advantage
- EU language/localization requirements disadvantage US-first products
- EU public procurement preference for European vendors
- Deep tech categories where EU has no strong local champion (unlike US or Israel)

---

## Total Score & Tiers

Sum the three dimension scores (max 15):

| Tier | Score | Label |
|------|-------|-------|
| S | 13–15 | Strong EU fit — prioritize for EU go-to-market |
| A | 10–12 | Solid EU potential — needs positioning work |
| B | 7–9 | Niche or crowded — enter EU only with a sharp wedge |
| C | ≤6 | Weak EU fit — focus on other markets first |

---

## Output Format

### For a list of startups (3+):
Produce an **interactive visual** using the `visualize:show_widget` tool (HTML artifact).

Structure:
1. Tiered card grid (Tier S → A → B → C)
2. Each card shows: startup name, total score (color-coded by tier), three dimension bars (Problem / Novelty / Whitespace), and a 1–2 sentence rationale
3. Color coding: Tier S = teal (#1D9E75), Tier A = blue (#378ADD), Tier B/C = gray (#888780)
4. After the visual, provide a prose summary covering:
   - The top 2–3 picks and why
   - The single strongest EU investor angle (regulatory tailwind, structural market condition, or whitespace)
   - 1–2 warnings about highly-scored startups that still face real barriers

### For a single startup:
Produce a structured text analysis:
- Score table (three dimensions + total)
- Tier and label
- 3–4 paragraphs: EU problem fit, competitive landscape, investor angle, key risks
- Recommended first EU beachhead (country or sector)

---

## Scoring Heuristics & Edge Cases

**SaaS vs. deep tech**: Deep tech (hardware, materials, robotics, biotech) scores higher on whitespace in EU because US SaaS dominates software categories. Adjust whitespace scores accordingly.

**B2B vs. B2C**: B2B startups generally score higher on EU problem urgency because EU regulation primarily targets enterprises. B2C mental health, consumer apps, etc. score lower unless there is a clear employer/institutional channel.

**"Regulation creates the market" test**: If a specific EU law passed in the last 5 years directly mandates or financially incentivizes what this startup does, add +1 to Problem Urgency (max 5). This is the strongest possible EU investor signal.

**Data sovereignty bonus**: If the startup handles sensitive data (health, financial, enterprise, government) and operates from within the EU, add +1 to Competitive Whitespace (max 5) — EU customers are actively seeking alternatives to US hyperscalers for GDPR/Schrems II compliance.

**Do not penalize Turkish/non-EU origin**: Being founded outside the EU is not a market fit penalty. Score purely on whether the problem, solution, and competitive position fit the EU market, regardless of founder location.

---

## Investor Framing Addendum

After scoring, always add a brief section on **EU investor thesis angles** for the top-tier startups:

- **Regulatory capture**: The EU mandate is creating the market (strongest thesis)
- **Infrastructure gap**: EU has unique physical infrastructure that creates demand (offshore wind, industrial base, rail network)
- **Data sovereignty**: EU enterprises will pay a premium for non-US alternatives
- **Deep tech leadership**: EU is building strategic autonomy in semiconductors, robotics, clean energy — local champions get policy and procurement support
- **Circular economy**: EU EPR and sustainability mandates create compliance-driven revenue floors

Flag which angle applies to each Tier S and A startup.
