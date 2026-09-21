# Commercial Analysis Contract

Use this reference when a commercial diligence review needs a structured hypothesis register, market sizing, customer validation, competitor comparison, or synchronized Markdown/JSON state.

## 1. Workspace metadata

```yaml
workspace_type: commercial_due_diligence_analysis
workspace_version: "1.1"
project_id: ""
as_of_date: ""
project_stage: early | growth | mature | mixed | unknown
geography: ""
transaction_context: ""
commercial_thesis: []
decision_questions: []
selected_lenses: []
excluded_lenses: []
shared_issue_ledger_ref: ""
```

Always define the market, customer, product, geography, period, and transaction context before drawing a conclusion. Missing scope is a gap to resolve, not an invitation to use a familiar market definition.

## 2. Hypothesis register

```yaml
hypothesis_id: H-COM-001
question: "What must be true for the commercial thesis to hold?"
claim: "Exact management or investor claim"
materiality: P0 | P1 | P2
linked_decision: ""
expected_evidence: []
current_evidence: []
evidence_labels: []
comparison_base: ""
status: not_started | evidence_requested | partially_supported | management_claim_only | independently_supported | conflicting | needs_human_validation | resolved | deferred_with_reason
possible_explanations: []
what_it_does_not_prove: ""
next_action: ""
owner: investor | company | agent | customer | supplier | expert | adviser | unknown
source_refs: []
```

Good hypotheses are decision-linked and testable: “The target segment will accept the product at a price that supports the planned gross margin” is better than “the market is attractive”.

## 3. Business model map

Keep facts and claims attached to their source:

```yaml
business_model:
  offering: []
  customer_segments: []
  economic_buyers: []
  user_or_use_cases: []
  value_proposition: []
  revenue_model: []
  pricing_and_discounting: []
  channels: []
  sales_cycle: []
  delivery_and_support: []
  key_partners: []
  critical_dependencies: []
  repeat_purchase_or_retention: []
  source_refs: []
  unresolved_items: []
```

For industrial or B2B projects, distinguish technical user, economic buyer, procurement, certifier, channel partner, and final customer. For consumer or marketplace projects, adapt the map to acquisition, activation, engagement, retention, monetization, and supply/liquidity.

## 4. Market sizing record

```yaml
market_estimate_id: MKT-001
market_name: ""
product_boundary: ""
customer_boundary: ""
geography: ""
period: ""
measure: revenue | units | capacity | spend | other
method: top_down | bottom_up | triangulated
value: null
range_low: null
range_high: null
currency_or_unit: ""
assumptions: []
source_refs: []
independent_support: none | partial | supported | conflicting
limitations: []
status: draft | needs_definition | evidence_requested | triangulated | needs_human_review
```

Rules:

- Do not combine a market-research firm's total industry revenue with a bottom-up capacity estimate unless the definitions and period are reconciled.
- Show the calculation path: customers × units × price, installed base × replacement rate, capacity × utilization × price, or another explicit method.
- State whether the estimate is addressable demand, theoretical opportunity, current spend, or the company's achievable revenue.
- TAM/SAM/SOM are labels, not evidence. Define each one in the project's context.
- Use ranges and sensitivity when inputs are uncertain.

## 5. Customer and commercialization record

Use a consistent funnel and preserve the source for each stage:

`lead → qualified opportunity → sample/pilot → technical/procurement approval → signed order/contract → shipment/delivery → recognized revenue → repeat purchase`

```yaml
customer_record:
  customer_id: "anonymized or named as permitted"
  segment: ""
  use_case: ""
  stage: lead | qualified | sample | pilot | approved | order | contract | shipped | revenue | repeat | lost | unknown
  stage_date: ""
  expected_value: null
  realized_revenue: null
  price_or_terms: ""
  next_step: ""
  evidence_type: management_statement | internal_data | contract_or_order | customer_interview | delivery_or_invoice | public_source
  evidence_ref: ""
  provenance: "who supplied or collected it"
  independent_check: pending | not_needed | requested | completed | conflicting
  notes: []
```

Do not collapse all active prospects into “customers”. Separate contracted revenue, delivered revenue, recognized revenue, repeat revenue, and pipeline. If customer identity is confidential, retain an anonymized ID plus the aggregation and verification route.

## 6. Customer interview and reference plan

The Agent may prepare and analyze an interview plan or supplied transcript. The human conducts the conversation and records provenance.

