---
name: financial-forecast-and-valuation
description: "Use when an equity investment project needs a stage-appropriate operating forecast, three-statement model, company valuation, investor ownership analysis, or exit-return scenario from diligence evidence and user-supplied assumptions."
---

# Financial Forecast and Valuation

Build a traceable financial model from the project's verified evidence, diligence findings, interview assumptions, transaction terms, and explicitly marked management inputs. The model connects business drivers to forecast statements, valuation methods, investor ownership, and exit returns. It is a decision-support model, not an audit, fairness opinion, or promise of investment performance.

## 输出语言

默认所有面向用户的报告、模型说明、表格标题、字段显示名、问题、结论、建议、警示和解释均使用简体中文。用户明确要求其他语言时才切换。公司/人名、官方机构和产品名、文件名、URL、代码、公式、JSON/YAML键、稳定ID，以及必要的专业缩写（如 DCF、EBITDA、IRR、MOIC）可以保留原文；首次出现的专业缩写要附中文释义。Excel 公式、机器可读字段和状态值可以保留英文，但工作簿中的人类可读标签和解释必须使用中文；若 JSON 或表格也直接面向用户，必须同时提供对应的中文显示值或中文说明。原始材料引文可保留原语言，Agent 的分析和结论必须使用中文。

**REQUIRED SHARED CONTRACT:** Read [due-diligence-workspace-and-issue-ledger](../due-diligence-workspace-and-issue-ledger/SKILL.md). Every material forecast or valuation assumption inherited from diligence must link to source evidence or an issue/feed ID. If an issue is unresolved, carry its uncertainty into a range, scenario, sensitivity, or unavailable result.

## Boundary

Do not:

- turn a BP, management forecast, or Agent scenario into historical fact;
- use a single precise valuation when the method, date, capital structure, net debt, or key assumptions are uncertain;
- apply DCF to a pre-revenue company as though long-term cash flows were observable;
- mix enterprise value, equity value, pre-money, post-money, fully diluted ownership, and investment amount without labeling each bridge;
- hide missing data through `IFERROR(...,0)`, plugs, unexplained balancing items, or invented benchmark inputs;
- treat IRR/MOIC as a recommendation or imply that an exit is guaranteed;
- accept a valuation or return result without showing the human decision inputs and unresolved issues behind it.

## Inputs

Read the latest available:

- project card, initiation research, meeting updates, shared diligence workspace, issue ledger, and downstream feeds;
- BP and company materials, preserving the distinction between disclosed facts, management claims, commitments, forecasts, and Agent inference;
- historical financial statements or structured user data, including entity scope, period, currency, accounting basis, and audit status;
- business-driver evidence: capacity, customers, pipeline, price, volume, utilization, unit economics, headcount, capex, working capital, financing need, and milestones;
- transaction assumptions: instrument, investment amount, price or valuation, ownership target, option pool, liquidation preferences, follow-on rights, and expected exit timing;
- user-supplied comparable companies/transactions, discount rates, terminal assumptions, or sector parameters. If not supplied, create a request or a clearly labeled illustrative assumption rather than silently searching or inventing.

## Select the model path

Classify the project before choosing methods. Use multiple paths only when each answers a different question.

| Situation | Forecast emphasis | Valuation / return methods to consider |
|---|---|---|
| Pre-revenue or pre-commercialization | runway, milestone funding, capacity or pipeline conversion, headcount, capex, scenario dates | venture method, milestone/scorecard, relevant transactions, cost-to-duplicate as a sanity check; DCF only as an illustrative sensitivity |
| Early revenue with uncertain conversion | driver-based revenue bridge, gross margin, burn, working capital, customer concentration | revenue/GMV/ARR or transaction multiples, venture method, scenario DCF only if assumptions are explicit |
| Growth company with repeatable cohorts or orders | cohorts, bookings-to-revenue, pricing, retention, margin expansion, cash conversion | DCF, trading/transaction comparables, venture method, ownership and dilution scenarios |
| Mature or asset-intensive business | full three statements, maintenance/growth capex, debt, working capital, tax, normalized earnings | DCF, EBITDA/EBIT multiples, asset or transaction comparables, LBO/returns where relevant |

Then adapt the driver tree to the business: product × price × volume, capacity × utilization × yield × price, customer cohort × retention × ARPU, transaction volume × take rate, project backlog × conversion × delivery, or another evidence-supported structure.

