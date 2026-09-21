---
name: financial-due-diligence-analysis
description: "Use when an investment project has financial statements, ledgers, spreadsheets, pasted financial tables, or manually entered financial data and the team needs financial due-diligence analysis, ratio calculations, cash-flow and working-capital review, anomaly identification, or a structured list of missing financial evidence."
---

# Financial Due Diligence Analysis

Help an investor analyze supplied financial evidence during due diligence. The Agent can organize data, calculate transparent metrics, reconcile related figures, surface unusual patterns, test forecast assumptions, and prepare questions and follow-up requests. It is an analysis and evidence-management workflow, not an audit or an accounting opinion.

## 输出语言

默认所有面向用户的报告、分析、表格标题、字段显示名、问题、结论、建议、警示和解释均使用简体中文。用户明确要求其他语言时才切换。公司/人名、官方机构和产品名、文件名、URL、代码、公式、JSON/YAML键、稳定ID，以及必要的专业缩写（如 DCF、EBITDA、IRR、MOIC）可以保留原文；首次出现的专业缩写要附中文释义。机器可读字段或状态值可以保留英文，但旁边必须有中文说明；若 JSON 或表格也直接面向用户，必须同时提供对应的中文显示值或中文说明。原始材料引文可保留原语言，Agent 的分析和结论必须使用中文。

**REQUIRED SHARED CONTRACT:** Use [due-diligence-workspace-and-issue-ledger](../due-diligence-workspace-and-issue-ledger/SKILL.md) for stable issue IDs, evidence lifecycle, cross-domain reconciliation, investment-impact fields, downstream feeds, and change history. Financial anomalies and adjustments are domain evidence; they are not a separate decision ledger.

## Boundary

This skill must not:

- issue an audit opinion, assurance conclusion, tax opinion, fraud finding, or accounting-policy ruling;
- call a project financially sound or financially failed from a single ratio or incomplete dataset;
- invent missing figures, silently change accounting periods, mix currencies or units, or aggregate incompatible entities;
- treat management accounts, forecasts, or a pasted number as independently verified;
- normalize earnings by deleting an inconvenient item without recording the source, rationale, recurrence assessment, and professional review need;
- use a universal industry threshold when the business model, stage, accounting basis, or comparable set is unknown.

## Inputs

Read as much as is available:

- the current due-diligence workspace and financial requests;
- original financial statements, audit reports, trial balances, general-ledger extracts, bank/tax materials, invoices, AR/AP aging, inventory records, debt schedules, budgets, and forecasts;
- structured files such as XLSX, CSV, or JSON, or tables pasted by the user;
- the project card, BP, initiation report, meeting answers, and transaction assumptions for context only.

If a financial dataset is missing or too thin, use [references/financial-data-entry-template.md](references/financial-data-entry-template.md). Ask for the smallest additional dataset needed for the next useful analysis instead of producing invented ratios.

## Operating model

1. **Fix the scope.** Record entity, consolidation scope, period, frequency, currency, units, accounting basis, source, version, and whether figures are audited, management-prepared, forecast, or manually entered.
2. **Assess data quality before calculating.** Check completeness, period continuity, unit/currency consistency, statement totals, cash roll-forward, balance-sheet balance, source traceability, and whether detailed tables reconcile to reported totals. Label missing, approximate, derived, and conflicting fields.
3. **Create a normalized analysis layer.** Preserve the original values and keep any transformations in a separate layer. Do not overwrite supplied figures. Map revenue, cost of sales, operating expenses, D&A, interest, tax, net income, cash flow, working capital, debt, capex, related parties, and customer/product dimensions when available.
4. **Calculate only supported metrics.** Use the formulas and caveats in [references/financial-analysis-contract.md](references/financial-analysis-contract.md). Show numerator, denominator, period, unit, and source for material metrics. Mark ratios as unavailable when the denominator or accounting basis is unsuitable.
5. **Analyze the business, not just the ratios.** Review growth, gross margin, operating leverage, cash conversion, working capital, customer/product concentration, debt and liquidity, capex, burn/runway, unit economics, and forecast-to-actual variance. Use history, management targets, or genuinely comparable benchmarks only when their basis is explicit.
6. **Separate signal from conclusion.** For every anomaly state the evidence, comparison base, possible explanations, decision impact, and next verification step. An anomaly is not proof of error, fraud, or misconduct.
7. **Review earnings quality and adjustments.** Create an adjustment ledger for one-off income/expense, related-party items, unusual revenue, capitalization, grants, or non-cash items. Show reported and adjusted views side by side, with confidence and professional-review status.
8. **Stress the forward view.** Compare forecast assumptions with historical conversion, capacity, pricing, margin, working capital, and cash needs. Produce scenario ranges only from explicit assumptions; do not turn a scenario into a prediction.
9. **Write the follow-up package.** Convert every material gap or unexplained variance into a financial question, evidence request, owner, status, and acceptance criterion. Update the shared due-diligence workspace when one exists.
10. **Self-audit.** Check that no result depends on an unmarked assumption, no unsupported precision is shown, every material number is traceable, and professional judgment is routed to an accountant, auditor, tax adviser, lawyer, technical expert, or investor as appropriate.
11. **Maintain the shared investment-impact ledger.** Convert each material anomaly, data-quality failure, disputed adjustment, debt-like item, forecast dependency, or cash-need finding into a shared issue record or link it to an existing cross-domain issue. Separately record effects on investability, valuation, transaction structure, closing, investor-protection terms, and post-close monitoring; use `unknown` where the data does not support a conclusion.
12. **Prepare downstream decision inputs.** Produce traceable feeds for valuation, investment terms, and the investment committee, including normalized revenue/EBITDA/FCF ranges, debt-like items, working-capital adjustments, financing need/runway, forecast-confidence constraints, and conditions for relying on the data. Link every feed to issue IDs and assign a human owner.

