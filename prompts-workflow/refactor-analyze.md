# `/refactor-analyze`

> **Purpose:** Analyzes the open file, categorizes smells by level (L1/L2/L3), and estimates impact.  
> **Prerequisite:** use after [`/refactor-interview`](./refactor-interview.md).

---

## Smell Analysis by Level

Analyze the current file in the editor context. For each smell found:
- Categorize it by level
- Assess impact and priority

### Required Table Format

| Smell | Level | Line/Method | Impact (1-3) | Notes |
|-------|-------|-------------|--------------|-------|
| Magic number 160 | L1 | line 16 | 1 | Replace with `SMS_CHAR_LIMIT` |
| Unclear parameter `u` | L1 | line 7 | 1 | Rename to `user` |
| Structural duplication | L2 | `send()` method | 2 | Branches repeat the same pattern |
| God Class | L3 | entire class | 3 | Does 5 different things |

### Impact Scale

| Value | Meaning |
|-------|---------|
| **1** | Cosmetic — no effect on maintainability |
| **2** | Hinders comprehension or testing |
| **3** | Blocks extension, causes future bugs |

---

## Smell Dependencies

Identify smells that depend on each other before being resolved:

```
e.g., "The God Class makes it impossible to resolve the Feature Envy
       without first separating responsibilities."

e.g., "The duplication is not worth fixing before extracting the constants."
```

---

## Final Recommendation

Based on the analysis and interview answers (`/refactor-interview`):

- **Smells to fix immediately (L1):** list with specific fix.
- **Smells to fix if tests allow (L2):** list with approach.
- **Smells to address carefully (L3):** list with suggested pattern + condition.
- **Smells to ignore:** what is NOT worth changing and why.

---

> **Next command:** [`/refactor-execute`](./refactor-execute.md) — specify the chosen level.  
> e.g., *"Ready to proceed? Use `/refactor-execute` and tell me: level L2"*
