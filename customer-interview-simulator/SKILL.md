---
name: customer-interview-simulator
description: >
  Simulate realistic customer discovery interviews for problem validation. Takes a problem statement and ICP (Ideal Customer Profile) from a pre-PMF founder and generates 5 diverse persona profiles scored on key ICP attributes, then simulates 5 full discovery interviews (5–10 questions each) to assess whether the problem is real, acute, and worth building on. Use this skill whenever a founder wants to validate a problem, test their ICP assumptions, simulate customer discovery, run a Mom Test-style interview, check if a problem is worth solving, or says anything like "validate my idea", "is this a real problem", "who would buy this", "simulate customer interviews", "test my hypothesis", "discovery interviews", "problem validation", or "who has this pain". Always use this skill when a founder describes a startup idea and wants to know if the problem is real before building. Designed for pre-PMF AI-native startups.
---

# Customer Interview Simulator

Simulate a realistic, unbiased set of customer discovery interviews to pressure-test whether a problem is real, acute, and worth building on — before writing a line of code.

This skill produces:
1. **5 ICP persona profiles** scored on 6 key attributes (realistic spread — not all believers)
2. **5 simulated discovery interviews** (5–10 Q&A each) conducted in the spirit of the Mom Test
3. **A problem validation signal report** with evidence for/against, patterns, and next steps

Designed for **pre-PMF founders** of AI-native startups who need honest signal, not confirmation.

---

## ⚠️ Anti-Confirmation Bias Mandate

This skill's most important job is to **resist the founder's natural optimism**. You are not here to validate — you are here to stress-test.

Rules that cannot be broken:
- At least **2 of 5 personas must be skeptics or non-believers** — they either don't have the problem, have a workable alternative, or don't rate it as a priority
- Interviews must ask about **past behavior and current reality**, never future hypotheticals ("would you use...?" is forbidden)
- Personas must **occasionally redirect, give vague answers, or reveal that the problem isn't as acute as the founder assumed**
- The synthesis report must give an **honest signal score** — if the evidence is weak, say so clearly, even if some interviews were positive

If the founder's problem statement is vague or the ICP is too broad, flag it before running the simulation and ask for clarification. A sharp input produces useful signal; a fuzzy input produces noise.

---

## Phase 0: Parse & Sharpen Inputs

Extract from the founder's message:
- **Problem statement**: What specific pain does this product solve? For whom?
- **ICP definition**: Who exactly is the target customer? (role, company type, size, context)
- **Stage**: How early is the founder? (idea / prototype / waitlist / early users)

If any of these are missing or too vague, ask before proceeding. Use this framing:

> "Before I run the simulation, I need to sharpen two things: (1) Your problem in one sentence — what does [customer] struggle to do today, and why does that cost them? (2) Your ICP — give me a specific role and context, not just an industry."

**ICP sharpening examples:**
- Too broad: "marketing teams" → Sharpen to: "demand gen managers at B2B SaaS companies with 50–200 employees running paid campaigns"
- Too broad: "small businesses" → Sharpen to: "solo e-commerce operators on Shopify doing $10K–$100K/year in revenue"

Once inputs are sharp, confirm them back to the founder before generating personas:
> "Running the simulation with: **Problem:** [X] | **ICP:** [Y]. Proceeding."

---

## Phase 1: Generate 5 ICP Personas

