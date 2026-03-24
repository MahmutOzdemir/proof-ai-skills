# Customer Interview Simulator

A Claude skill that simulates realistic customer discovery interviews to validate whether a problem is real, acute, and worth building on — before writing a line of code.

Part of the [PROOF AI Accelerator](https://www.proofaiaccelerator.com) methodology.

---

## The Problem It Solves

Finding the right people to interview takes weeks you don't have. When you do get in the room, people are polite — they tell you what you want to hear. And without realising it, founders lead the witness. "That must be really frustrating, right?" is not a discovery question. It's a confirmation trap.

This skill is built to remove those failure modes.

---

## What It Produces

Given a problem statement and ICP definition, the skill outputs:

**1. Five ICP Persona Profiles**
Each persona fits your ICP but differs meaningfully in how they experience the problem. Scored on 6 attributes: pain intensity, problem awareness, urgency, budget authority, tech adoption, and workaround reliance. The spread is intentional — not all believers.

| Persona | Archetype |
|---|---|
| 1 | The Power User — high pain, actively searching |
| 2 | The Pragmatist — workaround in place, needs ROI |
| 3 | The Skeptic — fits ICP, doesn't see the problem as acute |
| 4 | The Unaware — has the problem, hasn't named it |
| 5 | The Solved — built or bought their own solution |

**2. Five Simulated Discovery Interviews**
5–10 questions each, all conducted on Mom Test principles. Questions ask about past behaviour and current reality — never future hypotheticals. At least one persona per interview redirects, gives a vague answer, or reveals the problem is less acute than assumed.

**3. A Problem Validation Signal Report**
- Signal score out of 10 across 5 dimensions
- Evidence for and against the problem hypothesis
- Unexpected findings and adjacent pain signals
- ICP assessment — did the definition hold up?
- A clear verdict: 🟢 proceed / 🟡 reframe / 🔴 pivot
- Three specific next actions

---

## File Structure

```
customer-interview-simulator/
├── SKILL.md                        ← core skill instructions
└── references/
    ├── question-bank.md            ← categorised discovery question library
    └── persona-archetypes.md       ← character guides for all 5 archetypes
```

---

## How to Install

### Option 1: Claude.ai Skills UI
Download `customer-interview-simulator.skill` from the [releases page](https://github.com/MahmutOzdemir/proof-ai-skills/releases) and upload it via **Claude Settings → Skills → Upload skill**.

### Option 2: Use the source directly
Clone this repo and point Claude at the `SKILL.md` file using the Claude API or your preferred Claude integration.

---

## How to Use

Once installed, just describe your startup problem and ICP in plain language:

> "I'm building [product] for [customer]. The problem is [pain]. Validate whether this is real."

The skill activates automatically and runs the full simulation.

---

## Example Input

> "Problem: Early-stage B2B SaaS founders spend 3–4 weeks scheduling and running customer discovery interviews, often getting socially polite answers rather than honest signal. ICP: Technical co-founders at pre-PMF B2B SaaS startups, 1–3 person teams, no dedicated sales or research function."

---

## Contributing & Feedback

If you've run this on a real problem — open an issue and share what you found. Did it surface honest signal or just confirm what you already believed? Where did it fall short?

This gets better with real-world testing. That's the whole point.

---

## License

MIT © 2026 [Innovato Consultancy — PROOF AI Accelerator](https://www.proofaiaccelerator.com)
