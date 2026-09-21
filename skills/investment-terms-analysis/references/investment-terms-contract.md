# Investment Terms Contract

## 1. Transaction frame

```yaml
workspace_type: investment_terms_analysis
workspace_version: "1.0"
project_id: ""
as_of_date: ""
jurisdiction: ""
instrument: equity | preferred_equity | convertible | other | unknown
investment_amount: ""
primary_proceeds: ""
secondary_proceeds: ""
entry_valuation_basis: pre_money | post_money | price_per_share | unknown
entry_valuation: ""
target_ownership: ""
fully_diluted_basis: ""
valuation_workspace_ref: ""
shared_workspace_ref: ""
status: draft | under_review | counsel_review | ready_for_approval | superseded
```

## 2. Term record

```yaml
term_id: TERM-001
category: economics | instrument | capitalization | liquidation_exit | governance | information | founder_key_person | transfer_exit | follow_on | conditions_precedent | representations_warranties | indemnity | escrow_holdback | covenant | default_dispute | tax_accounting
title: "Short term title"
position: "Candidate term or open question"
purpose: "Risk or decision this addresses"
linked_issue_ids: []
linked_feed_ids: []
trigger_or_condition: ""
beneficiary: investor | company | founders | all_shareholders | unknown
economic_effect: ""
legal_or_accounting_dependency: ""
priority: must_resolve_before_term | required_protection | negotiation_preference | fallback | not_applicable
status: open | proposed | management_counter | investor_approved | counsel_review_pending | agreed_in_principle | documented | rejected | deferred
owner: investor | company | lawyer | accountant | tax_adviser | agent | unknown
fallback: ""
walk_away_condition: ""
limitations: []
change_log: []
```

## 3. Risk-to-term mapping

```yaml
risk_term_map_id: RTM-001
issue_id: DD-001
observation: ""
uncertainty: ""
investment_impact: ""
response_type: resolve_before_close | condition_precedent | term_protection | post_close_monitoring | no_term_substitute | decision_item
candidate_term_ids: []
alternative_action: ""
human_decision_owner: investor | lawyer | accountant | technical_expert | investment_committee | unknown
status: open | under_review | resolved | deferred
```

## 4. Economic scenario record

```yaml
term_scenario_id: TERMSC-001
scenario_name: ""
entry_valuation: ""
investment_amount: ""
primary_or_secondary: ""
option_pool_treatment: ""
instrument_terms: []
investor_ownership: ""
exit_equity_value: ""
investor_proceeds: ""
moic: ""
irr_or_xirr: ""
assumption_refs: []
```

## 5. Approval feed

```yaml
approval_feed_id: FEED-TERM-001
consumer: investment_committee | investment_decision
statement: ""
source_term_ids: []
source_issue_ids: []
source_feed_ids: []
decision_required: ""
uncertainty: low | medium | high | unknown
owner: investor | lawyer | accountant | investment_committee | unknown
status: draft | needs_human_review | ready_for_approval | superseded
```
