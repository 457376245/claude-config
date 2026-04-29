---
name: "requirement-doc-tracking"
description: "Create and maintain a Chinese requirement implementation tracking document before and during code changes, then final-align it for later Requirement Doc Review. Use when starting or continuing a new feature, bug fix, change request, integration change, or cross-project task that should leave a docs trail in the target project's docs directory. Do not use for independent delivery review after implementation; use requirement-doc-review for that."
---

# Requirement Doc Tracking

Keep one requirement implementation tracking document aligned with the real work from kickoff to delivery. Create the project doc before substantive implementation, update it as scope or decisions change, and finish by making it ready for an independent Requirement Doc Review.

## Workflow

1. Identify the target project and its documentation location.
2. Before making substantive code changes for a new requirement, create or update a tracking document in that project's `docs/` or `docs/requirements/` directory.
3. Use `references/需求文档模版.md` as the starting structure. Fill unknown details with `TBD` instead of inventing answers.
4. Preserve the user's original request separately from later conclusions, final delivery notes, and implementation decisions.
5. Define explicit acceptance criteria before or early in implementation. If the user has not provided them, derive the smallest verifiable criteria from the request and mark assumptions clearly.
6. Update the document whenever the plan, scope, interfaces, database changes, risks, progress, validation status, or rollout assumptions change.
7. Before closing the task, compare the final code and behavior with the document. Remove stale plans, capture deviations, and make the document describe what actually shipped.
8. Mark the review entry as `待审查` when the requirement is complete, paused for handoff, or ready for independent audit.
9. In the final response, include the document path and confirm whether the document now matches the delivered business and technical state.

## Required behaviors

- Create the requirement document before the first substantive implementation edit for a new request.
- Prefer one document per user-visible requirement or tightly related change set.
- Record both business intent and technical design; do not leave the document as code notes only.
- Keep the original request, assumptions, acceptance criteria, and final delivery facts distinguishable.
- Keep the document updated during execution, not only at the end.
- If the work spans multiple repos or services, capture the dependency chain and note which side changed.
- If the task is blocked or paused, leave the document in a state that lets the next engineer resume quickly.
- Replace outdated statements instead of appending contradictory notes.
- Map changed code, APIs, configs, tables, jobs, or routes back to the acceptance criteria whenever possible.
- Record what was not verified and why; do not imply validation that did not happen.
- Document name and content should be in Chinese.

## Minimum content

Every requirement document should cover:

- Metadata and status
- Original request
- Summary, background, and goal
- Scope, out of scope, assumptions, and open questions
- Acceptance criteria
- Affected systems, files, routes, APIs, tables, configs, jobs, or external dependencies
- Implementation plan and key decisions
- Progress log
- Code change list mapped to acceptance criteria
- Validation and testing, including unverified items
- Risks and follow-up work
- Final alignment check
- Requirement Doc Review handoff entry

## Final audit checklist

Before declaring the task complete, verify that:

- The implemented behavior matches the documented business goal.
- The document names the actual files, modules, routes, tables, configs, or jobs that changed.
- Cross-project dependencies and contracts are described correctly.
- Deviations from the original plan are captured.
- Validation status reflects what was actually run and what was not verified.
- Remaining risks and follow-up work are explicit.
- The document does not describe code or behavior that was never shipped.
- The review entry identifies whether an independent `requirement-doc-review` pass is recommended and where its report should go.

## Trigger examples

Use this skill for requests like:

- "Implement a new requirement in this project."
- "Add this feature and keep a docs trail."
- "Before coding, create a docs file to track the demand."
- "This change spans two services; document the dependency and update it until done."

## Relationship to Requirement Doc Review

Use this skill while the requirement is being discussed, implemented, paused, or finalized. It creates the source-of-truth tracking document.

Do not perform the independent delivery review here. When the user asks to review, audit, verify, accept,复核,验收, or check whether an implemented requirement meets its tracking document, use `requirement-doc-review` instead.

## Reference map

- Read `references/需求文档模版.md` when creating or refreshing the project tracking document.
- Read `references/可选章节清单.md` only when the requirement involves interfaces, database changes, rollout, rollback, or other complex delivery concerns.
