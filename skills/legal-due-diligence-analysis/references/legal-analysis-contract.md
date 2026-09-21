# Legal Analysis Contract

Use this reference when legal diligence needs a structured issue register, document package, conditional workstream routing, or synchronized Markdown/JSON state.

## 1. Workspace metadata

```yaml
workspace_type: legal_due_diligence_analysis
workspace_version: "1.1"
project_id: ""
as_of_date: ""
jurisdictions: []
transaction_context: ""
entity_perimeter: []
project_stage: early | growth | mature | mixed | unknown
materiality_notes: []
selected_workstreams: []
excluded_workstreams: []
investment_decision_questions: []
shared_issue_ledger_ref: ""
```

At minimum, define the jurisdiction, entity perimeter, transaction context, and as-of date. A missing jurisdiction changes the meaning of many legal questions and must be flagged before a legal conclusion is attempted.

## 2. Investor impact record

Every material issue should be mapped separately across these dimensions:

```yaml
investor_impact:
  investability: go_no_go | wait_for_resolution | no_current_blocker | unknown
  valuation_effect: none_identified | possible_discount | possible_revaluation | input_needs_rework | unknown
  structure_effect: price | ownership | instrument | investment_amount | closing_sequence | consent | financing_milestone | unknown | none_identified
  closing_effect: condition_precedent_candidate | closing_deliverable_candidate | no_current_effect | unknown
  terms_effect: representation_warranty | indemnity | escrow_or_holdback | covenant | governance_right | information_right | founder_key_person_commitment | other | none_identified | unknown
  post_close_effect: monitor | remediation | reporting | milestone | none_identified | unknown
  human_decision_owner: investor | lawyer | tax_adviser | accountant | safety_specialist | company | unknown
  rationale: "Evidence-linked explanation; not a legal conclusion"
```

The Agent may propose candidate routes for discussion. The investor and transaction counsel determine whether a route is legally valid, commercially appropriate, and enforceable.

## 3. Evidence record

```yaml
evidence_id: LEG-E-001
category: corporate | ownership | governance | contract | ip | labor_work_injury | dispute | license_regulatory | ehs | tax | data_privacy | cybersecurity | financing_security | real_estate | integrity
claim_or_observation: ""
source_type: company_provided | management_representation | contract_or_record | official_public_source | counterparty_or_employee_evidence | counsel_input | agent_extraction | agent_inference | conflict
source_ref: "file / version / page / section / record ID / URL"
entity: ""
jurisdiction: ""
date_or_period: ""
status: supplied | extracted | corroborated | disputed | incomplete | not_applicable
limitations: []
linked_issue_ids: []
```

Never turn `agent_extraction` into a legal conclusion. A document can prove that a clause or allegation exists without proving enforceability, liability, loss, or probability of success.

## 4. Workstream selection guide

Use the following as routing prompts, not a mandatory universal checklist:

| Workstream | Include when | Typical supplied materials | Human review focus |
|---|---|---|---|
| Corporate / ownership | Any equity investment or governance right | registration, articles, cap table, historical issuances, shareholder/board records, beneficial ownership | title, control, authority, restrictions, approvals |
| Registration history / abnormalities | Registration fields changed, public records conflict, or transaction counterparties need identity verification | historical registration records, change notices, official extracts, abnormal-operation/penalty/freeze/pledge records, company explanations | significance, correction, disclosure, transaction impact |
| Governance / decision authority | Investor receives governance or consent rights, or history contains related-party or approval questions | board/shareholder minutes, resolutions, signing authority, related-party approvals, conflicts, policies | validity of approvals, authority, conflict management, investor rights |
| Contracts | Revenue, supply, channel, technology, or strategic relationships matter | material contracts, amendments, orders, templates, terms, claims | enforceability, breach, consents, change of control, remedies |
| IP | Technology, brand, data, content, or process is material | patent/trademark list, assignments, licenses, employment inventions, open-source, notices | chain of title, scope, validity, infringement, freedom to operate |
| Labor / key people / work injury | Employees, contractors, factories, labs, field work, or key-person risk exists | roster, full-time/consultant status, labor contracts, payroll/social insurance, dispatch/contractor agreements, safety training, accidents, injury claims, insurance, IP/non-compete terms | classification, liability, key-person continuity, remediation, local-law exposure |
| Disputes / enforcement | Any litigation, claim, demand, penalty, investigation, or adverse record appears | case list, pleadings, judgments, settlements, enforcement, correspondence, insurance | exposure, status, collectability, disclosure, transaction impact |
| Licenses / regulatory | Business requires permits, certifications, regulated activity, or government approvals | permits, certifications, inspection and penalty records, applications, correspondence | scope, validity, conditions, change-of-control, missing approvals |
| EHS | Manufacturing, chemicals, energy, construction, laboratories, or environmental exposure exists | environmental/safety permits, inspections, incidents, remediation, occupational-health files | ongoing exposure, liability, closure/remediation, insurance |
| Data / cyber | Personal data, software, critical systems, or customer security requirements matter | policies, data maps, contracts, incidents, assessments, vendor terms | compliance, breach exposure, controls, consent/transfer |
| Financing / security | Debt, guarantees, pledges, shareholder loans, or secured assets exist | loan/security documents, guarantee schedules, releases, bank letters | encumbrance, consent, covenant, priority, closing release |
| Tax | Tax treatment, incentives, cross-border or transaction tax affects value | filings, notices, incentives, related-party pricing, disputes | tax liability and specialist tax opinion |
| Real estate / assets | Facilities, land, equipment, leases, or construction are material | title/lease, permits, mortgages, construction and insurance records | title, use, encumbrance, compliance, transfer/consent |

