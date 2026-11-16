# Technical Writing Guidelines

This document defines writing principles for technical documentation maintained within a project, including README files, requirements, architecture and design documents, decision records, and development plans.

The goal is to help readers build an accurate understanding of the subject with as little unnecessary effort as possible. Technical correctness and consistency are requirements; the guidance on structure and expression should be applied with judgment rather than as a rigid template.

This document governs **how information is communicated**. Document responsibilities, information ownership, language selection, and change scope are governed by [conventions.md](conventions.md). These guidelines do not authorize changes outside the requested task.

## 1. Reader-oriented writing

- Identify what the intended reader needs to understand, decide, or do after reading. Organize the explanation around that goal rather than around the order in which the information was discovered or implemented.
- Assume the knowledge appropriate to the document's audience. Explain unfamiliar concepts and essential context without repeating background the reader can reasonably be expected to know.
- Make the purpose and relevance of each substantial explanation apparent. Readers should be able to tell why a detail matters before investing effort in it.
- Favor a direct explanation of the subject over commentary about the act of documenting it.

## 2. Information flow

- **Present the main point before supporting detail** when the reader benefits from knowing the outcome first. State a component's responsibility before describing its internals, or a design decision before elaborating on its rationale. Do not bury essential information beneath background.
- Develop the explanation progressively. Introduce the overall structure before its parts, general concepts before specialized cases, and familiar ideas before unfamiliar ones when these orders support understanding.
- Respect conceptual dependencies: introduce necessary definitions, assumptions, and prerequisites before relying on them. An important result may be stated early as an overview, with its justification developed afterward.
- Use each section to address a coherent question or topic. Give sections informative headings, and make their relationship to the surrounding discussion clear.
- Within a paragraph, establish a central point and connect supporting statements to it. Across paragraphs, make changes in topic or level of detail easy to follow.
- Choose the order that best serves the explanation. A concrete example, motivating problem, or stepwise derivation may appropriately precede an abstract account or conclusion. Avoid imposing one sequence on every document.

## 3. Cognitive clarity

- **Express what something is or does directly.** Prefer affirmative descriptions when they communicate the intended meaning more clearly. Use negative statements when absence, prohibition, exclusion, or contrast is itself important.
- Make relationships explicit when readers would otherwise have to infer them: cause and effect, prerequisites, alternatives, trade-offs, and the relationship between a claim and its justification.
- Keep the amount of information the reader must hold at once manageable. Separate distinct ideas, limit deeply nested qualifications, and place conditions close to the statements they qualify.
- Use consistent subjects and terminology so readers can follow what each statement refers to. Avoid ambiguous pronouns and abrupt changes of perspective.
- Be concise without becoming cryptic. Remove repetition, filler, and incidental details, but retain the explanations and transitions needed to understand the argument.
- Use examples when they make an unfamiliar abstraction or subtle distinction easier to grasp. Explain what the example illustrates, and do not let an example substitute for the general rule.

## 4. Technical precision

- Distinguish established facts, requirements, guarantees, assumptions, design decisions, proposals, and examples. Express uncertainty explicitly, and never present intended or hypothetical behavior as verified behavior.
- State the conditions under which a claim holds. Distinguish universal claims from conditional ones, and avoid confusing necessary and sufficient conditions.
- Support non-obvious technical claims with appropriate reasoning, evidence, or references. Do not invent behavior, guarantees, performance characteristics, or design rationale.
- Define domain-specific terms, mathematical objects, symbols, and notation as needed before using them in detailed reasoning. Specify domains, units, invariants, preconditions, and postconditions wherever they affect interpretation.
- Use names and notation consistently, especially for APIs, types, operations, and mathematical quantities. Preserve meaningful distinctions between related concepts.
- Prefer precise statements over vague qualifiers such as “appropriate,” “efficient,” or “as needed” when those qualifiers would obscure a contract or decision criterion.
- Preserve correctness when simplifying an explanation. Mark deliberate simplifications, approximations, and omitted cases when they could otherwise mislead the reader.

## 5. Presentation

- Use prose for connected explanations and arguments. Use lists for parallel points or procedures, tables for comparisons across shared dimensions, equations for mathematical relationships, code for concrete interfaces or examples, and diagrams for structures or interactions that are difficult to convey in prose.
- Select a form because it makes the content easier to understand, not because a document template or stylistic preference calls for it.
- Introduce substantial equations, examples, diagrams, and code with enough context to explain their purpose; clarify their implications or limitations when they are not self-evident.
- Use headings to expose the structure of the subject, but avoid fragmenting a short continuous explanation into many small sections.
- Keep formatting consistent and restrained. Emphasis should identify genuinely important distinctions rather than compete with the content.

## 6. Context and references

- Make a document sufficiently self-contained for its intended purpose. Supply the immediate context needed to interpret its claims, while allowing readers to follow references for broader background or detailed definitions.
- Refer to authoritative definitions and specifications instead of reproducing them in multiple places. A brief local summary is useful when it lets readers understand the current discussion without interrupting their reading.
- Identify the source of external facts or nontrivial borrowed claims when verification or attribution matters. Use descriptive links that make the destination and relevance clear.
- Avoid both extremes: forcing readers to navigate elsewhere for every basic concept and repeating extensive material that has a clear authoritative home.
