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

Use one `docs/plans/<task>/` directory for each task that has a plan. Its `README.md` is the entry point and should state objectives, scope, stages, progress, and completion criteria. Depending on the amount and nature of the material, you may add files in the same directory for supporting material such as investigations, design notes, experiments, or review results. Plans are not authoritative specifications.

## 3. Current state, history, and proposals

- `requirements.md`, `architecture.md`, and `design/` describe the **current accepted direction and implementation**, not their history. Do not keep superseded behavior, rejected proposals, or progress logs in these documents.
- Place significant decision history and rationale in `decisions/`.
- Place unadopted future proposals in `future-work.md` or `future-work/`.
- Place temporary investigation, planning, and progress information in `plans/`.
- Never present unimplemented or unaccepted behavior as an established fact. When describing current behavior, verify it against the relevant source where feasible.

## 4. Information ownership, relevance, and links

- Give each authoritative fact one primary home, chosen by document responsibility.
- Prefer links to canonical definitions over maintaining duplicate statements. Brief summaries are permissible for local comprehension.
- Add useful **relative links** between permanent documents when they improve navigation or understanding. Links may go in either direction; document responsibilities do not impose a link hierarchy.
- Documents under `plans/` may link to permanent documentation. **No documents outside `plans/` may link to documents inside `plans/`.**
- Keep links valid when moving, deleting, or renaming files.
- Avoid documenting incidental details of individual developers' or agents' environments, such as operating systems, Nix devShells, or `direnv exec` workflows.
- Document environment-specific requirements or procedures only when they are part of the project's supported workflow, necessary for its use, or relevant to reproducibility. Do not infer project requirements from the development environment alone.

## 5. Language

Choose the language in this order:

1. Explicit user instruction.
2. Existing document's language.
3. English.

Avoid unnecessary language mixing. Preserve established terminology unless changing it is part of the task.

## 6. Writing guidelines

For project technical documentation, follow [Technical Writing Guidelines](writing.md) for reader-oriented information flow, cognitive clarity, technical precision, presentation, and contextual references. These guidelines govern how content is communicated; the conventions in this document govern its scope, ownership, and placement.

## 7. Review criteria

For documents within the requested scope, check that content belongs to the correct owner, reflects the accepted/current project state where applicable, uses appropriate cross-references, and does not contradict relevant authoritative documents. Check writing quality against [Technical Writing Guidelines](writing.md). A check is not permission to restructure unrelated documentation.
