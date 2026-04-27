# `/refactor-execute`

> **Purpose:** Executes refactoring at the specified level (L1/L2/L3) respecting the context constraints from the interview.  
> **Prerequisite:** use after [`/refactor-analyze`](./refactor-analyze.md).

---

## Refactoring Execution

Execute the refactoring of the current file at the level specified by the user. Before modifying anything, verify that a test suite exists and is green.

## Required Input

Specify the level: **L1**, **L2**, or **L3**.

---

### Level L1 — Cosmetic

Apply only:
- Rename variables/parameters with unclear names.
- Extract magic numbers and magic strings as named constants.
- Align style (casing, spacing, consistency).

**Do NOT:** add new classes, new methods, or restructure any logic.  
**Verify:** the diff must contain only renames and new constants. Zero logic changed.

---

### Level L2 — Structural

Apply only (in addition to L1):
- Extract private methods for repeated logic blocks.
- Break long methods (> 20 lines) into named sub-functions.
- Turn the main method into a readable dispatcher.

**Do NOT:** add new classes, GoF patterns, interfaces, or ABC.  
**Verify:** each extracted method must be independently testable.

---

### Level L3 — Architectural

Apply only the patterns justified by the interview (in addition to L1+L2):

#### Always apply if justified

| Pattern | Condition |
|---------|-----------|
| Extract `@dataclass` | Data Clumps: 3+ fields that always travel together |
| Extract function | Logic duplicated 3+ times *(not Strategy, just a function)* |

#### Apply only if the context requires it

| Pattern | Condition |
|---------|-----------|
| Extract a service class | Feature Envy — only if the separation makes sense for the team |
| Strategy pattern | Only if the logic has concrete, already-known stable variants |

#### Never apply without an interview

- Repository, Money class, ABC, plugin registry.

> **Definite constraint:** For every pattern introduced, write a comment in the code.

---

## Execution Process

```
1. Show a plan in 3–5 steps with a risk estimate for each.
2. Wait for confirmation before proceeding.
3. Execute step by step, showing the diff after each step.
4. After each step: "Are tests still green? Proceeding to the next step?"
5. At the end: run tests + summary of changes applied.
```

---

## Final Check

At the end of refactoring:

- [ ] Behavior is identical (tests green)
- [ ] No pattern introduced without justification from interview
- [ ] The code is more readable, not just "more patterns"
- [ ] A new developer understands the code faster than before

---

> **Full flow:** `/refactor-interview` → `/refactor-analyze` → `/refactor-execute`
