---
name: commercial-due-diligence-analysis
description: "Use when an investment project is in formal or conditional commercial diligence and the team needs to test its market, customers, competition, business model, sales conversion, unit economics, supply chain, or commercial growth assumptions using company data, interviews, and public sources."
---

# Commercial Due Diligence Analysis

Help an investment team test whether a company's commercial story is supported by evidence. The Agent can map the business, turn the investment thesis into hypotheses, organize market and competitor research, analyze customer and sales data, prepare interview plans, compare claims with evidence, and maintain a risk/verification register.

## 输出语言

默认所有面向用户的报告、分析、表格标题、字段显示名、问题、结论、建议、警示和解释均使用简体中文。用户明确要求其他语言时才切换。公司/人名、官方机构和产品名、文件名、URL、代码、公式、JSON/YAML键、稳定ID，以及必要的专业缩写（如 DCF、EBITDA、IRR、MOIC）可以保留原文；首次出现的专业缩写要附中文释义。机器可读字段或状态值可以保留英文，但旁边必须有中文说明；若 JSON 或表格也直接面向用户，必须同时提供对应的中文显示值或中文说明。原始材料引文可保留原语言，Agent 的分析和结论必须使用中文。

This is a commercial analysis and evidence-management workflow. It does not replace customer calls, expert interviews, site visits, commercial advisers, or the investor's judgment.

**REQUIRED SHARED CONTRACT:** Use [due-diligence-workspace-and-issue-ledger](../due-diligence-workspace-and-issue-ledger/SKILL.md) for stable issue IDs, evidence lifecycle, cross-domain links, investment-impact fields, downstream feeds, and change history. The commercial issue register is a domain view of that shared ledger, not a separate competing list.

## Boundary

This skill must not:

- declare a market, customer, product, or competitive advantage “validated” from management statements or a single report;
- treat leads, pipeline, samples, pilots, LOIs, or non-binding discussions as orders, revenue, repeat purchases, or customer approval;
- infer customer willingness to pay, retention, product-market fit, or market leadership without an appropriate evidence route;
- invent TAM/SAM/SOM, growth rates, competitor facts, customer names, or conversion rates;
- turn an interview transcript into an independent customer reference when the interview was conducted by management or the investor has not confirmed its provenance;
- issue a technical, legal, regulatory, accounting, valuation, or investment-committee conclusion;
- hide contradictory definitions of market, customer, product, geography, period, or sales stage.

## Inputs

Read the latest available versions of:

- the shared due-diligence workspace, project card, initiation research, and prior question status;
- BP, product/service documents, business plans, pricing, contracts, order data, customer lists, pipeline/CRM exports, retention or cohort data, and unit-economics data;
- management interviews, customer/supplier/expert interview notes or transcripts, site-visit records, and follow-up commitments;
- public market, competitor, policy, technical, procurement, and industry sources when relevant and available;
- the investment thesis, target stage, geography, transaction assumptions, and decision constraints.

If a required input is missing, state the gap and generate the smallest useful request or interview task. Do not fill it with model knowledge.

## Operating model

1. **Set the decision questions.** State what the investment decision depends on: demand, customer adoption, pricing, competitive position, route to market, scalability, unit economics, supply chain, or execution. Link each question to a materiality and a stopping condition.
2. **Map the business.** Describe products/services, target users and economic buyers, value proposition, use cases, value chain, revenue model, pricing, channels, sales cycle, delivery model, key partners, dependencies, and post-sale behavior. Separate source facts, management claims, and Agent inference.
3. **Build a hypothesis and evidence map.** For each important claim record the exact claim, expected evidence, current evidence, evidence quality, contradiction, verification route, owner, and status. Prefer direct operational evidence over promotional language.
4. **Define the market before sizing it.** Fix product boundary, customer boundary, geography, period, currency, inclusion/exclusion, and whether the estimate is revenue, units, capacity, or spend. Use bottom-up and top-down approaches only when their definitions are compatible. Show assumptions and ranges; do not present a single precise number as fact.
5. **Analyze customers and commercialization.** Use an explicit funnel such as lead → qualified opportunity → sample/pilot → technical or procurement approval → signed order/contract → shipment/delivery → recognized revenue → repeat purchase. Analyze conversion, sales cycle, customer concentration, retention, cohort behavior, price realization, payment behavior, and reasons for losses where data exists.
6. **Test competition and substitutes.** Compare like with like: customer segment, use case, product performance, price, total cost, switching cost, certification, channel access, capacity, service, and incumbent behavior. A feature list is not a competitive advantage unless customers or market behavior support it.
7. **Test the commercial model.** Reconcile price, volume, gross margin, customer acquisition, channel cost, sales-cycle length, support cost, capacity, and working-capital assumptions with financial and operational data. Refer financial calculations to `financial-due-diligence-analysis` when that skill is available; do not duplicate conflicting numbers.
8. **Review scalability and dependencies.** Check production/service capacity, suppliers, critical inputs, delivery constraints, quality, implementation, regulatory or certification gates, key-person dependencies, and the gap between current capability and the growth plan.
9. **Use humans for primary validation.** Prepare open-ended customer, supplier, expert, and site-visit questions. Analyze supplied notes after provenance is recorded, but do not claim an interview happened or that a customer confirmed a claim unless the evidence says so.
10. **Update the decision state.** Convert unresolved claims into P0/P1/P2 issues, evidence requests, and owners. State whether the evidence supports, weakens, or does not yet resolve each hypothesis. Keep facts, analysis, and recommendation separate.
11. **Maintain the shared investment-impact ledger.** For each material commercial issue, preserve the observation and evidence refs, then separately record what it may do to investability, valuation assumptions, transaction structure, closing conditions, investor-protection terms, and post-close monitoring. Link related financial or legal issues instead of copying their conclusions. Use `unknown` when the commercial evidence does not support an impact assessment, and route the final judgment to the investor or relevant specialist.
12. **Prepare downstream decision inputs.** Produce traceable feeds for valuation, investment terms, and the investment committee: market/revenue ranges, customer-conversion assumptions, concentration or retention constraints, pricing/unit-economics sensitivities, milestone conditions, and unresolved commercial dependencies. Each feed must cite issue IDs and state uncertainty.