## Operating workflow

1. **Fix the scope and date.** Record entity perimeter, forecast start, historical periods, forecast horizon, currency, units, nominal/real basis, tax basis, scenario labels, and valuation date. A missing scope is an open issue.
2. **Create an evidence-to-assumption map.** For each material driver record the value, unit, period, source ref, evidence type, confidence, linked issue/feed IDs, owner, and what would change it. Separate actuals, management case, Agent case, and user override.
3. **Build the operating forecast.** Use visible driver schedules for revenue, COGS/gross margin, headcount/payroll, opex, capex/depreciation, working capital, debt/interest, tax, and cash. Use supported formulas and do not force the balance sheet to tie with an unexplained plug.
4. **Use scenarios deliberately.** Keep one authoritative case selector or an explicitly documented scenario comparison. Base, downside, and upside must differ through named assumptions, not arbitrary valuation multiples only. Mark which scenario is management-provided versus analyst-built.
5. **Run quality checks.** Reconcile historical source data, period/currency/entity scope, revenue recognition timing, cash roll-forward, balance sheet, debt, equity, capex/depreciation, working capital, and forecast-to-actual bridges. Missing or failed checks remain visible.
6. **Choose and apply valuation methods.** For each method state applicability, valuation date, operating metric, multiple/discount rate source, terminal method, net debt and dilution bridge, and limitations. Use ranges and sensitivities for material uncertainty. Reconcile methods without averaging them mechanically.
7. **Model the financing and ownership bridge.** Show pre-money/post-money, primary versus secondary proceeds, new shares or conversion, option pool, investor ownership, founder/other holder dilution, and any preference or instrument mechanics supplied by the user. Do not infer legal terms.
8. **Model exit returns.** For each exit scenario show exit date, exit metric, exit multiple or equity value, net debt/cash, investor ownership, proceeds, fees/taxes if provided, cash flows, MOIC, IRR/XIRR, and sensitivity to entry valuation, dilution, exit value, and timing. State that this is scenario analysis.
9. **Feed downstream decisions.** Publish structured feeds for investment terms and the investment committee. Link each conclusion to source issue IDs and identify what is still a human decision.
10. **Update, do not overwrite.** On a new data round, preserve the prior model version, change log, changed assumptions, and effect on valuation/returns. Never replace a historical actual or prior case silently.

## Required output

Return these sections in order:

1. **模型范围与输入状态** — stage, entity/period scope, data coverage, source quality, valuation date, and missing inputs.
2. **商业假设到财务预测的映射** — driver tree, evidence refs, issue/feed IDs, scenarios, and uncertainty.
3. **财务预测结果** — revenue, gross profit, opex, EBITDA/EBIT where supported, cash flow, working capital, capex, debt, cash, and funding need.
4. **估值分析** — applicable methods, valuation ranges, bridge to equity value, dilution, and sensitivity.
5. **投资人持股与退出收益测算** — entry, ownership, exit scenarios, proceeds, MOIC, IRR/XIRR, and limitations.
6. **估值与收益相关的尽调问题** — open issue IDs, evidence gaps, conflicts, and what would change the model.
7. **下游输入** — structured feeds for investment terms and investment committee review, with human owner and status.
8. **模型状态与下一步** — `data_incomplete`, `illustrative`, `under_review`, `ready_for_human_review`, or `superseded`, with the smallest next action.

If a workbook is requested, create a formula-driven `.xlsx` with the reader-facing summary first and distinct **假设、预测、估值、退出收益、检查、来源** areas only where each has a clear role. The workbook must expose inputs, formulas, units, scenario selection, data gaps, source refs, and checks. Markdown and workbook outputs must agree on the model date, cases, valuation ranges, ownership, and returns.

## Model contract

Read [references/financial-forecast-and-valuation-contract.md](references/financial-forecast-and-valuation-contract.md) for the structured records, formulas, stage routing, and downstream feed schema. Use [references/valuation-method-routing.md](references/valuation-method-routing.md) when the project stage or business model makes method selection non-obvious.

## Quality bar

The model should make it easy for a human to answer: “Which business assumptions drive the value, what evidence supports them, what breaks in the downside, how much capital is needed, what ownership and protections follow, and what return is possible under each exit scenario?” If the answer cannot be traced, the correct output is a transparent gap or range, not false precision.