Create 5 distinct personas who all technically fit the ICP definition but differ meaningfully in how they experience (or don't experience) the problem.

### The 6 ICP Scoring Attributes

Score each persona on these dimensions (1–5 scale):

| Attribute | What it measures | 1 = | 5 = |
|---|---|---|---|
| **Pain Intensity** | How much does this problem hurt them day-to-day? | Minor nuisance, easy to ignore | Actively blocking key work, causes real loss |
| **Problem Awareness** | Do they know they have this problem? | Unaware — they've normalized it | Fully aware, actively looking for a solution |
| **Urgency** | How soon do they need this solved? | No pressure to solve it | Already losing time/money/deals because of it |
| **Budget Authority** | Can they buy or approve a purchase? | No influence — someone else decides | Full autonomy to buy tools under a threshold |
| **Tech Adoption** | Are they early adopters or cautious? | Wait-and-see; needs proven ROI | Eager to try new AI tools; low friction to adopt |
| **Workaround Reliance** | How entrenched is their current solution? | No workaround — they're just stuck | Deep workaround (spreadsheets, manual process, duct-taped stack) they're invested in |

### Persona Spread Rules

The 5 personas must represent a realistic **bell curve of belief**, not a stack of champions:

| Persona | Archetype | Expected profile |
|---|---|---|
| 1 | **The Power User** | High pain, high awareness, high urgency. Actively searching. |
| 2 | **The Pragmatist** | Moderate pain, workaround in place. Will buy if ROI is clear. |
| 3 | **The Skeptic** | Fits ICP but low pain intensity. Doesn't see the problem as acute. |
| 4 | **The Unaware** | Has the problem but hasn't named it. Normalized it as "just how it works." |
| 5 | **The Solved** | Had the problem, built or bought their own solution. Won't switch easily. |

### Persona Output Format

For each persona, output:

```
### Persona [N]: [First name, job title, company type]

**Background:** [2–3 sentences: their role, company context, relevant workflow]

| Attribute | Score | Evidence |
|---|---|---|
| Pain Intensity | [1–5] | [One sentence grounding the score in their specific context] |
| Problem Awareness | [1–5] | [...] |
| Urgency | [1–5] | [...] |
| Budget Authority | [1–5] | [...] |
| Tech Adoption | [1–5] | [...] |
| Workaround Reliance | [1–5] | [...] |

**Overall ICP Fit Score:** [Average of 6 attributes, 1 decimal] / 5
**Predicted Interview Stance:** [Champion / Interested but cautious / Skeptical / Unaware / Resistant]
```

---

## Phase 2: Simulate the Interviews

Simulate one discovery interview per persona. Each interview is a realistic back-and-forth between the founder (asking questions) and the persona (answering in character).

### Interview Principles (Mom Test Rules)

These rules govern every question asked:

1. **Ask about the past, not the future.** "Walk me through the last time you had to do X" not "Would you use a tool that..."
2. **Ask about their life, not your idea.** Don't mention the product until the final question (if at all).
3. **Dig into specifics.** "How do you handle that today?" → "How long does that take?" → "What did you try before that?"
4. **Let silence work.** If a persona is vague, follow up — don't accept "it's a bit annoying" without probing what "annoying" means in time, money, or frequency.
5. **Never lead.** "That must be really frustrating, right?" is a bad question. "How do you feel about that?" is better.
6. **Listen for the three gold signals:** (a) unprompted mention of the problem, (b) money already being spent on a workaround, (c) emotion (frustration, embarrassment, relief) when describing the situation.

### Question Bank

Pull questions from these categories (read `references/question-bank.md` for the full bank):
- **Context-setting**: Role, workflow, tools, team structure
- **Problem probing**: Last time X happened, frequency, impact, cost
- **Workaround mapping**: What they do today, how that's working, what's broken about it
- **Priority calibration**: Where this sits vs. other problems they're trying to solve
- **Buying behavior**: How they've bought tools before, who approves, what they've tried

### Interview Output Format

```
---
## Interview [N]: [Persona Name] — [Archetype]
**Setting:** [One sentence: e.g., "30-min Zoom call, mid-afternoon. She's between meetings."]

**Q1 [Context]:** [Question]
> **[Persona name]:** [Realistic answer in character — 2–5 sentences. Include hesitations, redirects, and natural speech patterns. Not every answer is a gift.]

**Q2 [Problem probe]:** [Question]
> **[Persona name]:** [Answer]

[... 5–10 questions total, mix of categories ...]

**🔍 Interview Signal:** [1 paragraph: What did this interview reveal? What was notable — positive or negative? Any surprises?]
**Signal Strength:** [Strong positive / Moderate positive / Neutral / Weak / Negative]
---
```

**Character fidelity rules per archetype:**
- **Power User**: Volunteers specifics, gets animated, may finish your sentences. Asks "when can I try it?"
- **Pragmatist**: Measured, asks about integrations and pricing, needs to see ROI before committing
- **Skeptic**: Polite but unconvinced. Short answers. "I mean, it's fine. We manage." Won't volunteer pain.
- **Unaware**: Describes workarounds as normal. Doesn't frame the problem as a problem — it's just "how we do things."
- **Solved**: Articulate about the problem (they've thought about it), but has conviction in their current solution. Hard to move.

---

## Phase 3: Problem Validation Signal Report

After all 5 interviews, synthesize findings into an honest assessment.

**Report structure — use exactly:**

```
# Problem Validation Report
**Problem tested:** [One sentence]
**ICP tested:** [One sentence]
**Interviews completed:** 5

---

## Signal Score: [X] / 10
[One sentence verdict: e.g., "Moderate signal — the problem is real for a subset of the ICP, but urgency and willingness to abandon current workarounds is low."]

### Score Breakdown
| Signal Dimension | Score | Evidence |
|---|---|---|
| Problem is real (people actually have it) | [1–10] | [Key evidence from interviews] |
| Problem is painful (causes real cost/loss) | [1–10] | [...] |
| Problem is frequent (happens regularly) | [1–10] | [...] |
| Problem is unsolved (no good alternative) | [1–10] | [...] |
| Willingness to pay / change behavior | [1–10] | [...] |

---

## What the Interviews Told Us

### ✅ Evidence FOR the Problem Being Real
- [Bullet: specific quote or behavior from an interview that validates]
- [...]

### ❌ Evidence AGAINST (or Complicating Factors)
- [Bullet: specific signal that weakens the problem hypothesis]
- [...]

### ⚡ Unexpected Findings
- [Things that came up that the founder didn't anticipate — new angles, adjacent pains, segment surprises]

---

## ICP Assessment
[1–2 paragraphs: Did the ICP definition hold up? Were some sub-segments stronger than others? Should the founder narrow, expand, or pivot the ICP?]

---

## Verdict
[One of three verdicts, stated clearly:]

🟢 **Strong signal — proceed to solution discovery**
> The problem is real, acute, and largely unsolved for your ICP. At least 3 of 5 personas showed strong evidence. Move to solution interviews.

🟡 **Partial signal — reframe and re-test**
> The problem exists but urgency, frequency, or willingness to switch is insufficient. Recommend narrowing the ICP to the 1–2 personas who showed strongest signal, then re-running.

🔴 **Weak signal — pivot before building**
> Fewer than 2 personas showed genuine, unprompted pain. Either the problem is too mild, the ICP is wrong, or the timing is off. Do not proceed to solution design without further discovery.

---

## Next 3 Actions
1. [Specific: e.g., "Run 5 real interviews with [sub-segment] — focus on [specific question that needs more signal]"]
2. [Specific: e.g., "Reframe the problem from [X] to [Y] based on what personas actually described as painful"]
3. [Specific: e.g., "Test whether [unexpected finding] is a bigger pain than the original hypothesis"]
```

---

## Tone & Realism Standards

- Personas must feel like **real people**, not product marketing archetypes. Give them opinions, habits, and blind spots.
- Interviews must include **at least one moment per interview where the persona is vague, redirects, or gives a non-answer** — that's realistic and diagnostic.
- The synthesis must **name uncomfortable truths**. If the signal is weak, don't bury it in caveats.
- If the founder's problem statement reveals a **solution disguised as a problem** (e.g., "people need my AI tool"), reframe it before running — the interviews should probe the underlying pain, not the proposed solution.

---

## Reference Files

- `references/question-bank.md` — Full categorized bank of discovery questions by interview phase
- `references/persona-archetypes.md` — Deep character guides for each of the 5 archetypes to ensure consistent, realistic behavior across different domains
