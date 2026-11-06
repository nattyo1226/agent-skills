# Documentation Conventions

This document defines the shared conventions for project documentation. It is a set of constraints, not a request to create, reorganize, or update documents.

## 1. Scope and precedence

- Apply these conventions only within the scope of the requested task.
- Do not create, edit, move, or delete unrelated documents to enforce these conventions.
- Read related documents as needed for context, but do not modify them without task-specific justification.
- Report unrelated inconsistencies separately rather than silently fixing them.
- Follow explicit user instructions where they override these defaults. If an instruction conflicts with a critical responsibility boundary, identify the conflict rather than silently reinterpreting it.

## 2. Document layout

Use the following structure as needed; do not create empty placeholder files or directories:

```text
docs/
├── requirements.md
├── architecture.md
├── design/
│   └── <topic>.md
├── decisions/
│   └── <decision>.md
├── future-work.md
├── future-work/
│   └── <proposal>.md
└── plans/
    └── <task>/
        ├── README.md
        └── ...
```

### Requirements — `docs/requirements.md`

Define **what the project is intended to achieve**: purpose, scope, functional and non-functional requirements, and relevant constraints or exclusions. Avoid implementation-specific descriptions unless essential to the requirement.

### Architecture — `docs/architecture.md`

Define **what the project provides and how its major parts are organized**: deliverables/components, their responsibilities and boundaries, dependencies, and system-level relationships. Delegate component-level APIs and contracts to `design/`.

### Design — `docs/design/*.md`

Define **how a component is specified and broadly realized**: responsibilities, APIs and semantics, mathematical definitions and contracts, invariants, preconditions/postconditions, key algorithms, and implementation overview where relevant. A design document may cover a cross-component concern when appropriate. Avoid mechanical restatements of code.

### Decisions — `docs/decisions/*.md`

Preserve **important decisions and their rationale**, including consequential accepted, rejected, and superseded alternatives. Describe context, alternatives, decision, rationale, and important consequences when applicable. Do not record every minor implementation choice.

### Future work — `docs/future-work.md` and `docs/future-work/*.md`

Record **ideas, candidate features, deferred improvements, and unadopted proposals**. Keep the top-level file a concise overview; put substantial explanations in `future-work/`. Distinguish proposals from committed requirements and implemented features.

### Plans — `docs/plans/<task>/`

Store **temporary working documents for active multi-stage development tasks**. Create a plan when the task benefits from several stages, especially investigation or design before implementation; do not require one for trivial or straightforward changes.

The task directory's `README.md` should state objectives, scope, stages, progress, and completion criteria. Additional files may hold investigations, design notes, experiments, or review results. Plans are not authoritative specifications.

## 3. Current state, history, and proposals

- `requirements.md`, `architecture.md`, and `design/` describe the **current accepted direction and implementation**, not their history. Do not keep superseded behavior, rejected proposals, or progress logs in these documents.
- Place significant decision history and rationale in `decisions/`.
- Place unadopted future proposals in `future-work.md` or `future-work/`.
- Place temporary investigation, planning, and progress information in `plans/`.
- Never present unimplemented or unaccepted behavior as an established fact. When describing current behavior, verify it against the relevant source where feasible.

## 4. Information ownership and links

- Give each authoritative fact one primary home, chosen by document responsibility.
- Prefer links to canonical definitions over maintaining duplicate statements. Brief summaries are permissible for local comprehension.
- Add useful **relative links** between permanent documents when they improve navigation or understanding. Links may go in either direction; document responsibilities do not impose a link hierarchy.
- Documents under `plans/` may link to permanent documentation. **No documents outside `plans/` may link to documents inside `plans/`.**
- Keep links valid when moving, deleting, or renaming files.

## 5. Language

Choose the language in this order:

1. Explicit user instruction.
2. Existing document's language.
3. English.

Avoid unnecessary language mixing. Preserve established terminology unless changing it is part of the task.

## 6. Writing quality

- Structure explanations from **abstract to concrete**, both across the document and within sections.
- Introduce purpose, scope, and core concepts before details where useful; state responsibilities before interfaces and implementation details.
- Explain prerequisites before dependent material, and group content into coherent sections with descriptive headings.
- Distinguish requirements, guarantees, assumptions, design choices, implementation details, and examples.
- Define mathematical symbols and objects before use; state assumptions, domains, invariants, and conditions under which claims hold.
- Be precise, concise, and consistent in terminology, notation, and API names. Do not invent guarantees or unsupported rationale.
- Prefer prose for explanations; use tables, lists, equations, diagrams, and code only when they improve clarity.
- Avoid unnecessary background, duplication, excessive fragmentation, and rigid templates that do not suit the document.

## 7. Review criteria

For documents within the requested scope, check that content belongs to the correct owner, reflects the accepted/current project state where applicable, uses appropriate cross-references, and does not contradict relevant authoritative documents. A check is not permission to restructure unrelated documentation.
