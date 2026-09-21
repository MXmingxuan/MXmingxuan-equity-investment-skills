---
name: due-diligence-workspace-and-issue-ledger
description: "Use when commercial, financial, legal, or other due-diligence workstreams need shared evidence state, persistent issue tracking, cross-domain reconciliation, or structured inputs for valuation, investment terms, or an investment-committee decision."
---

# Due Diligence Workspace & Issue Ledger

Maintain the shared state that connects due-diligence evidence to investment decisions. This is the common layer for the commercial, financial, legal, and future specialist diligence Skills. It preserves the difference between a question, an evidence gap, a finding, a conflict, a risk, a decision impact, and a proposed next action.

## 输出语言

默认所有面向用户的摘要、台账说明、问题、影响解释、下一步和决策输入均使用简体中文。用户明确要求其他语言时才切换。稳定ID、JSON/YAML键、机器状态值、代码、公式、URL、文件名和必要的专业缩写可以保留英文，但面向用户的字段说明和解释必须使用中文；若 JSON 或表格也直接面向用户，必须同时提供对应的中文显示值或中文说明；原始引文可以保留原语言。

This Skill coordinates evidence and downstream inputs. It does not perform commercial, financial, legal, tax, technical, valuation, or investment-committee judgment.

## Boundary

It must not:

- replace a domain Skill's professional analysis;
- mark an issue resolved merely because management supplied an explanation;
- turn a candidate protection route into an approved legal term;
- merge conflicting evidence into one value;
- infer that an empty issue list means no risk;
- produce a final investment recommendation without the required human decision process.

## Inputs

Read the current project card, initiation workspace, due-diligence intake, and every available domain workspace. On later rounds, load the prior structured workspace first and apply new material as a change, not as a replacement.

## Operating model

1. **Load and preserve state.** Keep stable IDs, source references, prior values, statuses, owners, and change history.
2. **Normalize domain records.** Convert commercial hypotheses, financial anomalies/adjustments, legal issues, and specialist findings into the shared issue model in [references/issue-and-impact-contract.md](references/issue-and-impact-contract.md).
3. **Separate the layers.** Keep `question`, `evidence`, `finding`, `conflict`, `decision_impact`, and `candidate_action` as distinct fields. A finding can have several evidence items; an issue can remain open while its evidence is complete but professional judgment is pending.
4. **Map investment impact.** For every material issue, record separate effects on investability, valuation, ownership/price/instrument, closing, investor-protection terms, and post-close monitoring. Use `unknown` where the evidence is insufficient.
5. **Reconcile across workstreams.** Link related issues rather than copying them. Surface contradictions such as customer claims versus revenue, IP ownership versus technical value, or debt/claims versus financial statements.
6. **Prepare downstream feeds.** Produce a traceable set of inputs for future valuation, investment-terms, and investment-decision Skills. Each feed must link to source issue IDs and preserve assumptions and uncertainty.
7. **Update iteratively.** When new documents, answers, interviews, or professional reviews arrive, update statuses and add a change-log entry. Do not erase the earlier state.

## Required output

Return these sections in order:

1. **尽调统一工作区摘要** — current scope, workstreams, evidence coverage, and overall state.
2. **统一问题与投资影响台账** — all open, conflicted, resolved, and deferred issues using the shared contract.
3. **跨领域矛盾与依赖** — linked issues that require joint review or prevent a downstream conclusion.
4. **估值、投资条款与投决会输入** — structured downstream feeds with source issue IDs, assumptions, uncertainty, and human owner.
5. **下一步资料与核验任务** — the smallest actions that reduce decision-critical uncertainty.

If structured output is supported, maintain the JSON workspace from the reference. Markdown and JSON must agree on IDs, evidence, issue status, priorities, impact fields, downstream feeds, and change log.