## 5. Entity, ownership, and registration map

```yaml
entity_record:
  entity_id: ENT-001
  legal_name: ""
  entity_type: ""
  jurisdiction: ""
  registration_id: ""
  formation_date: ""
  current_status: ""
  shareholders_or_members: []
  beneficial_owners: []
  nominee_or_held_on_behalf_arrangements: []
  directors_officers: []
  historical_changes: []
  pledges_options_or_restrictions: []
  registration_abnormalities: []
  transaction_approval_status: ""
  source_refs: []
  conflicts: []
```

Use a separate record for historical values. Do not replace an earlier cap table with a later one without preserving the effective date and transaction that caused the change.

For each material change, preserve the event date, registered field, before/after value, filing or record source, explanation, consideration/payment evidence where relevant, and investor impact. A difference between the registered cap table and a private agreement is an issue to investigate, not an automatic finding of nominee holding.

```yaml
registration_change:
  change_id: REG-001
  effective_or_filing_date: ""
  field: registered_capital | shareholder | legal_representative | address | business_scope | director_supervisor | pledge_freeze | abnormal_status | other
  before_value: ""
  after_value: ""
  source_ref: ""
  company_explanation: ""
  supporting_documents: []
  anomaly_signal: none | unexplained | conflicting | needs_official_check
  investor_impact: {}
```

## 6. Contract record

```yaml
contract_record:
  contract_id: CTR-001
  parties: []
  counterparty_type: customer | supplier | partner | employee | lender | licensor | other
  effective_date: ""
  term_and_renewal: ""
  scope_and_value: ""
  status: signed | draft | expired | disputed | unknown
  key_clauses:
    change_of_control: ""
    assignment: ""
    termination: ""
    exclusivity: ""
    ip_and_confidentiality: ""
    indemnity_and_liability: ""
    governing_law_and_dispute_forum: ""
    compliance_and_audit: ""
  missing_versions_or_amendments: []
  source_refs: []
  counsel_review: not_requested | requested | completed
  investor_impact: {}
```

Extract what the contract says and where it says it. Keep the legal interpretation, negotiation position, and enforceability assessment in the human-review field.

## 7. IP record

```yaml
ip_record:
  ip_id: IP-001
  type: patent | trademark | copyright | trade_secret | software | domain | know_how | other
  identifier: ""
  title_or_description: ""
  applicant_or_registrant: ""
  current_owner: ""
  inventors_authors: []
  assignment_or_license_chain: []
  jurisdiction_and_status: ""
  expiry_or_renewal: ""
  encumbrance_or_security: ""
  business_relevance: ""
  infringement_or_freedom_to_operate_issue: ""
  source_refs: []
  professional_review: not_requested | requested | completed
  investor_impact: {}
```

Public registries can support status and filing history, but they do not by themselves establish complete ownership, employee invention rights, freedom to operate, validity, or absence of infringement.

## 8. Key-person, labor, work-injury, and safety record

