# Due Diligence Intake Contract

Use this reference when the intake requires a detailed request schema, a structured workspace, or a domain-specific first-pass list. The list is a starting point, not a universal requirement set.

## 1. Decision context

```yaml
workspace_type: due_diligence_intake
workspace_version: "1.1"
project_id: ""
as_of_date: ""
starting_gate: approved_for_formal_diligence | preparing_conditionally | awaiting_initiation_condition | unknown
project_stage: early | growth | mature | mixed | unknown
transaction:
  instrument: equity | preferred_equity | convertible | debt_like | unknown
  target_ticket: ""
  target_ownership: ""
  target_close_window: ""
investment_thesis: []
selected_workstreams: []
excluded_workstreams: []
material_caveats: []
shared_issue_ledger_ref: ""
```

Do not infer instrument, ticket, ownership, or close timing from a BP unless the source clearly says so. A missing value is a decision-context gap, not permission to invent one.

## 2. Request item schema

Every request item should contain:

```yaml
id: DD-COM-001
workstream: commercial | financial | legal | technical_operational | ip | tax | management_hr | esg_ehs | data_cyber | integrity | regulatory | transaction
title: "Short request name"
request: "What should be supplied, checked, or performed?"
purpose: "Which decision question does this answer?"
priority: P0 | P1 | P2
evidence_type: company_document | structured_data | public_source | management_interview | customer_reference | supplier_reference | site_visit | specialist_review | professional_opinion
acceptable_evidence: []
required_period_or_version: ""
entity_scope: ""
collection_route: request_from_company | public_research | interview | site_visit | specialist | investor_input | mixed
suggested_owner: company | investor | agent | accountant | lawyer | technical_expert | tax_adviser | unknown
status: not_requested | requested | partially_received | received | under_review | needs_clarification | independent_check_pending | specialist_review_pending | resolved | deferred_with_reason
dependency_ids: []
agent_roles: [organize | extract | compare | calculate | reconcile | research | draft_questions | no_independent_conclusion]
review_action: "How will the evidence be checked?"
escalation_condition: "What makes this a P0/P1 escalation or human review?"
source_links: []
notes: []
```

`acceptable_evidence` must be concrete. For example, “latest audited financial statements plus trial balance and revenue detail for the same period” is better than “financial information”. The acceptance criteria should preserve currency, units, accounting basis, consolidation scope, date, version, and responsible entity when relevant.

## 3. Workstream routing

### Commercial

Use when the thesis depends on market size, customer adoption, pricing, channels, competition, retention, demand, or growth assumptions. Typical evidence includes customer and order cohorts, sales pipeline definitions, churn/retention data, pricing history, customer concentration, channel economics, competitor comparison, and reference calls. Claims about future demand should be separated from actual orders, signed contracts, and repeat purchases.

### Financial

Use when the decision depends on earnings quality, cash generation, working capital, debt, financing need, unit economics, or forecast credibility. Request source financial statements, trial balance/general ledger extracts, bank and tax evidence where appropriate, revenue and gross-margin detail, AR/AP and inventory aging, debt/guarantee schedules, capex, related-party transactions, and the forecast model with assumptions. The Agent may normalize, reconcile, calculate ratios, and flag anomalies; it must not issue audit assurance.

### Legal

Use when ownership, authority to transact, material contracts, IP rights, licenses, employment, litigation, financing security, data/privacy, or regulatory permissions may affect value or closing. Request corporate records, cap table and historical issuances, board/shareholder approvals, IP registers and assignment agreements, material contracts, licenses, litigation/claim schedules, financing/security documents, and employment/consultant templates. The Agent may index, extract clauses, compare versions, and build an issue tracker; a lawyer owns legal conclusions and opinions.

### Technical and operational

Add for technology, manufacturing, regulated products, infrastructure, biotech, hardware, or projects whose value depends on performance or capacity. Request technical architecture, test reports, yield and quality data, production records, equipment/capacity evidence, supply-chain dependencies, certifications, product roadmap, and site access. Require specialist or on-site validation when desk evidence cannot establish performance.

