# Founder-Market Fit Skill

**A Claude skill by [Innovato Consultancy](https://www.innovatoconsultancy.com) — part of the [PROOF AI Accelerator](https://proofaiaccelerator.com) skill library.**

---

## What it does

This skill reverse-engineers a person's strongest **AI-native SaaS go-to-market opportunity** from their LinkedIn profile and/or CV.

Given a professional background, it:

1. Runs a **brief discovery dialogue** (2 questions) to understand constraints and preferences
2. Silently extracts **skills, experience signals, network capital, and unfair advantages**
3. Web-searches **live market data** to ground insights in current trends and competitor funding
4. Scores **5 GTM opportunity candidates** on Impact, Urgency, and Feasibility
5. Delivers **full deep-dive analyses** on the Top 2, including:
   - Ideal Customer Profile (ICP)
   - Founder-to-investor Problem Statement
   - 3-layer Value Proposition
   - VC-grade Competitor Matrix (positioning, features, funding, moat, whitespace)
   - Wedge-first Entry Point Recommendation

---

## When to use it

- You have a LinkedIn profile or CV and want startup direction
- You want to know what pain points your background uniquely qualifies you to solve
- You're entering a new market and want to validate founder-market fit
- Phrases like: *"what should I build?"*, *"what's my best GTM opportunity?"*, *"turn my expertise into a product"*, *"is my background fundable?"*

---

## Installation

1. Download `founder-market-fit.skill`
2. In Claude.ai, go to **Settings → Skills**
3. Click **Install from file** and select the `.skill` file

---

## Example inputs

- Paste your LinkedIn **About + Experience** sections directly into chat
- Upload your **CV as a PDF**
- Or both — the skill handles mixed input gracefully

---

## Output format

A structured memo covering:

```
Profile Analysis (internal)
↓
5 GTM Opportunity Candidates (scored table)
↓
Top 2 Deep Dives:
  - ICP Table
  - Problem Statement
  - Value Proposition (3 layers)
  - Competitor Matrix (VC-grade)
  - Entry Point Recommendation
```

---

## Part of the PROOF AI Accelerator Skill Library

This skill is one of a growing collection of Claude skills built for pre-PMF AI-native founders, published open-source by Innovato Consultancy.

Other skills in the library:
- `icp-architect` — Define and stress-test your Ideal Customer Profile
- `outreach-forge` — Generate cold outreach sequences from trigger events
- `discovery-coach` — Pre-call prep and post-call debrief
- `demo-playbook-builder` — Build discovery-anchored demo narratives
- `objection-decoder` — Classify and respond to sales objections (ACAC framework)
- `pipeline-pulse` — Weekly deal review and forecast
- `frustration-archaeology` — Ideation from professional pain
- `kano-roadmap` — Feature prioritisation using Kano model
- `customer-interview-simulator` — Simulate discovery interviews for problem validation

→ Full library: [github.com/MahmutOzdemir/proof-ai-skills](https://github.com/MahmutOzdemir/proof-ai-skills)

---

## License

MIT License — Copyright (c) 2025 Innovato Consultancy, Breskens, Netherlands.

See [LICENSE](./LICENSE) for full terms.
