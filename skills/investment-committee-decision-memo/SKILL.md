---
name: investment-committee-decision-memo
description: "Use when a project has completed enough initiation, diligence, valuation, returns, and transaction-terms work to prepare an investment-committee decision package or approval memo."
---

# Investment Committee Decision Memo

Synthesize the project evidence, diligence findings, forecast, valuation, exit returns, proposed investment terms, conditions, and unresolved risks into a decision-ready investment-committee package. The Agent organizes and reconciles evidence and drafts the memo. The investment committee retains the decision.

## 输出语言

默认所有面向用户的投决会报告、摘要、表格标题、字段显示名、问题、结论、建议、条件、警示和解释均使用简体中文。用户明确要求其他语言时才切换。公司/人名、官方机构和产品名、文件名、URL、代码、公式、JSON/YAML键、稳定ID，以及必要的专业缩写（如 DCF、EBITDA、IRR、MOIC）可以保留原文；首次出现的专业缩写要附中文释义。机器可读字段或状态值可以保留英文，但旁边必须有中文说明；若 JSON 或表格也直接面向用户，必须同时提供对应的中文显示值或中文说明。原始材料引文可保留原语言，投决会分析和结论必须使用中文。

**REQUIRED SHARED CONTRACT:** Read [due-diligence-workspace-and-issue-ledger](../due-diligence-workspace-and-issue-ledger/SKILL.md). Every material conclusion, condition, risk, valuation input, return scenario, and term must link to source issue IDs, downstream feed IDs, or original evidence refs.

## Boundary

Do not:

- manufacture a positive recommendation from an incomplete data room;
- hide unresolved P0/P1 items in prose or treat management explanations as verification;
- average conflicting valuations or return scenarios without explaining the method;
- present a candidate legal term as agreed or a professional review as completed;
- use a single IRR/MOIC case as the investment conclusion;
- convert the memo into a legal, audit, tax, technical, or regulatory opinion;
- create approval conditions that are not linked to an issue, decision need, or owner.

## Inputs

Read the latest versions of:

- project card, initiation memo, meeting updates, and shared workspace;
- commercial, financial, legal, and other diligence outputs plus issue/impact ledgers and reconciliations;
- financial forecast, valuation methods/ranges, ownership/dilution, exit-return scenarios, and model checks;
- proposed investment terms, term-risk map, counsel comments, transaction structure, and approval authority;
- investment mandate, ticket limits, concentration limits, stage/geography preferences, and required committee format if supplied.

If a critical input is missing, state that explicitly and route the decision to `defer`, `conditional approval`, or `no-go pending evidence`. Do not make the gap disappear by summarizing it less prominently.

## Decision architecture

Assess the project through six separate questions:

1. **Thesis:** Is there an evidence-supported reason to invest, and what must remain true?
2. **Business:** Is the market, product, customer demand, competition, execution, and scalability sufficiently supported?
3. **Financial:** Are revenue quality, margins, cash need, forecast credibility, and downside survivability sufficient?
4. **Legal and transaction:** Can the investor obtain valid ownership and protections, and can identified legal risks be resolved or allocated?
5. **Economics:** Is the entry valuation, ownership, dilution, terms, and expected return acceptable under base/downside/upside scenarios?
6. **Decision and conditions:** Should the committee approve, approve conditionally, defer, or reject? What exact evidence, remediation, or approval is required?

## Operating workflow

1. **Freeze the decision snapshot.** Record as-of date, data-room version, model version, valuation date, term version, and any stale inputs.
2. **Build the evidence and issue summary.** Separate verified/independently supported evidence, management claims, forecasts, open questions, conflicts, and human-review items. Summarize P0/P1 issues first.
3. **Reconcile cross-domain facts.** Check commercial claims versus financial revenue, legal IP ownership versus technical value, debt/claims versus financial liabilities, cap table versus ownership model, and terms versus counsel/legal constraints.
4. **Test investment economics.** Show entry valuation and dilution, funding use, ownership, exit assumptions, proceeds, MOIC/IRR or unavailable status, and sensitivities. Explain which assumptions drive the result.
5. **Assess risk allocation.** For each material issue identify resolve-before-close, condition precedent, term protection, post-close monitoring, or no-term-substitute. Confirm owner and deadline.
6. **Form a recommendation route.** Use only the available evidence to draft one of `approve`, `approve_with_conditions`, `defer`, or `reject`. The rationale must be tied to decision questions and not overstate certainty.
7. **Prepare the committee questions.** List decisions the committee must make, trade-offs, dissent points, conflicts, and information that cannot be delegated to the Agent.
8. **Maintain an approval log.** Record committee decision, conditions, owners, deadlines, deviations from the proposed terms, and post-approval monitoring items. A future update is a new version, not a silent rewrite.

## Required output

Return these sections in order:

1. **投决会结论摘要** — proposed route, requested amount/instrument, valuation/ownership, key rationale, and top unresolved items.
2. **项目与投资逻辑** — company, stage, product, market, thesis, catalysts, and what must be true.
3. **尽调发现与风险** — commercial, financial, legal, and other findings; issue status; cross-domain conflicts; and limitations.
4. **财务预测、估值与退出收益** — base/downside/upside, valuation range, dilution, funding need, exit proceeds, MOIC/IRR, and key sensitivities.
5. **投资条款与风险分配** — proposed terms, conditions precedent, representations/indemnities, governance/information, milestones, and post-close protections.
6. **反对意见与不确定性** — strongest bear case, evidence that could disprove the thesis, model limitations, and what is not verified.
7. **投决会需要决定的事项** — explicit approval questions and alternatives.
8. **交割前条件与投后监控** — owner, deadline, evidence standard, and escalation route.
9. **附录与来源索引** — source files, issue IDs, feed IDs, model version, term version, and change log.

If structured output is supported, maintain [references/investment-committee-contract.md](references/investment-committee-contract.md). A memo is not complete if Markdown and structured output disagree on recommendation route, amount, valuation, ownership, conditions, or unresolved P0/P1 issues.

## Quality bar

The committee should be able to see quickly what is being approved, why it may work, what can break, how much capital is at risk, what rights protect the investor, and what must happen before or after closing. The memo should make uncertainty visible rather than making the project look more complete than the evidence allows.
