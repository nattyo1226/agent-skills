# Code Quality Philosophy

Code is not merely a sequence of instructions for a machine. It is also a representation of concepts, operations, and constraints that people must understand, use, verify, and change. **Good code communicates its meaning through its structure.**

This communication serves two audiences:

- **Users of the code** should be able to express their intent through coherent, predictable interfaces without understanding irrelevant implementation details.
- **Developers maintaining the code** should be able to recover its responsibilities, invariants, dependencies, and design rationale without reconstructing the entire system.

## Semantics before structure

Design begins with what the software means and must guarantee: domain concepts, supported operations, observable behavior, and constraints. Names, types, modules, data representations, and algorithms should follow from those requirements. Existing code is evidence about the system, not an unquestionable specification of its design.

## Expressive core, simple use

Core abstractions should capture the genuine generality of the domain rather than the accidents of particular use cases. User-facing interfaces should make common tasks straightforward, even when that requires sophisticated internals. Neither maximum generality nor minimum code size is an end in itself.

## Complexity belongs where it can be understood

Some complexity is essential to the problem and must be represented faithfully; other complexity arises from avoidable dependencies, incidental distinctions, or unnecessary mechanisms. The aim is not to erase complexity, but to **express essential complexity clearly and minimize accidental complexity**. Good boundaries keep details from spreading to people who do not need them.

## Design is deliberate, revisable judgment

Consider the relevant semantics and overall structure before committing to local changes. Implementation may proceed incrementally, and evidence from implementation or testing may require revising the design. Principles guide this judgment; they are not mechanical rules. Exceptions are legitimate when their constraints, benefits, and costs are explicit.

The corresponding evaluation criteria are in [Design Principles](principles.md).
