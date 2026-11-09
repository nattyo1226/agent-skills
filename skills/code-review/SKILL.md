---
name: code-review
description: >
  Review code for correctness, semantic contracts, architecture, robustness,
  performance, and maintainability. Use for reviews of changes, components,
  or repositories, including structural design concerns. Investigate primarily
  through static code inspection and verify significant uncertainties with
  targeted tests when useful. Report findings without modifying code.
---

# Code Review

Evaluate whether an implementation satisfies its intended behavior and whether its structure appropriately expresses domain concepts, responsibilities, and invariants.

Identify both **demonstrable defects** and **substantiated design concerns**. Do not treat conformity with the existing codebase as proof of design quality, and do not mistake stylistic preferences for defects.

## Scope and Boundaries

- Determine the review target from the request: a change/diff, component, architecture, or repository.
- Inspect dependencies, callers, tests, and documentation as needed to understand the target, but do not expand findings into unrelated areas.
- Review only by default. Do not modify source files, tests, configuration, or documentation unless explicitly asked to implement fixes.
- Use existing checks or isolated, temporary reproductions when warranted. Avoid destructive commands and unexpected side effects; follow the user's authorization constraints.
- A request to review does not authorize a redesign or implementation. Suggest `code-design` for substantial redesign where appropriate, rather than undertaking it unasked.
- Scale the depth of investigation and reporting to the task's size and risks.

## Review Criteria

Select relevant criteria rather than mechanically auditing every category.

1. **Correctness:** observable behavior, specifications, edge cases, state transitions, and error handling.
2. **Semantics:** meaning of types and APIs, contracts, invariants, preconditions, postconditions, and domain assumptions.
3. **Architecture:** responsibility boundaries, abstraction level, component granularity, coupling, and dependency direction.
4. **Robustness:** invalid inputs, failure handling, resource lifecycle, concurrency, and recovery where applicable.
5. **Performance:** significant algorithmic, computational, allocation, memory, or I/O costs; avoid speculative micro-optimization findings.
6. **Maintainability:** avoidable complexity, duplication, hidden coupling, and the cost of foreseeable changes.

For structural findings, explain the concrete mismatch between the implementation and its responsibilities or semantics, and the consequences of that mismatch. Do not recommend additional layers, generic frameworks, or larger refactors merely for aesthetic uniformity.

## Workflow

### 1. Establish the Review Contract

- Identify the exact files, changes, behavior, or components under review.
- Determine the intended requirements and accepted constraints from the request, relevant project documentation, tests, and public API contracts.
- Distinguish established requirements from assumptions, historical design choices, and the incidental current implementation.
- For change reviews, understand the intended change and compare behavior before and after where relevant.

### 2. Reconstruct the Relevant Design

- Identify domain concepts, responsibilities, data and control flow, observable contracts, and invariants.
- Inspect the implementation and its actual call sites or consumers.
- Evaluate whether abstractions and boundaries express those concepts coherently; do not assume existing types or module divisions are inherently correct.
- Trace plausible failure paths and distinguish essential constraints from implementation accidents.

### 3. Investigate Candidate Findings

- Begin with static reading and reasoning from concrete code paths and relevant specifications.
- Check whether a suspected defect can actually occur under supported inputs or states; account for existing guards, callers, and documented assumptions.
- For important or uncertain claims that can be tested, use relevant existing tests or a targeted reproduction when the expected value justifies the effort.
- Prefer an isolated temporary reproduction to altering the repository solely for review. Do not leave generated artifacts behind unless they are required and authorized.
- Tests are evidence, not the definition of correctness: a passing test suite does not rule out uncovered defects, and an untested but logically demonstrated defect may still be reported as confirmed.
- Assess structural concerns using contracts, concrete coupling or complexity, and realistic change scenarios; execution tests may not resolve architectural questions.
- For external behavior that materially affects a finding, consult authoritative documentation or source for the version actually used where feasible.

### 4. Classify and Prioritize

Use three distinct classes:

**Defects:** A violation of an established requirement, contract, invariant, or expected supported behavior, supported by a concrete code path, logical demonstration, or reproduction. Confirmation does not require a running test if the evidence is decisive.

**Design Concerns:** A substantiated mismatch in semantics, abstractions, responsibility boundaries, dependencies, or maintainability, even if no current malfunction is demonstrated. State specific consequences or plausible maintenance costs, not just a preferred style.

**Unverified Risks:** A potentially important failure hypothesis that remains unresolved. Explain the uncertainty, what evidence is missing, and how to verify it. Never present these as confirmed defects.

Prioritize based on impact and likelihood, not confidence alone:

- **P0 — Critical:** severe, urgent, broadly damaging failure (for example, major data loss or security compromise).
- **P1 — High:** significant failure of important behavior or contract, or a high-impact structural problem.
- **P2 — Medium:** material but bounded correctness or design issue that merits remediation.
- **P3 — Low:** minor, concrete issue with limited consequences.

Use priority for both defects and design concerns when helpful, while keeping the categories separate. Explicitly state confidence or limitations when they affect interpretation. Do not inflate severity because evidence is uncertain.

### 5. Report Actionable Findings

Present findings before general commentary, ordered by priority within each category.

For each **Defect**, provide:

- A short, specific title and priority.
- File and line references where possible.
- The triggering conditions and observed or logically entailed impact.
- Evidence: relevant code path, specification, or test/reproduction result.
- A proportionate direction for correction, without implementing it unless requested.

For each **Design Concern**, provide:

- A short, specific title and priority or impact level.
- Relevant locations and the affected abstraction or responsibility boundary.
- Why the structure is problematic in semantic or engineering terms.
- Concrete consequences and an appropriate direction for improvement.

For each **Unverified Risk**, give its suspected impact, current evidence, missing verification, and useful next check.

Use this report structure when applicable:

```markdown
## Defects
### [P1] Specific issue
...

## Design Concerns
### [P2] Specific structural concern
...

## Unverified Risks
...

## Verification
- Scope inspected: ...
- Checks run and outcomes: ...
- Checks not run and limitations: ...
```

Omit empty sections when doing so improves clarity, but explicitly state when no actionable findings were identified. Distinguish absence of findings from proof of correctness. Avoid long praise, speculative suggestions, and purely stylistic remarks unless they violate an established requirement.

## Review Quality Checklist

Before concluding, verify that:

- Each confirmed defect has a supported failure mechanism or contract violation.
- Each design concern has a concrete rationale and meaningful consequence.
- Uncertain hypotheses are labeled as such rather than promoted to defects.
- Findings are within scope, distinct, actionable, and not duplicates.
- Claims about tests, tools, and inspections reflect what was actually done.
- No unintended repository changes were made.
