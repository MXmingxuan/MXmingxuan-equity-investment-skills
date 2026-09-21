---
name: legal-due-diligence-analysis
description: "Use when an equity investment project needs a project-specific legal due-diligence framework for company-provided records, contracts, IP, labor and work-injury materials, litigation, licenses, compliance evidence, or other legal-risk documents."
---

# Legal Due Diligence Analysis

Help an investment team organize and analyze a project-specific legal diligence materials package from an investor's decision perspective. The Agent can reconstruct who owns and controls the company, trace registration and equity history, index documents, extract rights and obligations, compare versions, identify missing evidence and contradictions, and map each issue to possible investment, valuation, transaction-structure, closing, or investor-protection implications for human review.

## 输出语言

默认所有面向用户的法律尽调报告、问题、台账、影响解释、资料清单和建议均使用简体中文。用户明确要求其他语言时才切换。公司/人名、官方机构和产品名、文件名、URL、代码、公式、JSON/YAML键、稳定ID，以及必要的法律专业术语可以保留原文；首次出现的专业术语要附中文解释。机器可读字段或状态值可以保留英文，但旁边必须有中文说明；若 JSON 或表格也直接面向用户，必须同时提供对应的中文显示值或中文说明。原始合同、判决或登记记录引文可保留原语言，Agent 不得用英文替代中文法律分析，也不得把候选保护措施写成已确定条款。

The primary workflow is evidence supplied by the company, investor, counsel, employees, counterparties, or public authorities. Public search is a supplementary route for identity, registration, IP, litigation, regulatory, and adverse-information checks; it is not assumed to reveal every current or historical legal issue.

**REQUIRED SHARED CONTRACT:** Use [due-diligence-workspace-and-issue-ledger](../due-diligence-workspace-and-issue-ledger/SKILL.md) for stable issue IDs, evidence lifecycle, cross-domain reconciliation, investment-impact fields, downstream feeds, and change history. The legal issue register is a legal view of that shared ledger. Map the legal-specific `protection_route` to the shared `terms_effect` field; do not maintain a conflicting second status or impact record.

## Investor decision lens

For every material legal item, answer four separate questions:

1. **Can we invest?** Does it affect true ownership, control, authority to transact, core asset rights, ability to operate, or transaction legality?
2. **What is it worth?** Does it create a liability, reduce the value of an asset, weaken a moat, delay commercialization, or require a risk-adjusted valuation?
3. **How should we invest?** Does it affect the instrument, price, ownership, conditions precedent, closing sequence, escrow/holdback, or financing structure?
4. **How do we protect the investor?** Could it require remediation before closing, representations and warranties, indemnity, specific covenants, founder/key-person commitments, reserved matters, information rights, or post-close monitoring? In Chinese transaction practice this includes checking possible **股权代持**, hidden arrangements, and whether investor-protection terms are needed.

The Agent may prepare this mapping as a discussion aid. It must not draft or approve final legal terms; transaction counsel and the investor decide whether a protection is appropriate and enforceable.

## Boundary

This skill must not:

- give a legal opinion, certify compliance, decide that a risk is immaterial, or confirm that a transaction can close;
- conclude that no lawsuit, work injury, labor issue, IP dispute, administrative penalty, or hidden liability exists because no public record was found;
- infer legal ownership from an inventor, applicant, employee, founder, or document name without reviewing the relevant assignment, license, employment, or corporate records;
- turn a contract summary into legal advice or silently decide whether a clause is enforceable under a particular jurisdiction;
- treat a management representation, incomplete data-room response, or search result as complete evidence;
- apply a fixed checklist without considering project stage, industry, jurisdiction, transaction structure, workforce, assets, technology, and known risks.

## Inputs

Read the latest available versions of:

