# Investment Committee Contract

## 1. Decision snapshot

```yaml
workspace_type: investment_committee_decision
workspace_version: "1.0"
project_id: ""
as_of_date: ""
data_room_version: ""
model_version: ""
terms_version: ""
requested_route: approve | approve_with_conditions | defer | reject | unknown
requested_instrument: ""
requested_amount: ""
valuation_range: ""
target_ownership: ""
critical_missing_inputs: []
```

## 2. Decision issue

```yaml
decision_issue_id: IC-ISSUE-001
question: "What must the committee decide?"
context: ""
options: []
recommended_option: ""
source_issue_ids: []
source_feed_ids: []
materiality: P0 | P1 | P2
uncertainty: low | medium | high | unknown
decision_owner: investment_committee | investor | lawyer | accountant | technical_expert | unknown
status: open | ready_for_decision | decided | deferred
decision_or_rationale: ""
```

## 3. Recommendation and condition

```yaml
recommendation:
  route: approve | approve_with_conditions | defer | reject | unknown
  rationale: ""
  thesis_support: []
  thesis_breakers: []
  key_uncertainties: []
  dissent_points: []

conditions:
  condition_id: IC-COND-001
  description: ""
  type: evidence | remediation | counsel_approval | valuation_update | term_agreement | closing_deliverable | post_close_covenant | monitoring
  linked_issue_ids: []
  evidence_standard: ""
  owner: company | investor | lawyer | accountant | adviser | unknown
  due_date: ""
  status: open | received | under_review | satisfied | waived | escalated
  escalation: ""
```

## 4. Decision record

```yaml
decision_record:
  meeting_date: ""
  attendees: []
  decision: approved | approved_with_conditions | deferred | rejected | not_decided
  approved_amount: ""
  approved_instrument: ""
  approved_valuation_or_price: ""
  approved_terms_version: ""
  deviations_from_proposal: []
  conditions: []
  follow_up_owner: ""
  next_review_date: ""
  change_log: []
```