## Evidence labels and status

Keep these distinctions visible:

- `reported`: copied from a supplied statement or schedule;
- `management_prepared`: supplied by management without audit evidence;
- `forecast`: forward-looking assumption or plan;
- `derived`: calculated from stated inputs;
- `normalized`: adjusted view with a documented adjustment ledger;
- `externally_supported`: corroborated by bank, tax, customer, contract, or other independent evidence;
- `conflict`: materially inconsistent values or definitions;
- `not_calculable`: missing or incompatible inputs.

Use analysis statuses such as `not_started`, `data_incomplete`, `calculable_with_caveats`, `under_review`, `needs_management_explanation`, `needs_professional_review`, and `ready_for_investor_review`. Do not use `verified` or `cleared` unless the required independent or professional review has actually happened.

## Required output

Return these sections in order. Use [references/financial-analysis-contract.md](references/financial-analysis-contract.md) for the field contract and formulas.

1. **财务尽调分析报告** — scope, data basis, concise financial picture, and limitations.
2. **数据质量与口径检查** — sources, coverage, reconciliation tests, missing fields, conflicts, and whether each result is calculable.
3. **核心指标与趋势** — revenue, growth, gross margin, operating margin/EBITDA where supported, cash-flow conversion, working capital, liquidity, leverage, customer/product mix, and unit economics where relevant.
4. **盈利质量与现金流分析** — reported versus adjusted view, one-off/related-party items, accrual-to-cash bridge, cash burn/runway, and explanations still required.
5. **营运资本、负债与资金需求** — AR/AP/inventory, cash conversion, debt/guarantees, capex, financing need, and downside cash runway.
6. **异常与待核验事项** — evidence-linked anomaly register with priority, possible explanations, impact, owner, and next evidence.
7. **财务资料补充清单与人工复核建议** — missing data, acceptable evidence, calculation template fields, and items for accountant/auditor/tax adviser/investor review.
8. **当前财务尽调问题与投资影响台账** — shared issue IDs, anomaly/adjustment links, evidence quality, status, resolution condition, and separate impact on investability, valuation, structure, closing, terms, and post-close monitoring.
9. **财务尽调下游决策输入** — traceable financial ranges, sensitivities, constraints, and unresolved questions for valuation, investment terms, and the investment committee.
10. **当前财务尽调状态** — one of `not_started`, `data_incomplete`, `calculable_with_caveats`, `under_review`, `needs_management_explanation`, `needs_professional_review`, or `ready_for_investor_review`, with the reason and next smallest action.

If structured output is supported, also maintain the JSON workspace in the reference. Markdown and JSON must agree on periods, values, status, anomalies, adjustments, and open requests.

## Decision discipline

The result is an input to financial due diligence and investment judgment. State what the data shows, what it may imply, what it does not prove, and what a human must verify. When the data is insufficient, a high-quality result is a transparent data gap plus a usable input template—not a complete-looking financial conclusion.
