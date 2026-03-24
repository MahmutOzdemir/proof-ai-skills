# proof-ai-skills
Claude Skills for Proof AI Accelerator by Innovato Consultancy
# PROOF AI Skills

**Open-source Claude skills for pre-PMF AI-native founders.**

Built by [Innovato Consultancy](https://innovatoconsultancy.com) as part of the [PROOF AI Accelerator](https://www.proofaiaccelerator.com) methodology.

PROOF founders get access to 50+ of these skills across the full 10-week program. This repository contains the ones we're releasing publicly.

---

## What are Claude Skills?

Claude Skills are installable instruction sets that extend Claude's behaviour for a specific, repeatable task. Once installed, Claude applies them automatically when the context calls for it — no prompting required.

Think of them as methodology encoded into your AI copilot.

---

## Available Skills

### 🎙️ [Customer Interview Simulator](./customer-interview-simulator/)

Simulate realistic customer discovery interviews to pressure-test whether a problem is real, acute, and worth building on — before writing a line of code.

**What it does:**
- Takes your problem statement + ICP definition
- Generates 5 distinct customer personas scored on 6 key attributes (pain intensity, urgency, budget authority, problem awareness, tech adoption, workaround reliance)
- Simulates 5 full discovery interviews (5–10 questions each) using strict Mom Test principles
- Delivers a Problem Validation Signal Report with a scored verdict: proceed, reframe, or pivot

**Why it matters:**
Most discovery interviews are designed, unintentionally, to produce false confidence. This skill builds in structural skepticism — at least 2 of 5 personas are skeptics, pragmatists, or people who've already solved the problem. Because that's what reality looks like.

→ [Read the full skill documentation](./customer-interview-simulator/SKILL.md)

---

## How to Install a Skill

1. Go to [claude.ai](https://claude.ai) → your profile icon → **Settings**
2. Navigate to the **Skills** tab
3. Click **Upload skill** and upload the `.skill` file

Or clone this repo and follow the instructions in each skill's folder.

### Installing from source (for developers)

Each skill folder contains a `SKILL.md` and a `references/` directory. You can use these directly with the Claude API or package them into a `.skill` file for the Claude.ai interface.

```bash
git clone https://github.com/MahmutOzdemir/proof-ai-skills.git
cd proof-ai-skills
```

---

## Contributing

Found a bug? Have an improvement? Pull requests are welcome.

If you've tested a skill on a real problem and have signal on what works or what falls short — open an issue. Real-world feedback is how these get better.

---

## About PROOF

PROOF is a 10-week AI accelerator for technical founders who turn deep domain expertise into AI ventures. Zero equity upfront.

We compress months of venture building into weeks using a sprint methodology supported by custom AI copilots — of which these skills are a part.

→ [proofaiaccelerator.com](https://www.proofaiaccelerator.com)

---

## License

MIT © 2026 [Innovato Consultancy — PROOF AI Accelerator](https://www.proofaiaccelerator.com)
