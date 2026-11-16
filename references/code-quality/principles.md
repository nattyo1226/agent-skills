# Code Quality Principles

These principles operationalize the [Code Quality Philosophy](philosophy.md). They are criteria for reasoning about designs and reviews, **not a mandatory checklist or a ranking of stylistic preferences**. Apply them according to the project's contracts, risks, and constraints.

## 1. Represent semantics faithfully

**Principle.** Types, names, operations, and module boundaries should express the domain's actual concepts and relationships.

**Rationale.** When structure matches meaning, users can infer valid usage and developers can reason about behavior without translating through incidental implementation choices.

**Judgment.** Distinguish essential domain distinctions from representation details and historical accidents. Do not create a type, module, or hierarchy merely because the current implementation happens to have that shape. Conversely, do not merge concepts simply because their implementations look alike.

## 2. Make contracts and invariants explicit

**Principle.** Specify what an operation requires, guarantees, and preserves, including error semantics and resource obligations where relevant. Give each invariant a clear point of enforcement.

**Rationale.** Explicit contracts reduce hidden assumptions and allow components to be understood and verified independently. [1]

**Judgment.** Encode invalid states and operations out of the representable space when practical. Prefer static guarantees where they are expressive and usable; enforce remaining boundary conditions at runtime and verify behavioral properties with tests or stronger methods as appropriate. Added type machinery is justified by the guarantees it provides, not by its sophistication.

## 3. Keep core abstractions expressive and user-facing APIs simple

**Principle.** Core facilities should express the domain's genuine generality; interfaces for common tasks should remain direct and unsurprising.

**Rationale.** A capable core avoids duplicating domain knowledge, while simple entry points reduce the concepts users must learn. Well-designed interfaces can hide substantial implementation complexity. [2]

**Judgment.** Generalize along real semantic dimensions, not hypothetical future variations. Specialized conveniences are useful when they clarify common operations, but should not introduce competing definitions of the same concept. Avoid layers, traits, parameters, or wrappers that only move complexity around.

## 4. Align responsibilities with invariants and reasons to change

**Principle.** Place related behavior and the invariants it maintains under coherent ownership; separate responsibilities that represent genuinely different concerns.

**Rationale.** Coherent ownership helps localize changes and prevents consistency rules from becoming scattered obligations.

**Judgment.** High cohesion does not mean making every function or module small. A split is beneficial when it clarifies responsibilities or isolates a meaningful change; it is harmful when it forces callers to coordinate details that should remain internal.

## 5. Hide decisions that clients need not know

**Principle.** Expose stable semantic contracts, not incidental representations, algorithms, sequencing, or storage choices.

**Rationale.** Information hiding allows implementation decisions to change without requiring unrelated clients to change. Module boundaries should be chosen for what they conceal, not merely for the order of processing steps. [3]

**Judgment.** Avoid both leaking internal details and introducing abstract interfaces that conceal nothing meaningful. Select dependencies and boundaries according to the knowledge each component actually requires. No particular object-oriented, functional, or data-oriented organization is universally preferred; performance and data-access constraints can legitimately affect the internal structure.

## 6. Minimize accidental complexity and enable local reasoning

**Principle.** Make the relevant behavior and guarantees understandable with as little unrelated context as practical.

**Rationale.** Dependencies, hidden coupling, and needless indirection increase the mental work required to understand and modify code. Essential problem complexity cannot always be simplified away. [2, 4]

**Judgment.** Evaluate complexity by concepts, interactions, and knowledge required—not line count, function length, or number of files alone. Document non-obvious assumptions and design reasons; do not expect identifiers or source structure to communicate every rationale by themselves.

## 7. Verify correctness at the appropriate level

**Principle.** Prefer guarantees established by construction or static analysis, and validate properties that remain outside those guarantees through suitable dynamic or analytical checks.

**Rationale.** Static checks rule out classes of invalid programs within their stated assumptions; tests exercise behavior and reveal failures but do not establish correctness for all cases.

**Judgment.** Select verification according to the contract: unit and integration tests for behavior, property-based tests for general laws, targeted checks for edge cases, and measurement for performance or resource claims. Account for floating-point behavior, concurrency, or external systems when relevant. A passing test suite is evidence, not a substitute for reasoning about requirements and invariants.

## 8. Design deliberately; implement incrementally when useful

**Principle.** Derive a coherent target structure from the relevant semantics and constraints before choosing implementation steps.

**Rationale.** Unexamined local extensions can preserve unsuitable boundaries; small, verifiable implementation steps can reduce migration risk. Deliberate design and evolutionary implementation are compatible. [5]

**Judgment.** Compare retaining the current design with revising it. Preserve sound structures; make the smallest coherent structural change when they are unsound. Revise the target design if new evidence invalidates its assumptions. Avoid speculative extensibility and unrelated redesign.

## 9. Make trade-offs explicit and proportional

**Principle.** Treat principles as competing considerations, not absolute prohibitions. Decisions should serve documented requirements and realistic usage.

**Rationale.** A stronger guarantee may complicate an API; information hiding may constrain optimization; reuse may increase indirection. There is no context-free winner.

**Judgment.** For consequential choices, identify the affected semantic contract, the alternatives, their concrete costs, and the constraints that decide between them. Do not classify style preferences or speculative future scenarios as defects. Prefer measured evidence for performance claims and concrete change scenarios for maintainability claims.

## Questions for design and review

- What does this component mean, and what must it guarantee?
- Can users express valid intent without learning irrelevant details?
- Which invariants are enforced, where, and by what mechanism?
- Can a developer understand and change this responsibility locally?
- Does each abstraction remove a real burden, or merely add indirection?
- What evidence supports the selected trade-off and its verification?

## References

These sources inform the principles; the judgments above are this project's synthesis, not rules claimed to be universally established by those authors.

1. Bertrand Meyer, *Design by Contract* (preconditions, postconditions, invariants). [Eiffel documentation](https://www.eiffel.org/doc/eiffel/I2E-_Design_by_Contract_and_Assertions).
2. John Ousterhout, *A Philosophy of Software Design*, 2nd ed. (2021). [Author's book page](https://web.stanford.edu/~ouster/cgi-bin/aposd.php).
3. D. L. Parnas, “On the Criteria To Be Used in Decomposing Systems into Modules,” *Communications of the ACM* 15(12), 1053–1058 (1972). [DOI](https://doi.org/10.1145/361598.361623).
4. Frederick P. Brooks Jr., “No Silver Bullet—Essence and Accidents of Software Engineering,” *IEEE Computer* 20(4), 10–19 (1987). [Text](https://cs.calvin.edu/courses/cs/262/kvlinden/references/brooksNoSilverBullet.html).
5. Martin Fowler, *Refactoring: Improving the Design of Existing Code*, 2nd ed. (2018), and “[Is Design Dead?](https://martinfowler.com/articles/designDead.html)” (2004). [Book page](https://martinfowler.com/books/refactoring.html).
