---
name: update-project-card-from-meeting
description: "Use when new meeting notes, transcripts, answers, data, commitments, or contradictions arrive after an initial project card and question list, and the investment workspace must be updated without losing prior evidence."
---

# Update Project Card from Meeting

Incrementally update an existing investment workspace after a project-team conversation. The primary deliverable must be named **更新后的项目卡**. Also return **问题状态更新**, **本次变更摘要**, and **新增/未闭环事项**. This is an evidence-reconciliation workflow, not a meeting-summary-only workflow.

## 输出语言

默认**更新后的项目卡**、问题状态更新、变更摘要、新增事项和未闭环事项均使用简体中文。用户明确要求其他语言时才切换。公司/人名、官方机构和产品名、文件名、URL、代码、公式、JSON/YAML键、稳定ID和必要的专业缩写可以保留原文；首次出现的专业缩写要附中文释义。机器可读字段或状态值可以保留英文，但旁边必须有中文说明；若 JSON 或表格也直接面向用户，必须同时提供对应的中文显示值或中文说明。会议原话可保留原语言，但 Agent 的更新、判断和问题状态说明必须使用中文。

## Required inputs

- the prior project card, preferably with source references;
- the prior question list with stable question IDs, if available;
- meeting notes, transcript, recording transcript, email follow-up, or newly supplied data;
- any new files or evidence referenced during the meeting.

If the prior card or question list is missing, state the limitation and reconstruct only what the supplied materials support. Do not present a fresh summary as an update without saying what baseline was unavailable.

## Workflow

1. **Inventory the delta.** Separate prior materials from newly received materials. Record meeting date, participants, speaker attribution, file names, and readability. Do not treat the meeting date as the date of an underlying financial metric.
2. **Map new content to the baseline.** Link each answer, number, promise, or contradiction to an existing project-card field or question ID. If no link exists, create a new issue or question instead of forcing a match.
3. **Classify each update.** Distinguish management statement, historical data, forecast/plan, document-backed evidence, investor interpretation, and commitment. A spoken answer or promise is not independent verification.
4. **Reconcile without erasing history.** Keep the prior value, new value, source, and update status. When a new answer explains a contradiction but does not prove the underlying fact, mark it explained_pending_verification rather than verified. Never silently overwrite a prior figure.
5. **Update question states.** Use the state model in [references/update-contract.md](references/update-contract.md). Mark questions answered, partially answered, answered_unverified, unchanged, superseded, or contradicted. Create stable IDs for new questions and preserve old IDs.
6. **Generate the outputs.** Follow the reference contract. The first section must be titled **更新后的项目卡** and should be a usable current snapshot, not a patchwork of meeting notes. Include a concise change log so the reader can see what changed.
7. **Self-audit.** Check that every changed material field has a source, every closed question has a reason, commitments are not treated as completed evidence, unresolved contradictions remain visible, and no new fact came from model knowledge or imagination.

## Non-negotiable reasoning rules

- Preserve history: prior values are evidence, not disposable drafts.
- A management answer can clarify wording, but it does not independently verify itself.
- A commitment (“会后提供审计报告”) is a follow-up obligation, not a received document.
- “已回答” and “已验证” are different states.
- A number without period, unit, scope, or definition remains incomplete.
- Do not infer that silence means agreement.
- If speakers disagree, retain attribution and show the conflict.
- If the new information changes the project stage, business model, risk, or thesis, flag the downstream impact.

## Output

Return, in this order:

1. **更新后的项目卡** — current structured snapshot with prior and newly supported information distinguished;
2. **问题状态更新** — every prior question affected by the meeting, plus new questions;
3. **本次变更摘要** — material additions, changes, resolved explanations, and newly identified risks;
4. **新增/未闭环事项** — promised documents, remaining contradictions, and next actions.

If structured output is supported, provide JSON using the same field and status contract. Markdown and JSON must agree.
