# Financial Forecast and Valuation Contract

## 1. Workspace metadata

```yaml
workspace_type: financial_forecast_and_valuation
workspace_version: "1.0"
project_id: ""
as_of_date: ""
valuation_date: ""
entity_scope: ""
forecast_start: ""
forecast_end: ""
currency: ""
unit_scale: yuan | thousand | million | other | unknown
project_stage: pre_revenue | early_revenue | growth | mature | mixed | unknown
business_model: manufacturing | saas | marketplace | project | biotech | consumer | other | unknown
selected_scenarios: [base, downside, upside]
selected_valuation_methods: []
shared_workspace_ref: ""
status: data_incomplete | illustrative | under_review | ready_for_human_review | superseded
```

## 2. Evidence-to-assumption record

```yaml
assumption_id: ASSUMP-001
name: "Forecast driver"
category: revenue | price | volume | utilization | conversion | retention | margin | headcount | opex | capex | working_capital | tax | debt | exit | valuation
value_or_range: ""
unit: ""
period: ""
scenario: base | downside | upside | actual | management_case | user_override
source_refs: []
evidence_type: actual | company_provided | management_statement | diligence_finding | downstream_feed | public_source | agent_scenario | user_input
linked_issue_ids: []
confidence: high | medium | low | unknown
what_would_change_it: ""
owner: company | investor | agent | accountant | adviser | unknown
status: active | pending | superseded | unavailable
change_log: []
```

## 3. Forecast record

```yaml
forecast_record:
  period: "2027"
  scenario: base
  revenue: null
  cogs: null
  gross_profit: null
  opex: null
  ebitda: null
  da: null
  ebit: null
  tax: null
  cfo: null
  capex: null
  cfi: null
  cff: null
  ending_cash: null
  debt: null
  working_capital: null
  funding_need: null
  source_or_formula_refs: []
  availability: calculated | partial | unavailable
```

Use the user's accounting basis and entity scope. Keep revenue, collections, profit, cash flow, capex, depreciation, debt principal, and equity proceeds distinct.

## 4. Valuation record

```yaml
valuation_record:
  method_id: VAL-001
  method: dcf | revenue_multiple | ebitda_multiple | transaction_comparable | venture_method | scorecard | cost_to_duplicate | lbo_returns | other
  valuation_date: ""
  enterprise_value_range: ""
  equity_value_range: ""
  operating_metric: ""
  metric_period: ""
  multiple_or_discount_rate: ""
  terminal_method: perpetuity_growth | exit_multiple | none | not_applicable
  net_debt_or_cash: ""
  dilution_basis: pre_money | post_money | fully_diluted | unknown
  source_refs: []
  linked_issue_ids: []
  applicability: appropriate | illustrative | not_suitable | unavailable
  limitations: []
  human_owner: investor | valuation_adviser | accountant | other | unknown
```

## 5. Investor entry and exit record

```yaml
returns_record:
  scenario_id: RET-001
  entry_date: ""
  exit_date: ""
  entry_investment: ""
  primary_proceeds: ""
  secondary_proceeds: ""
  entry_pre_money: ""
  entry_post_money: ""
  investor_ownership_at_entry: ""
  dilution_events: []
  exit_enterprise_value: ""
  exit_net_debt_or_cash: ""
  exit_equity_value: ""
  investor_ownership_at_exit: ""
  investor_proceeds: ""
  cash_flows: []
  moic: ""
  irr_or_xirr: ""
  assumptions: []
  limitations: []
```

IRR requires at least one negative investment cash flow and a valid exit/distribution cash flow with dates. If timing is not known, calculate MOIC and mark IRR unavailable or use a clearly labeled illustrative date.

## 6. Downstream feed

```yaml
feed_id: FEED-VAL-001
consumer: investment_terms | investment_decision | post_close_monitoring
input_type: revenue_range | margin_range | funding_need | valuation_range | ownership | dilution | exit_value | return_sensitivity | condition | other
statement: ""
value_or_range: ""
source_assumption_ids: []
source_issue_ids: []
uncertainty: low | medium | high | unknown
status: draft | needs_human_review | approved_for_downstream_use | superseded
owner: investor | lawyer | accountant | adviser | unknown
change_log: []
```

## 7. Minimum checks

- actual periods and forecast periods are clearly separated;
- scenario selector drives the active forecast assumptions;
- balance sheet and cash roll-forward tie or show an explicit unavailable check;
- no negative cash is hidden as zero;
- valuation date, net debt/cash, share basis, and dilution basis are consistent;
- primary and secondary proceeds are separated;
- exit proceeds reconcile to exit equity value × investor ownership, subject to specified preferences/fees;
- MOIC and IRR/XIRR are independently recalculated from the cash-flow series;
- every material assumption and downstream feed has a source, issue ID, or explicit illustrative label.
