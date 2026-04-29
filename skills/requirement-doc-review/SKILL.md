---
name: "requirement-doc-review"
description: "Review whether an implemented, paused, or ready-to-deliver requirement satisfies its Requirement Doc Tracking document by comparing the tracked requirement, scope, acceptance criteria, final delivery notes, validation records, and current workspace code. Use when the user asks to review, audit, verify, accept,验收,审查,复核,达标检查, or check whether an implementation meets a tracked requirement before delivery, merge, release, handoff, or after fixing prior review findings. Do not use for starting a new requirement or creating the tracking document."
---

# Requirement Doc Review

Audit a requirement after implementation, pause, handoff, or delivery preparation. Compare the Requirement Doc Tracking document with the real workspace code and produce a Chinese requirement delivery review report.

## Workflow

1. Locate the requirement tracking document.
   - Use the path provided by the user when available.
   - Otherwise search the target project's `docs/` and `docs/requirements/` directories for the most relevant recent tracking document.
   - If no tracking document can be identified, ask for the document path instead of guessing.
2. Read the tracking document first. Focus on original request, scope, out of scope, assumptions, acceptance criteria, affected systems, code change list, validation records, final alignment check, and review handoff.
3. Inspect the current workspace implementation.
   - Check `git status`, relevant diffs, changed files, tests, routes, configs, migrations, and modules named by the tracking document.
   - Treat the document as review input, not as proof. Verify claims against code wherever possible.
4. Compare implementation against the documented acceptance criteria.
   - Mark each criterion as `通过`, `不通过`, `部分通过`, or `无法确认`.
   - Cite concrete code, test, config, or document evidence for each conclusion.
5. Produce or update a requirement delivery review report using `references/需求达标审查报告模板.md`.
   - Default path: place it next to the tracking document as `<tracking-doc-name>-review.md`.
   - For a re-review after fixes, update the existing review report when that is clearer; otherwise create a numbered report such as `<tracking-doc-name>-review-2.md`.
6. In the final response, lead with the review conclusion, list blocking findings first, and include the report path.

## Required behaviors

- Review only after a requirement has implementation, is paused for handoff, is ready to deliver, or the user explicitly asks for a stage review.
- Do not create the requirement tracking document; that belongs to `requirement-doc-tracking`.
- Do not edit implementation code unless the user explicitly asks to fix review findings.
- Do not silently modify the tracking document. If it is inaccurate, record the mismatch in the review report and mention that the tracking document should be updated.
- Distinguish requirement gaps, document-code mismatches, test gaps, and unconfirmable items.
- Prefer tight file and line references for findings when possible.
- Keep the review report in Chinese.

## Review Conclusions

Use one of these conclusions:

- `通过`：验收标准有足够代码和验证证据支撑，未发现阻塞问题。
- `有条件通过`：核心目标达成，但存在非阻塞文档偏差、测试缺口或低风险后续项。
- `不通过`：存在未实现、实现错误、范围偏差、关键验证缺失或交付风险。
- `无法确认`：缺少追踪文档、代码上下文、测试证据或必要环境，无法可靠判断。
- `阶段性审查`：需求尚未完成，报告当前完成度、缺口和交接风险。

## Reference map

- Read `references/需求达标审查报告模板.md` when creating or refreshing the review report.
- Read `references/审查清单.md` while comparing the tracking document with workspace code.
