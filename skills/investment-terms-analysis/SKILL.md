---
name: investment-terms-analysis
description: "Use when an equity investment project needs investor-protection terms, a term-sheet issue list, negotiation preparation, or a mapping from diligence findings and valuation uncertainty to transaction structure."
---

# Investment Terms Analysis

Translate the investment decision, valuation range, diligence issue ledger, financing need, ownership objectives, and risk allocation into a structured investment-terms work package. The Agent can organize term options, explain their purpose, identify negotiation dependencies, and prepare a term-sheet comparison for investor and counsel review. It must not approve, negotiate, or give a legal opinion on final terms.

## 输出语言

默认所有面向用户的条款清单、条款解释、风险映射、谈判准备和投决会输入均使用简体中文。用户明确要求其他语言时才切换。公司/人名、官方机构和产品名、文件名、URL、代码、公式、JSON/YAML键、稳定ID，以及必要的专业缩写可以保留原文；首次出现的专业缩写要附中文释义。机器可读字段或状态值可以保留英文，但旁边必须有中文说明；若 JSON 或表格也直接面向用户，必须同时提供对应的中文显示值或中文说明。原始合同或材料引文可保留原语言，Agent 的分析、候选条款和建议必须使用中文。

**REQUIRED SHARED CONTRACT:** Read [due-diligence-workspace-and-issue-ledger](../due-diligence-workspace-and-issue-ledger/SKILL.md). Each proposed term or term gap must link to the issue IDs, valuation feeds, ownership calculations, and decision questions that justify it.

## Boundary

Do not:

- invent a market-standard term and present it as mandatory;
- convert a candidate protection into a negotiated or enforceable right;
- draft final legal language without transaction counsel and governing-law context;
- hide a valuation disagreement inside a liquidation preference, ratchet, redemption, or veto right;
- recommend a term without stating whose risk it allocates, the trigger, economic effect, duration, and trade-off;
- treat all P0/P1 diligence findings as grounds for a term when the issue may instead require a no-go decision or remediation before closing;
- calculate ownership from headline percentages without stating pre/post-money, option pool, primary/secondary mix, conversion, and fully diluted basis.

## Inputs

Read the latest:

- project card, initiation memo, updated project card, shared diligence workspace, issue ledger, and domain downstream feeds;
- financial forecast/valuation workspace, entry and exit return scenarios, funding need, dilution and ownership analysis;
- proposed instrument, investment amount, valuation or price range, target ownership, expected close, jurisdiction, and investor mandate;
- corporate/governance materials, existing shareholder rights, prior financing terms, debt/security, cap table, option/incentive arrangements, and material legal issues;
- user-supplied term sheet or draft documents. If absent, produce a discussion framework, not a final term sheet.

## Operating workflow

1. **Set the transaction frame.** State instrument, entry date, valuation basis, investment amount, primary/secondary split, share basis, target ownership, expected exit, jurisdiction, and unresolved context gaps.
2. **Build a risk-to-term map.** For each material diligence issue, state the observed fact, uncertainty, investment consequence, candidate term or alternative action, trigger, beneficiary, owner, and link to source issue IDs. Distinguish `remediate_before_close`, `condition_precedent`, `term_protection`, `post_close_monitoring`, and `no_term_substitute`.
3. **Cover the term categories.** Consider economics, instrument mechanics, capitalization and dilution, liquidation/exit economics, governance and reserved matters, information/reporting, founder/key-person obligations, transfer and exit rights, follow-on/anti-dilution, conditions precedent, representations/warranties, indemnity/escrow/holdback, covenants, defaults, and dispute/governing law. Include only categories relevant to the project.
4. **Separate candidate levels.** Label every item as `must_resolve_before_term`, `required_protection`, `negotiation_preference`, `fallback`, or `not_applicable`. State what evidence or human approval is needed to move it forward.
5. **Model economic effects.** Show how price, option-pool treatment, liquidation preference, conversion, anti-dilution, redemption, secondary shares, or tranche/milestone mechanics affect ownership and returns under the same scenarios used by the valuation Skill. Do not use a term to manufacture a desired IRR without exposing the cost to other holders.
6. **Check enforceability and conflicts.** Route legal validity, tax, accounting, regulatory, and company-law questions to counsel or specialists. Flag conflicts among the term proposal, cap table, debt documents, prior investor rights, and diligence findings.
7. **Prepare negotiation sequence.** Identify opening position, rationale, evidence, fallback, walk-away trigger, dependencies, and approval owner. Keep confidential negotiation preferences separate from the general issue ledger when the user requests it.
8. **Feed the investment committee.** Summarize economics, downside protection, unresolved conditions, dilution, governance, and what must be approved. Link each item to evidence and a human decision.
9. **Update iteratively.** Preserve version history and explain what changed, why, and how the valuation/return/decision outputs changed.

## Investor term categories

| Category | Questions to analyze | Typical diligence links |
|---|---|---|
| Economics | What price/valuation, amount, ownership, and dilution are supported? | valuation feeds, cap table, financial forecast |
| Instrument | Common/preferred equity, convertible, staged funding, or another form? | jurisdiction, financing need, legal feasibility |
| Liquidation and exit | What happens on sale, liquidation, down round, or low-return exit? | exit model, seniority, prior rights |
| Governance | Board seat/observer, reserved matters, consent thresholds, deadlock? | founder control, related parties, execution risk |
| Information | What reporting, inspection, budget, audit, and forecast rights are needed? | financial data quality, monitoring issues |
| Founder and key people | Full-time, IP assignment, non-compete/confidentiality, vesting, good/bad leaver? | legal/key-person/IP issues |
| Transfer and follow-on | ROFR/ROFO, tag/drag, pre-emption, pro rata, transfer restrictions? | cap table, exit route, future financing |
| Conditions and protection | What must be fixed or evidenced before close? What is an appropriate representation, indemnity, escrow, holdback, or covenant? | P0/P1 legal, commercial, financial issues |
| Milestones and tranches | What objective milestone justifies release of later funding? | forecast, technical/commercial validation, use of funds |

## Required output

Return these sections in order:

1. **交易背景与经济框架** — instrument, valuation, amount, ownership, primary/secondary mix, share basis, and key assumptions.
2. **尽调问题到投资条款映射** — issue ID, finding/uncertainty, investment impact, candidate response, trigger, and alternative if no term is appropriate.
3. **投资条款清单** — category, proposed position, purpose, trigger, economic/legal dependency, priority, owner, and status.
4. **经济条款与收益影响** — entry price, dilution, liquidation/exit scenarios, staged funding, and effect on investor/company/founders where calculable.
5. **治理、信息与投后保护** — rights, reporting, reserved matters, key-person and use-of-funds monitoring.
6. **交割条件与法律复核事项** — conditions precedent, representations, indemnities, escrow/holdback, consents, and counsel questions.
7. **谈判准备** — opening position, rationale, fallback, walk-away condition, and approval owner.
8. **投决会输入** — decisions required, unresolved issues, expected downside, and recommended approval route. This is not the final investment decision.

If structured output is supported, maintain the contract in [references/investment-terms-contract.md](references/investment-terms-contract.md). Markdown and JSON must agree on term IDs, linked issue IDs, status, economic assumptions, and human owners.

## Quality bar

Every term should answer “what risk does this address, what is the trigger, who bears the cost, how does it interact with valuation and exit returns, and who must approve it?” If those answers are unavailable, label the item as a discussion question rather than a recommendation.