```yaml
labor_safety_record:
  record_id: LAB-001
  period: ""
  population: employees | contractors | dispatched_workers | former_workers | unknown
  headcount_or_scope: ""
  person_or_group: ""
  full_time_or_consultant_status: full_time | part_time | consultant | contractor | dispatched | unknown
  topic: labor_contract | social_insurance | wage_hours | safety_training | occupational_hazard | accident | work_injury | compensation | labor_dispute | insurance | ip_assignment | non_compete | incentive_equity | key_person_dependence | other
  fact_or_claim: ""
  amount_or_exposure: ""
  status_or_procedure: ""
  evidence_refs: []
  management_explanation: ""
  missing_evidence: []
  human_review_route: lawyer | labor_specialist | safety_specialist | insurer | investor | unknown
  investor_impact: {}
```

Do not infer “no work injury” from no record. Ask for the defined period, all entities/sites, employees and contractors, reported and unreported incidents as represented, claims/settlements, insurance notifications, corrective actions, and unresolved authority matters.

## 9. Dispute and regulatory record

```yaml
dispute_record:
  dispute_id: DSP-001
  type: civil | commercial | labor | ip | administrative | environmental | safety | tax | criminal_related | other
  forum_or_authority: ""
  parties: []
  filing_or_notice_date: ""
  claim_or_issue: ""
  amount_or_exposure: ""
  procedural_status: ""
  judgment_order_settlement: ""
  enforcement_or_remediation: ""
  insurance_or_recovery: ""
  source_refs: []
  management_representation: ""
  counsel_review: not_requested | requested | completed
  investor_impact: {}
```

Record search scope and date. “No result found” should be stored as a search result with limits, not as an affirmative clean opinion.

## 10. Investor issue register

The common fields below are governed by `due-diligence-workspace-and-issue-ledger`. Legal-specific fields extend the common record. `candidate_protection_route` is a legal view of the shared `investor_impact.terms_effect`; it is a discussion candidate, not an approved term.

```yaml
issue_id: LEG-ISSUE-001
domain: legal
issue_type: question | evidence_gap | finding | conflict | assumption | adjustment | decision_item
category: ownership | governance | contract | ip | labor_work_injury | dispute | license_regulatory | ehs | tax | data_privacy | financing_security | real_estate | other
title: "Short issue title"
priority: P0 | P1 | P2
observation: "Evidence-linked statement"
question_or_observation: "What is unknown, observed, or conflicting"
source_refs: []
evidence_refs: []
evidence_types: []
source_date_or_period: ""
entity_or_scope: ""
confidence: low | medium | high | unknown
materiality: low | medium | high | unknown
possible_impact: "Transaction, value, liability, closing, or remediation impact"
uncertainty: "What is unknown or disputed"
required_resolution: "Evidence or professional conclusion needed"
owner: company | investor | lawyer | accountant | safety_specialist | tax_adviser | counterparty | agent | unknown
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
human_review_route: investor | lawyer | accountant | tax_adviser | safety_specialist | technical_expert | other
professional_review_status: not_requested | requested | in_progress | completed | not_applicable
closing_condition_candidate: true | false | unknown
candidate_protection_route: remediation_before_close | representation_warranty | indemnity | escrow_or_holdback | covenant | governance_right | information_right | founder_key_person_commitment | post_close_monitoring | none_identified | unknown
change_log: []
```

P0 means the issue could affect ownership, authority to transact, core asset rights, major liability, ability to operate, or transaction legality. P1 means it must be resolved before the investment decision or addressed through explicit terms/conditions. P2 can be monitored or remediated later only with a stated reason.

## 11. Structured output shape

```json
{
  "workspace_type": "legal_due_diligence_analysis",
  "project_id": "",
  "as_of_date": "",
  "scope": {},
  "entities": [],
  "registration_changes": [],
  "evidence": [],
  "contracts": [],
  "ip_records": [],
  "labor_safety_records": [],
  "disputes": [],
  "workstreams": [],
  "issues": [],
  "open_requests": [],
  "human_review_items": [],
  "reconciliations": [],
  "downstream_feeds": [],
  "investor_decision_impacts": [],
  "status": "not_started",
  "change_log": []
}
```

The Markdown and JSON must retain the same entity perimeter, evidence labels, issue priorities, document statuses, professional-review routes, and unresolved items.