Each task should include:

```yaml
interview_task:
  task_id: INT-COM-001
  participant_type: customer | former_customer | prospect | supplier | channel | expert | competitor_proxy
  selection_reason: ""
  conflict_or_bias_risk: ""
  objective: ""
  primary_questions: []
  probes: []
  evidence_to_request: []
  interviewer: ""
  date: ""
  transcript_or_notes_ref: ""
  status: planned | scheduled | completed | notes_received | follow_up_needed | not_independent
  limitations: []
```

Questions should test behavior and evidence, not invite praise: actual use, alternatives considered, procurement steps, price/terms, performance, switching cost, renewal/repeat behavior, reasons for delay/loss, and what would cause the customer to stop buying.

## 7. Competitor and substitute comparison

```yaml
competitor_record:
  name_or_id: ""
  type: direct | substitute | incumbent | internal_build | status_quo
  target_segment: ""
  use_case: ""
  comparable_dimensions: []
  public_evidence: []
  customer_evidence: []
  claimed_advantage: ""
  evidence_for_advantage: []
  evidence_against_or_missing: []
  price_or_total_cost: ""
  switching_or_adoption_barrier: ""
  limitations: []
```

Compare the customer's alternative, not only the named venture competitors. An advantage is stronger when it changes customer selection or economics and is supported by repeatable evidence.

## 8. Commercial issue register

The common fields below are governed by `due-diligence-workspace-and-issue-ledger`. Keep the commercial fields as a domain extension; do not create a second ID or overwrite the common record.

```yaml
issue_id: COM-ISSUE-001
domain: commercial
issue_type: question | evidence_gap | finding | conflict | assumption | adjustment | decision_item
category: market_definition | demand | customer_validation | pricing | competition | sales_conversion | unit_economics | channel | supply_chain | scalability | execution | data_quality
title: "Short issue title"
question_or_observation: "What is unknown, observed, or conflicting"
priority: P0 | P1 | P2
observation: "What is supported by evidence"
source_refs: []
evidence_refs: []
evidence_types: []
confidence: low | medium | high | unknown
materiality: low | medium | high | unknown
possible_explanations: []
what_it_does_not_prove: ""
required_resolution: "What evidence or human review would close this issue"
next_evidence: []
owner: investor | company | customer | supplier | expert | adviser | unknown
status: not_started | evidence_requested | partially_supported | management_claim_only | under_review | conflicting | needs_professional_review | needs_human_validation | decision_ready | resolved | accepted_with_protection | deferred_with_reason
linked_issue_ids: []
downstream_consumers: [valuation | investment_terms | investment_decision | post_close_monitoring]
investor_impact:
  investability: go_no_go | wait_for_resolution | no_current_blocker | unknown
  valuation_effect: none_identified | possible_discount | possible_revaluation | input_needs_rework | unknown
  structure_effect: price | ownership | instrument | investment_amount | closing_sequence | consent | financing_milestone | unknown | none_identified
  closing_effect: condition_precedent_candidate | closing_deliverable_candidate | no_current_effect | unknown
  terms_effect: representation_warranty | indemnity | escrow_or_holdback | covenant | governance_right | information_right | founder_key_person_commitment | other | none_identified | unknown
  post_close_effect: monitor | remediation | reporting | milestone | none_identified | unknown
  rationale: ""
human_review_route: investor | commercial_adviser | accountant | lawyer | technical_expert | other
professional_review_status: not_requested | requested | in_progress | completed | not_applicable
change_log: []
```

P0 is appropriate when the issue could invalidate the demand thesis, customer reality, route to market, core competitive claim, ability to deliver, or transaction fit. Use P1 for matters needed before investment decision or valuation. Use P2 for monitoring or post-close improvement.

## 9. Structured output shape

```json
{
  "workspace_type": "commercial_due_diligence_analysis",
  "project_id": "",
  "as_of_date": "",
  "decision_questions": [],
  "business_model": {},
  "hypotheses": [],
  "market_estimates": [],
  "customers": [],
  "competitors": [],
  "interview_tasks": [],
  "issues": [],
  "open_requests": [],
  "human_validation_items": [],
  "reconciliations": [],
  "downstream_feeds": [],
  "human_review_items": [],
  "status": "not_started",
  "change_log": []
}
```

The JSON and Markdown must preserve the same definitions, source references, customer stages, hypothesis statuses, issue priorities, and limitations.
