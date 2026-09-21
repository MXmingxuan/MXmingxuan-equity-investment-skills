# Shared Due-Diligence Issue and Impact Contract

This is the shared contract for all diligence domains. Domain Skills may add specialized fields, but they must preserve these common fields and meanings.

## 1. Workspace metadata

```yaml
workspace_type: due_diligence_workspace
workspace_version: "1.0"
project_id: ""
as_of_date: ""
starting_gate: approved_for_formal_diligence | preparing_conditionally | awaiting_initiation_condition | unknown
project_stage: early | growth | mature | mixed | unknown
transaction_context: ""
selected_workstreams: []
decision_questions: []
evidence_coverage: ""
overall_status: not_started | collecting | analyzing | waiting_for_materials | needs_professional_review | ready_for_downstream_decision | paused
```

## 2. Issue lifecycle

Use the following conceptual sequence, while allowing a record to move back when new evidence creates a conflict:

`question → evidence_request → evidence_received → finding_or_conflict → decision_impact → human_review → resolved_or_deferred`

Do not skip from `question` to `resolved` merely because an answer was provided.

## 3. Shared issue record

```yaml
issue_id: DD-COM-001
domain: commercial | financial | legal | technical_operational | tax | ip | esg_ehs | management_hr | other
issue_type: question | evidence_gap | finding | conflict | assumption | adjustment | decision_item
category: "Domain-specific category"
title: "Short human-readable title"
question_or_observation: "What is unknown or what the evidence shows"
evidence_refs: []
evidence_types: []
source_date_or_period: ""
entity_or_scope: ""
priority: P0 | P1 | P2
status: not_started | evidence_requested | partially_supported | management_claim_only | under_review | conflicting | needs_professional_review | needs_human_validation | decision_ready | resolved | accepted_with_protection | deferred_with_reason
confidence: high | medium | low | unknown
materiality: high | medium | low | unknown
possible_explanations: []
what_it_does_not_prove: ""
required_resolution: "Evidence, calculation, interview, professional review, or decision needed"
owner: company | investor | agent | lawyer | accountant | auditor | tax_adviser | technical_expert | customer | supplier | other | unknown
next_action: "Smallest useful next step"
linked_issue_ids: []
downstream_consumers: valuation | investment_terms | investment_decision | post_close_monitoring | none | unknown
investor_impact:
  investability: go_no_go | wait_for_resolution | no_current_blocker | unknown
  valuation_effect: none_identified | possible_discount | possible_revaluation | input_needs_rework | unknown
  structure_effect: price | ownership | instrument | investment_amount | closing_sequence | consent | financing_milestone | unknown | none_identified
  closing_effect: condition_precedent_candidate | closing_deliverable_candidate | no_current_effect | unknown
  terms_effect: representation_warranty | indemnity | escrow_or_holdback | covenant | governance_right | information_right | founder_key_person_commitment | other | none_identified | unknown
  post_close_effect: monitor | remediation | reporting | milestone | none_identified | unknown
  rationale: "Evidence-linked explanation; not a professional conclusion"
human_review_route: investor | lawyer | accountant | auditor | tax_adviser | technical_expert | other | none
professional_review_status: not_requested | requested | in_progress | completed | not_applicable
created_at: ""
updated_at: ""
change_log: []
```

### Meaning of the important distinctions

- `question_or_observation` is not automatically a risk conclusion;
- `evidence_refs` must point to the original file, page, cell, interview record, URL, or supplied statement;
- `management_claim_only` means the claim is recorded but not independently supported;
- `decision_ready` means the evidence package is ready for a human investment decision, not that the decision is positive;
- `accepted_with_protection` means the investor has explicitly decided to handle the issue through a protection route; it is not a legal clearance;
- `resolved` requires the stated resolution condition to be satisfied and recorded.

## 4. Evidence record

```yaml
evidence_id: DD-E-001
source_type: original_material | company_provided | management_statement | structured_data | public_source | customer_interview | supplier_interview | expert_interview | site_visit | professional_input | agent_inference | forecast_or_commitment | conflict
source_ref: "File / page / sheet / cell / transcript / URL / record ID"
publisher_or_provider: ""
publication_or_event_date: ""
access_or_received_date: ""
entity_or_scope: ""
period: ""
claim_or_fact: ""
evidence_status: supplied | extracted | corroborated | disputed | incomplete | not_applicable
limitations: []
linked_issue_ids: []
```

One source may support several issues. Preserve competing evidence records instead of overwriting one with another.

## 5. Downstream decision feed

```yaml
feed_id: FEED-VAL-001
consumer: valuation | investment_terms | investment_decision | post_close_monitoring
input_type: commercial_assumption | financial_metric | financial_adjustment | legal_exposure | ownership_constraint | closing_condition | governance_need | milestone | risk_range | other
statement: "What the downstream Skill may use"
value_or_range: ""
assumptions: []
source_issue_ids: []
uncertainty: low | medium | high | unknown
status: draft | needs_human_review | approved_for_downstream_use | superseded
owner: investor | lawyer | accountant | technical_expert | other | unknown
change_log: []
```

Downstream feeds must not flatten uncertainty. A valuation input can be a range or scenario; a legal issue can be a potential liability rather than a booked amount; a commercial issue can be an unverified assumption rather than a forecast fact.

## 6. Cross-domain reconciliation

```yaml
reconciliation_id: RECON-001
topic: "Shared topic"
linked_issue_ids: []
observations: []
conflict_type: definition | amount | period | entity | ownership | status | source_quality | other
resolution_needed: ""
owner: investor | company | lawyer | accountant | technical_expert | other | unknown
status: open | explanation_requested | under_review | resolved | deferred_with_reason
downstream_effect: valuation | investment_terms | investment_decision | none | unknown
```

Examples include: commercial customer/order claims versus financial revenue; legal IP ownership versus technical moat; legal debt/claims versus financial liabilities; or key-person employment/IP status versus operational dependency.

## 7. Priority rules

- **P0:** could invalidate the investment thesis, true ownership/control, ability to transact or operate, core asset rights, financial integrity, customer reality, or transaction fit.
- **P1:** must be resolved before valuation, investment decision, or final terms, or must become an explicit closing/protection condition.
- **P2:** can reasonably be monitored, remediated, or handled post-close without changing the core decision, with an owner and deadline.

Priority is not a conclusion about severity under law or accounting; it is an investment-workflow priority.

## 8. Structured workspace shape

```json
{
  "workspace_type": "due_diligence_workspace",
  "workspace_version": "1.0",
  "project_id": "",
  "as_of_date": "",
  "starting_gate": "",
  "selected_workstreams": [],
  "decision_questions": [],
  "evidence": [],
  "issues": [],
  "reconciliations": [],
  "downstream_feeds": [],
  "open_requests": [],
  "human_review_items": [],
  "change_log": []
}
```
