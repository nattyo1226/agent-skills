---
name: doc-write
description: >
  Create or locally revise project documentation, including development plans,
  following shared documentation structure, responsibility, and writing rules.
  Use for targeted writing/editing tasks, not repository-wide reorganization.
---

# Write Project Documentation

Use this skill for **creating or editing the documents requested by the user**, including `docs/plans/<task>/` for an upcoming multi-stage task.

## Required conventions

Before writing or editing, read and apply both `references/documentation/conventions.md` and `references/documentation/writing.md` in this Skill directory. The former governs document scope, ownership, placement, and language selection. The latter governs technical precision and reader-oriented communication. Treat both as constraints within the requested work, **not** as instructions to perform general maintenance. If either reference file is missing, report the installation problem rather than guessing its rules.

## Workflow

1. **Scope the request.** Identify the documents the user asked to create or modify and the intended outcome. Do not expand the edit set merely because related documents could be improved.
2. **Locate the owner.** Check the relevant existing documentation and choose the appropriate location according to the shared conventions. Reuse an existing document when it already owns the information.
3. **Gather necessary facts.** Read code, requirements, or other relevant documents as needed; distinguish verified behavior from assumptions and proposals.
4. **Write or edit.** Apply the shared writing guidelines to structure and express the content, and add useful links to permanent authoritative sources.
5. **Check the targeted result.** Verify that the changed documents are coherent and readable, satisfy the shared writing guidelines, respect ownership boundaries, and have valid links where relevant.
6. **Report the result.** Summarize what was changed and separately flag any unrelated issues discovered. Do not silently fix those issues.

## Development plans

Create `docs/plans/<task>/` only when the requested development task merits explicit multi-stage planning, especially when investigation or design precedes implementation. For straightforward tasks, a plan is optional rather than mandatory.

For a new plan, create `README.md` with objectives, scope, stages, current progress, and completion criteria. Add supporting files only when useful.

**Creating or revising a plan does not authorize implementing the plan, updating the project's permanent documentation, or deleting the plan.** Those are separate tasks.

## Boundaries

- Do not restructure unrelated documents.
- Do not automatically reconcile every document in `docs/`.
- Do not treat writing a plan as completing its development task.
- Never add references from permanent documents to `plans/`.
- If asked only to review or propose wording, do not modify files unless requested.
