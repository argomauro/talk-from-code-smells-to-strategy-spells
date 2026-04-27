# `/refactor-interview`

> **Purpose:** Asks the right context questions before refactoring — determines which level to apply and prevents over-engineering.

---

## Pre-Refactoring Interview

Before analyzing any code, guide the developer through these questions. The goal is to understand the real context and choose the right refactoring level.

Present these questions **one at a time** and wait for the answer before proceeding.

---

## Questions to Ask

### About the team and codebase

| # | Question |
|---|----------|
| 1 | How many people regularly work on this file? |
| 2 | Is this code in production or still under development? |

### About logic stability

| # | Question |
|---|----------|
| 3 | Will the conditions or cases in this code change in the future? *(e.g., new channels, new discount types)* |
| 4 | Is this logic already duplicated in other files in the project? |

### About technical requirements

| # | Question |
|---|----------|
| 5 | Do you need to test this logic in isolation (unit test per function)? |
| 6 | Are there non-functional requirements that affect the structure? *(multi-currency, multi-tenant, etc.)* |

---

## Interpreting the Answers

After receiving the answers, conclude with a clear recommendation:

| Condition | Recommended level |
|-----------|-------------------|
| Small team (≤3) + stable logic + not duplicated | **L1 only** (cosmetic) |
| Duplicated 3+ times or hard to test in isolation | **L2** (structural) |
| Large team or unstable logic or strong separation needed | **L3** (architectural) |

---

## Expected Output

At the end of the interview, produce a report with:

```
Recommended level: L1 / L2 / L3
Justification: [2 lines]

Patterns NOT to apply in this context:
  - [Pattern] → [Reason]
  - ...

Next step: use /refactor-analyze for the technical analysis.
```

---

> **Next command:** [`/refactor-analyze`](./refactor-analyze.md)
