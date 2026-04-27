# Strategic Framework for Context-Driven Refactoring

## The Interview-Analyze-Execute (IAE) Methodology

### 1\. Introduction: Refactoring as Strategic Asset Management

Refactoring is not an aesthetic pursuit; it is a maneuver in financial and technical risk management. Treating code in isolation from business goals leads to **over-engineering**: technically flawless but economically unsustainable architectures that increase maintenance costs through unnecessary abstractions.

The inherent limit of current AI models is their **syntactic nature**. AI excels at identifying formal patterns but fails to evaluate business stability, team topology, or product lifecycles. The **Interview-Analyze-Execute (IAE)** workflow bridges this gap by positioning human context as a prerequisite for technical execution.

### 2\. Phase I: Refactoring Interview – Extracting Invisible Context

The interview phase acts as a critical filter, determining the scope of intervention before a single line of code is touched.

**The Consultant/AI must ask the following questions and await specific answers:**

#### Impact & Lifecycle:

1.  **Team Velocity**: How many developers work on this file regularly?
    
2.  **Lifecycle Stage**: Is this code in production, a prototype, or a legacy system in sunset?
    
3.  **Testing Requirements**: Is isolation (unit testing) mandatory for this specific logic?
    

#### Technical Stability:

4.  **Volatility**: Are the business rules (e.g., tax logic, discount types) expected to change soon?
    
5.  **Redundancy**: Is this logic already duplicated elsewhere in the project?
    
6.  **Non-Functional Constraints**: Are there specific requirements like multi-currency, multi-tenancy, or high performance?
    

#### Decision Matrix (L1-L3):

*   **Level L1 (Cosmetic)**: Small teams (≤3), stable logic, no duplication. Goal: Immediate readability, zero risk.
    
*   **Level L2 (Structural)**: Logic duplicated ≥3 times or lack of testability blocking releases. Goal: Decomposing complexity.
    
*   **Level L3 (Architectural)**: Large teams, volatile logic, or complex requirements. Goal: Enabling product scalability.
    

### 3\. Phase II: Refactoring Analyze – Mapping Technical Debt

This is the "differential diagnosis" of software. The analyst maps issues using a rigorous structure:

| **Smell** | **Level** | **Location** | **Impact (1-3)** | **Strategic Note** |

| Magic Number | L1 | `calculate_tax()` | 1 | Replace with `VAT_RATE` constant |

| Long Method (>20 lines) | L2 | `process_order()` | 2 | Extraction needed for isolated testing |

| Feature Envy | L3 | `UserClass.check()` | 2 | Logic belongs to `Account` class |

| God Class | L3 | Entire Class | 3 | Blocks extension; violating SRP |

**Impact Scale:**

1.  **Cosmetic**: Low impact on maintainability.
    
2.  **Obstructionist**: Makes testing or understanding difficult.
    
3.  **Blocking**: Systematic source of bugs or total impediment to extension.
    

### 4\. Phase III: Refactoring Execute – Controlled Intervention

Execution follows an incremental protocol. **The absolute dogma: no changes without "green" tests.**

1.  **L1 (Cosmetic)**: Rename variables, extract constants. Zero logic changes.
    
2.  **L2 (Structural)**: Decompose long methods into named sub-functions. Each must be independently testable.
    
3.  **L3 (Architectural)**: Apply complex patterns (Service Classes, Strategy Pattern).
    
    *   _Mandatory Constraint_: Every L3 abstraction must include a code comment explaining the **strategic why** (e.g., `"// Strategy Pattern introduced to support future payment gateways per Interview Phase"`).
        

**Execution Workflow:**

1.  **Plan**: Propose 3-5 steps with risk estimation.
    
2.  **Confirm**: Wait for user approval.
    
3.  **Differential Execution**: Step-by-step implementation with diffs.
    
4.  **Test**: Verify "green" status after every single step.
    
5.  **Summary**: Final report of changes made.
    

### 5\. Implementation Guide: IDE Integration & Team Deployment

#### IDE Configuration (Cursor, Antigravity, Windsurf)

To make this framework operational, these Markdown files should be used as **System Prompts** or **Custom Instructions**:

*   **Project-Level Settings**: Save this document as `.cursorrules` or in the `.github/prompts` folder.
    
*   **Persona Mapping**: Instruct the AI: _"You are a Context-Driven Refactoring Consultant. Never suggest code changes before completing Phase I (Interview) and Phase II (Analyze)."_
    
*   **Command Triggers**: Create specific commands (e.g., `/refactor-interview`) that force the AI to follow the "Dimensions of Inquiry" before proceeding.
    

#### Team Customization & Deployment

Before deploying this framework to a development group, it must be **contextualized**:

1.  **Stack Alignment**: Adapt the "Exclusion Constraints" (e.g., if the team doesn't use `ABC` in Python or `Interfaces` in Go, update the L3 forbidden patterns).
    
2.  **Threshold Definition**: Define what "Long Method" means for your specific project (e.g., is it 20 lines or 50 lines?).
    
3.  **Onboarding**: Conduct a pilot refactoring session. If the refactoring increases the cognitive load for junior members or slows down onboarding, the architecture is failing its primary goal: **clarity**.
    

### 6\. Final Checklist

*   $$ $$
    
    **Functional Parity**: All tests are green; zero regressions.
    
*   $$ $$
    
    **Contextual Justification**: No complex patterns (Repository, ABC) introduced without explicit interview-based motivation.
    
*   $$ $$
    
    **Architectural Comments**: Every L3 abstraction explains the "why," not just the "what."
    
*   $$ $$
    
    **Cognitive Load**: A new developer can understand the flow faster than the previous version.