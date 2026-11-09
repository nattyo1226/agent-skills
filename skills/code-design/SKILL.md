---
name: code-design
description: >
  Evaluate and improve software design when implementing features, changing
  abstractions or APIs, or refactoring existing code. Use when semantic
  boundaries, component responsibilities, data models, invariants, or
  architectural structure need reconsideration rather than merely extending
  the current implementation. Supports design-only analysis and implementation.
---

# Code Design

Design from semantics; implement incrementally when useful.

Before extending existing structures, separate **what the software must mean and guarantee** from **how the current implementation happens to express it**. Treat the present architecture as evidence and a candidate solution, not as a default specification. Neither preserving nor replacing it is inherently preferable.

## Scope and working modes

- Follow the user's requested mode: **analysis/design only**, **refactoring**, or **implementation**. An analysis request does not authorize code changes; an implementation request should not stop at a proposal.
- Apply the depth of this workflow in proportion to the design risk. For routine local changes with no meaningful structural question, use a brief assessment rather than a formal design exercise.
- Inspect surrounding code and contracts as needed, but confine changes to the requested functional and architectural scope. Do not initiate unrelated cleanup or repository-wide redesign.
- Respect explicit compatibility requirements, repository constraints, user changes, and authorization boundaries. If a better design requires breaking an established external contract, explain the trade-off and obtain authorization when necessary.

## 1. Deconstruct: recover the underlying design

Identify the behavior and concepts independently of existing names, types, files, and call graphs.

- Determine the domain concepts, use cases, observable behavior, and required contracts.
- Identify invariants, preconditions, postconditions, ownership, lifecycle, and error semantics where relevant.
- Distinguish **essential constraints** (domain rules, accepted requirements, external contracts) from **incidental constraints** (historical organization, convenience wrappers, current representation, implementation accidents).
- Map existing components to their actual responsibilities. Look for responsibilities accidentally combined or artificially split, leaky abstraction boundaries, duplicated concepts, and mismatches between API names and behavior.
- Distinguish verified behavior from assumptions; consult tests, call sites, documentation, and implementation as needed. Do not infer an intended contract solely from the code's current shape.

The goal is to explain what the system does and must preserve **without treating its current decomposition as mandatory**.

## 2. Reconstruct: derive an appropriate design

Starting from the requirements and semantics, determine a coherent target structure before deciding how to edit existing files.

Consider, as relevant:

- Which concept owns each responsibility and invariant?
- What should be represented by types, modules, functions, interfaces, or data structures?
- Which states and operations should be expressible, and which invalid states can be excluded by construction?
- What belongs in the public contract versus an internal implementation detail?
- Are boundaries, dependency direction, coupling, and component granularity appropriate?
- Does each abstraction capture a genuine recurring concept or variation, rather than merely adding indirection?
- What constraints arise from performance, resource use, concurrency, interoperability, and migration?

Prefer the simplest structure that faithfully expresses the required semantics. Do not equate better design with more layers, traits, generics, files, or indirection. Conversely, do not keep an inadequate abstraction just because it already exists.

## 3. Compare with the current structure

Compare the derived design to the existing implementation. Where the choice is consequential, assess at least:

- **Incremental extension:** keep the existing boundaries and make localized changes.
- **Structural revision:** adjust responsibilities, representations, or interfaces to realize the target design.

Evaluate the alternatives against semantic fidelity, invariant enforcement, conceptual clarity, cohesion/coupling, API consistency, simplicity, performance, compatibility, verification, and migration cost.

Choose based on those trade-offs, **not on line count or preference for a large refactor**. If the existing design is sound, retain it. If not, identify the smallest coherent structural change that resolves the actual problem; avoid half-measures that preserve obsolete abstractions alongside their replacements without a clear need.

For a significant design choice, communicate the key reason and trade-off before implementation. Do not require an elaborate design report for a small change.

## 4. Realize: implement the selected design

When implementation is requested:

- Translate the target structure into changes, using incremental steps when they reduce risk or improve verifiability. Incremental **execution** must not silently become incremental **design**.
- Keep intermediate states coherent when practical; coordinate callers, types, tests, and documentation affected by changed contracts.
- Remove obsolete branches, adapters, and duplication when their removal is part of the selected change and safe within scope. Do not preserve compatibility shims without an actual compatibility requirement.
- Avoid introducing speculative extensibility or generic frameworks for hypothetical future needs.
- If investigation reveals that the chosen design rests on a false assumption, revise the design rather than forcing the implementation to fit it.

## 5. Verify behavior and structure

Check both functional correctness and whether the intended design improvement was achieved:

- Test observable behavior, edge cases, and the relevant invariants; check compatibility where required.
- Review responsibility boundaries, meaningful API semantics, coupling, granularity, and avoidable indirection.
- Verify that incidental properties of the old implementation have not become accidental new requirements.
- Run checks proportionate to the change and report any validation gaps or material risks.

When documentation updates are required, follow the repository's documentation conventions and applicable documentation skills; do not expand the change into a general documentation reorganization.

## Guiding question

> If this component were designed today from its requirements and semantics, would its structure resemble the existing implementation? If not, which differences matter for the present task?

Use the answer to make an explicit design judgment—not as an automatic mandate to rewrite code.
