---
name: doc-maintain
description: >
  Maintain and reorganize existing project documentation, reconcile completed
  development work into authoritative docs, clean up completed plans, or audit
  cross-document consistency. Use for explicit documentation maintenance tasks.
---

# Maintain Project Documentation

Use this skill for **explicitly requested documentation maintenance**, including restructuring, consolidation, consistency review, and closing out completed development plans.

## Required conventions

Read and apply `references/documentation/conventions.md` in this Skill directory. When writing or revising project technical documentation, or assessing its writing quality, also read and apply `references/documentation/writing.md`. The former governs document scope, ownership, and placement; the latter governs technical precision and reader-oriented communication. Neither expands the requested maintenance scope. If a required reference file is missing, report the installation problem rather than guessing its rules.

## Select the operation

Choose only the operation required by the user's request:

- **Audit:** examine documents, ownership, duplication, inconsistencies, and broken links; report findings without modifying files unless edits are requested.
- **Reorganize:** split, merge, move, or rewrite the specified documentation to improve boundaries and coherence. Update links affected by those changes.
- **Development closeout:** when implementation, validation, and review are complete, carry forward durable information from a plan into permanent documents and remove the finished plan.

Do not interpret a closeout request as authorization for repository-wide restructuring, or an audit request as permission to edit files.

## Development closeout

1. **Confirm status and scope.** Determine what development task is being closed. Check evidence that implementation, validation, and review have been completed; do not assume completion merely because a plan exists.
2. **Extract durable outcomes.** Read the relevant `docs/plans/<task>/` material and inspect the implemented result. Separate current facts, important decisions, future proposals, and transient progress notes.
3. **Update authoritative documentation as needed:**
   - `requirements.md`: newly accepted or modified requirements.
   - `architecture.md`: system-wide structure and responsibility changes.
   - `design/`: resulting component APIs, contracts, and implementation overview.
   - `decisions/`: consequential choices and rationale that warrant historical preservation.
   - `future-work.md` / `future-work/`: remaining unadopted or deferred proposals.
4. **Verify consistency.** Ensure the relevant permanent documentation reflects the implemented state and references remain valid. Check links to the task directory and its contents from documents that will remain, including other plans under `docs/plans/`. Resolve those links within the requested scope before deletion.
5. **Remove the completed plan.** Delete only the task directory being closed, after confirming completion, preserving the necessary durable information, and resolving incoming links from documents that will remain. If any of these conditions is unmet, report the blocker and retain the plan.
6. **Report changes and any remaining issues.** Do not copy chronological progress logs into permanent documentation.

## Reorganization

- Establish the explicitly requested scope before reorganizing.
- Identify authoritative owners and affected incoming/outgoing links.
- Prefer the smallest restructuring that resolves the documented problem.
- Preserve current specifications, mathematical contracts, and important decision rationale.
- Adjust links and check for regressions after moves or merges.

## Boundaries

- Restrict edits to the documents required for the requested operation.
- Read unrelated documents for context when necessary, but do not refactor them incidentally.
- Report unrelated issues separately.
- Do not start implementation work merely because a development plan is present.
- Apply the shared documentation conventions and writing guidelines to every technical document changed.