## Evidence and research rules

Use labels such as `management_statement`, `internal_operating_data`, `contract_or_order`, `customer_interview`, `supplier_interview`, `expert_interview`, `public_source`, `site_observation`, `agent_inference`, `forecast_or_commitment`, and `conflict`.

When public research is used, record publisher, URL, publication/access date, relevant passage, market definition, geography, period, and limitations. Prefer primary sources, official statistics, filings, procurement records, technical standards, and direct company or customer evidence. Treat search snippets, company marketing, aggregators, and unsourced rankings as leads or claims. Never claim to have searched when no search tool was used.

Use statuses such as `not_started`, `evidence_requested`, `partially_supported`, `management_claim_only`, `independently_supported`, `conflicting`, `needs_human_validation`, `resolved`, and `deferred_with_reason`. “Independently supported” requires an appropriate independent route; it does not mean the Agent is certain.

## Required output

Return these sections in order. Read [references/commercial-analysis-contract.md](references/commercial-analysis-contract.md) for the field model and detailed routing rules.

1. **商业尽调分析报告** — scope, decision questions, current evidence base, commercial thesis, and limitations.
2. **业务模式与价值链拆分** — product/service, customer, value proposition, revenue model, channel, delivery, dependencies, and critical assumptions.
3. **市场、竞争与替代方案** — defined market boundary, sizing methods, sources, competitor/substitute comparison, and unresolved gaps.
4. **客户、销售与商业化验证** — funnel stage, customer evidence, conversion/retention/concentration, pricing and sales-cycle analysis, and interview limitations.
5. **单位经济性与运营可行性** — price/volume/margin/channel economics, capacity, supply chain, implementation, and scalability; link to financial evidence rather than duplicating it.
6. **假设、证据与异常** — hypothesis register, evidence conflicts, possible explanations, impact, and next validation step.
7. **商业尽调问题与补充资料清单** — targeted data requests, public-research tasks, management questions, customer/supplier/expert tasks, site-visit tasks, owner, priority, and acceptance criteria.
8. **首轮访谈与外部核验计划** — purpose, participants, non-leading questions, probes, evidence to request, provenance, and follow-up sequence.
9. **当前商业尽调问题与投资影响台账** — shared issue IDs, status, priority, evidence, uncertainty, resolution condition, linked issues, and separate impact on investability, valuation, structure, closing, terms, and post-close monitoring.
10. **商业尽调下游决策输入** — traceable inputs and open questions for valuation, investment terms, and the investment committee, each with source issue IDs and a human owner.
11. **当前商业尽调状态** — one of `not_started`, `evidence_requested`, `partially_supported`, `needs_human_validation`, `conflicting`, `resolved`, or `deferred_with_reason`, with reason and next smallest action.

If structured output is supported, maintain the JSON workspace in the reference. Markdown and JSON must agree on hypotheses, market definitions, customer stages, evidence status, and open issues.

## Quality bar

The result should help a human decide what to verify next, not create a persuasive market narrative. Preserve source locations and definitions, show the calculation path for market and unit-economics claims, identify what each evidence route can and cannot prove, and escalate customer, technical, operational, legal, and investment judgments to the appropriate human.