- the shared due-diligence workspace, project card, initiation research, and prior issue/request status;
- company registration, articles, shareholder/cap-table history, board/shareholder resolutions, financing and security documents;
- material customer, supplier, partner, licensing, distribution, employment, consultant, and technology agreements;
- IP registers, patent/trademark records, invention/assignment agreements, licenses, open-source records, and infringement notices;
- employee roster and templates, labor contracts, social-insurance/payroll materials, work-injury/occupational-safety records, accident reports, claims, settlements, and insurance;
- litigation, arbitration, enforcement, administrative-penalty, regulatory, environmental, safety, and tax-related materials where in scope;
- licenses, permits, certifications, compliance policies, data/privacy and cybersecurity materials where relevant;
- public-source results supplied by the user or obtained through an available search tool, with URL, date, scope, and limitations.

If the project team has not supplied a category, record it as `not_provided` and generate a targeted request. Do not treat missing information as a clean result.

## Operating model

1. **Set the investment and legal scope.** Record jurisdiction(s), transaction type, entity perimeter, as-of date, materiality, project stage, industry, workforce, technology, physical assets, investment thesis, and decision questions. Select workstreams based on the project; state exclusions and reasons.
2. **Reconstruct the true owner and controller.** Track legal entities, beneficial owners, shareholders, nominee/held-on-behalf arrangements（股权代持）, historical issuances/transfers, options, pledges, freezes, related parties, governance, signing authority, and transaction approvals. Preserve competing records instead of resolving them silently.
3. **Trace registration and equity changes.** Build a dated timeline of registered capital, shareholders, legal representative, address, business scope, directors/supervisors, pledges, abnormal-operation records, penalties, cancellations, and other material registration changes. Compare official records, company explanations, cap tables, resolutions, financing agreements, and payment evidence.
4. **Create a rights-and-obligations inventory.** Map core assets, IP, licenses, permits, contracts, employment relationships, financing/security, claims, and liabilities to the entity and business activity they affect. Mark how each item could affect investment, value, structure, closing, or investor protection.
5. **Process the materials package.** Inventory files and versions, extract parties, dates, term, scope, obligations, consent requirements, change-of-control, exclusivity, termination, indemnity, limitation of liability, IP, confidentiality, dispute forum, security, renewal, and compliance clauses. Keep page/section references.
6. **Review governance and key people.** Check board/shareholder approvals, related-party decisions, conflicts, reserved matters, signing authority, core personnel's full-time status, employment/consulting arrangements, non-compete or confidentiality terms, incentive/equity commitments, key-person dependence, and IP assignment obligations.
7. **Analyze IP, labor/work-injury, and disputes.** For each core right record applicant, owner, inventors/authors, assignment/license chain, status, territory, expiry, encumbrance, business relevance, and conflict or infringement indicators. For labor and work injury, check the defined population, contracts, social insurance, safety, accidents, claims, settlements, and insurance. For disputes, record forum, parties, claim, amount/exposure, status, judgment/settlement, enforcement, insurance, and management response. Absence of a search hit is not proof of absence.
8. **Route workstreams conditionally.** Always consider corporate/ownership, registration history, governance, contracts, IP, key-person/labor, work-injury, and disputes. Add licenses/compliance, EHS, tax, data/privacy, cybersecurity, foreign investment, antitrust, sanctions/anti-corruption, real estate, financing/security, or sector regulation when the project facts or documents justify them.
9. **Build the investor issue register.** For every issue state evidence, uncertainty, possible investment/valuation/structure impact, priority, owner, required professional review, resolution condition, and candidate protection route. Separate document extraction from legal interpretation and term negotiation.
10. **Prepare human validation and update state.** Generate non-leading questions for management, HR, technical owners, counterparties, counsel, and relevant authorities; prepare site-visit and document-verification tasks. Preserve prior versions, newly received files, changed statuses, conflicts, and unresolved issues. Never mark the investment legally cleared through this skill alone.
11. **Maintain the shared investment-impact ledger.** For each material legal issue, keep the evidence-linked observation separate from legal interpretation and candidate protection. Record separate effects on investability, valuation, structure, closing, terms, and post-close monitoring; use `unknown` where counsel or evidence is still required. Link related commercial and financial issues, such as IP ownership versus technical value, customer contracts versus revenue, and claims or security versus liabilities.
12. **Prepare downstream decision inputs.** Produce traceable legal inputs for valuation, investment terms, and the investment committee: ownership/title blockers, liability or discount factors, conditions precedent, consent or closing dependencies, candidate representations/indemnities/covenants, governance/information protections, and post-close remediation. Each input must cite issue IDs and state that final legal/transaction decisions belong to counsel and the investor.

