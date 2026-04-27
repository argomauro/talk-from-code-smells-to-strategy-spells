# From Code Smells to Strategy Spells
### A Human-Guided AI Refactoring Framework

> **"AI can write your code. It can refactor your architecture. But it doesn't know your context."**

This repository contains all the materials for the talk **"From Code Smells to Strategy Spells"** — a conference presentation introducing the **Interview-Analyze-Execute (IAE)** methodology: a structured workflow for using AI to refactor code without over-engineering it.

---

## The Core Problem

AI coding assistants are fast, pattern-aware, and technically correct. They also have no idea whether your logic is stable, your team is small, or your codebase is in production. Left unconstrained, they solve a 2-condition problem with 6 design patterns and 300 lines of code.

The IAE methodology fixes this by making **human context a prerequisite** for any technical action.

---

## The Methodology: Interview → Analyze → Execute

### Phase 1 — `/refactor-interview` · *Inject Context*
Before touching a single line of code, the AI is forced to ask the right questions: team size, production status, logic stability, duplication, testing requirements. The answers determine the **refactoring level** (L1, L2, or L3) and lock in a list of patterns to explicitly avoid.

→ [`prompts/refactor-interview.md`](prompts/refactor-interview.md)

---

### Phase 2 — `/refactor-analyze` · *Map the Debt*
With context established, the AI scans the code and produces a structured smell table — categorized by level, scored by impact (1–3), and with explicit dependency mapping between smells. No guessing. No linting-as-diagnosis.

→ [`prompts/refactor-analyze.md`](prompts/refactor-analyze.md)

---

### Phase 3 — `/refactor-execute` · *Constrained Execution*
The AI proposes a 3–5 step plan with risk estimates per step. The human approves. Then the AI executes one step at a time, showing a diff and waiting for test confirmation before proceeding. No black box. No surprises.

→ [`prompts/refactor-execute.md`](prompts/refactor-execute.md)

---

## The Three Refactoring Levels

| Level | Name | When to apply | What it changes |
|-------|------|---------------|-----------------|
| **L1** | Cosmetic | Always safe | Renames, constants, style |
| **L2** | Structural | Logic duplicated or hard to test | Extract methods, decompose long functions |
| **L3** | Architectural | Large team, volatile logic, scaling needs | Service classes, Strategy pattern (only if justified) |

> **The golden rule:** no pattern is introduced at L3 without an explicit justification from the interview phase.

---

## Talk Materials

| File | Description |
|------|-------------|
| [`Presentation_Full.pdf`](Presentation_Full.pdf) | Full slide deck (54 slides, comic-style) |
| [`Strategic_Framework_for_Context-Driven_Refactoring.md`](Strategic_Framework_for_Context-Driven_Refactoring.md) | Complete written framework with decision matrix, IDE integration guide, and team deployment notes |
| [`prompts/refactor-interview.md`](prompts/refactor-interview.md) | Prompt: Pre-flight interview |
| [`prompts/refactor-analyze.md`](prompts/refactor-analyze.md) | Prompt: Smell analysis |
| [`prompts/refactor-execute.md`](prompts/refactor-execute.md) | Prompt: Controlled execution |

---

## How to Use These Prompts

The three prompt files are designed to be used as **custom instructions** or **slash commands** in any AI coding assistant (Cursor, GitHub Copilot, Windsurf, etc.):

1. Save the files in your project under `.github/prompts/` or `.cursorrules`
2. Instruct your AI: *"You are a Context-Driven Refactoring Consultant. Never suggest code changes before completing `/refactor-interview` and `/refactor-analyze`."*
3. Run `/refactor-interview` at the start of every refactoring session
4. Let the output of each phase feed the next

---

## The Case That Started It All

On **August 1, 2012**, Knight Capital deployed a trading update without removing deprecated code. A reused routing flag activated an 8-year-old dormant algorithm. In 45 minutes, **$440 million evaporated** — roughly $10M per minute.

Two code smells caused it: an **L1 cosmetic smell** (reused variable flag, unclear naming) and an **L3 architectural smell** (dead logic left loaded in production). Neither would have survived a structured review.

---

## About the Speaker

**Maurizio Argoneto** — CTO @ Publisys Spa · AWS Community Hero  
*"I use technology to solve problems, but I let humans make the strategy."*

---

## License

Content released for community use. Prompts are free to adapt for your team's stack and conventions — just update the L3 exclusion constraints to match your language and patterns.