### Other conditional workstreams

- `ip`: when IP is a core asset or freedom-to-operate matters;
- `tax`: when historical tax treatment, incentives, cross-border structure, or transaction tax affects value;
- `management_hr`: when key-person dependence, incentives, employment compliance, or succession affects execution;
- `esg_ehs`: when environmental permits, safety, labor, community, or reputational exposure is material;
- `data_cyber`: when software, personal data, critical infrastructure, or cyber exposure is material;
- `integrity`: when beneficial ownership, sanctions, corruption, conflicts, or adverse background risk matters;
- `regulatory`: when sector licenses, foreign investment, antitrust, or approval conditions may affect the transaction.

## 4. Priority logic

Use the highest applicable priority rather than scoring everything as urgent:

| Priority | Use when | Typical response |
|---|---|---|
| P0 | Could invalidate the investment thesis, ownership/identity, legal ability to transact, core technical feasibility, customer reality, or transaction fit | Escalate immediately; do not present formal approval as ready while unresolved |
| P1 | Needed to support valuation, terms, investment decision, or a material risk allocation | Resolve before investment decision or convert into explicit closing conditions |
| P2 | Useful for completeness, monitoring, or post-close remediation and does not currently change the core decision | Track with owner and deadline; explain why deferral is acceptable |

## 5. Initial request bank

Use only the rows justified by the project. Adapt names, periods, jurisdictions, and evidence standards.

| Area | Possible first-pass requests |
|---|---|
| Corporate / ownership | Current cap table; historical issuances and transfers; constitutional documents; board/shareholder approvals; beneficial ownership; option or incentive pool |
| Commercial | Product/service breakdown; customer list and concentration; order and revenue bridge; contract and renewal data; pipeline definitions; pricing and discount history; competitor map; customer-reference plan |
| Financial | Monthly/annual statements; trial balance or ledger extract; revenue by product/customer; cost and gross margin detail; AR/AP/inventory aging; cash/debt/guarantees; capex; related parties; forecast model and assumptions |
| Legal / contracts | Material customer/supplier/partner agreements; change-of-control and termination clauses; licenses; litigation and claims; financing/security; employment and consultant agreements |
| IP / technology | IP register; assignments; licenses; open-source inventory; test reports; architecture; product roadmap; third-party dependencies; freedom-to-operate questions |
| Operations / site | Facility and equipment list; capacity and utilization; yield/quality; certifications; key suppliers; production records; EHS permits; site-visit agenda |
| Tax / compliance | Tax filings and notices; incentives; unpaid or disputed taxes; related-party pricing; regulatory approvals; privacy/data and cybersecurity incidents where relevant |
| Management / integrity | Organization chart; key-person roles; incentive arrangements; conflicts; related parties; beneficial ownership; sanctions/adverse-information checks where appropriate |

## 6. Structured workspace shape

When JSON is requested, keep the full request list and state synchronized:

```json
{
  "workspace_type": "due_diligence_intake",
  "project_id": "",
  "as_of_date": "",
  "starting_gate": "",
  "selected_workstreams": [],
  "decision_questions": [],
  "requests": [],
  "first_round_tasks": [],
  "unresolved_items": [],
  "gates": [],
  "issues": [],
  "reconciliations": [],
  "downstream_feeds": [],
  "human_review_items": [],
  "change_log": []
}
```

`decision_questions` should link to request IDs. `unresolved_items` should preserve the original claim, source, conflict or gap, impact, owner, and resolution condition. `change_log` should record newly received documents, changed statuses, closed items, and newly discovered contradictions; never overwrite the earlier state without a trace.

`issues`, `reconciliations`, `downstream_feeds`, and `human_review_items` must follow the shared contract in `due-diligence-workspace-and-issue-ledger`. The intake skill initializes them; domain skills update them.