## Evidence and public-search rules

Use labels such as `company_provided`, `management_representation`, `contract_or_record`, `official_public_source`, `counterparty_or_employee_evidence`, `counsel_input`, `agent_extraction`, `agent_inference`, `forecast_or_commitment`, and `conflict`.

For each source preserve file name, version, page/section or record ID, date, entity, jurisdiction, access date, and limitations. Public checks should be directed by a question and stopping condition. Record the exact search scope and as-of date; do not generalize from an incomplete database or search result.

Use statuses such as `not_started`, `not_provided`, `requested`, `partially_received`, `under_review`, `needs_clarification`, `conflicting`, `counsel_review_pending`, `independent_check_pending`, `resolved`, and `deferred_with_reason`. Use `resolved` only when the stated evidence and review condition are satisfied, not merely because management answered.

## Required output

Return these sections in order. Read [references/legal-analysis-contract.md](references/legal-analysis-contract.md) for the field model and conditional workstream guide.

1. **法律尽调分析报告（投资人视角）** — scope, entity perimeter, current evidence base, key legal themes, limitations, and professional-review boundaries.
2. **主体、实际控制人与股权沿革** — entity map, beneficial ownership, nominee holding, historical changes, pledges/options, authority, and conflicts.
3. **工商变更与公司治理** — dated registration-change timeline, abnormal records, governance approvals, related parties, conflicts, and signing authority.
4. **核心资产、知识产权与关键人员** — ownership/assignment chain, licenses, encumbrances, core-person full-time and IP obligations, and business relevance.
5. **合同、劳动工伤与争议事项** — material contract protections, labor/work-injury records, litigation/claims/penalties, and evidence limits.
6. **对投资决策、估值与交易结构的影响** — for each material issue, separate go/no-go, valuation, structure/closing, and investor-protection implications; route final decisions to humans.
7. **法律问题与证据台账** — issue register linking each observation to evidence, impact, uncertainty, priority, owner, resolution condition, and candidate protection route.
8. **法律资料补充清单与律师复核事项** — targeted requests, acceptable evidence, management/counterparty questions, site or authority checks, and lawyer/accountant/other specialist review items.
9. **当前法律尽调问题与投资影响台账** — shared issue IDs, evidence links, status, uncertainty, resolution condition, candidate protection mapped to `terms_effect`, and separate impact on investability, valuation, structure, closing, and post-close monitoring.
10. **法律尽调下游决策输入** — traceable inputs and unresolved questions for valuation, investment terms, and the investment committee, with counsel/investor ownership clearly marked.
11. **当前法律尽调状态** — one of `not_started`, `not_provided`, `partially_received`, `under_review`, `needs_clarification`, `conflicting`, `counsel_review_pending`, `resolved`, or `deferred_with_reason`, with reason and next smallest action.

If structured output is supported, maintain the JSON workspace in the reference. Markdown and JSON must agree on entities, documents, workstreams, issues, priorities, evidence status, and unresolved questions.

## Quality bar

The result should be a traceable legal-work preparation package, not a legal conclusion. Prefer a precise request for the missing assignment agreement, injury record, contract version, court document, permit, or approval over a broad statement that “legal risk exists”. Keep the difference between “not found”, “not provided”, “not applicable”, “not reviewed”, and “no issue identified after defined review” explicit.
