# Financial Analysis Contract

Use this reference when the analysis requires a structured data model, a ratio calculation, a normalization ledger, or a synchronized Markdown/JSON workspace.

## 1. Dataset metadata

```yaml
workspace_type: financial_due_diligence_analysis
workspace_version: "1.1"
project_id: ""
as_of_date: ""
entity_scope: ""
consolidation_scope: standalone | consolidated | unknown
periods: []
frequency: monthly | quarterly | annual | mixed | unknown
currency: ""
unit_scale: yuan | thousand | million | other | unknown
accounting_basis: gaap | ifrs | tax_basis | management_basis | unknown
source_status: audited | reviewed | management_prepared | manually_entered | forecast | mixed | unknown
shared_issue_ledger_ref: ""
```

Never combine values with different currency, unit scale, entity scope, or accounting basis without an explicit conversion and a traceable note. If the period is not stated, mark the data as incomplete.

## 2. Metric record

For each material value or ratio, preserve:

```yaml
metric_id: FIN-REV-2025
metric: revenue | cogs | gross_profit | opex | ebitda | ebit | interest | tax | net_income | cfo | cfi | cff | cash | ar | inventory | ap | debt | capex | customer_revenue | product_revenue | other
period: "2025"
value: null
unit: ""
status: reported | management_prepared | forecast | derived | normalized | externally_supported | conflict | not_calculable
source_ref: "file / sheet / cell / page / pasted table row"
formula: ""
denominator_ref: ""
notes: []
```

For derived metrics, record the exact inputs and formula. For a conflicting metric, retain all competing values and their sources; do not select one silently.

## 3. Core formulas and caveats

Use only when the inputs have compatible periods and definitions:

| Metric | Formula | Caveat |
|---|---|---|
| Revenue growth | `(current revenue / prior revenue) - 1` | Explain if periods, consolidation, or currency changed |
| Gross profit | `revenue - cost of sales` | Do not derive if revenue or cost scope is incomplete |
| Gross margin | `gross profit / revenue` | Interpret by product mix and accounting classification |
| Operating margin | `operating profit / revenue` | State whether one-off items are included |
| EBITDA margin | `EBITDA / revenue` | Do not manufacture EBITDA from incomplete D&A or lease treatment |
| CFO margin | `operating cash flow / revenue` | Cash-flow classification must be known |
| CFO / net income | `operating cash flow / net income` | Do not overinterpret when net income is zero/negative or periods differ |
| DSO | `average accounts receivable / revenue × days` | End-period AR is only an approximation; use credit sales if available |
| DIO | `average inventory / cost of sales × days` | Use average inventory when available; seasonality matters |
| DPO | `average accounts payable / cost of sales × days` | AP scope must match the cost base |
| Cash conversion cycle | `DSO + DIO - DPO` | A diagnostic, not a universal good/bad cutoff |
| Current ratio | `current assets / current liabilities` | Classification and restricted cash matter |
| Net debt | `interest-bearing debt - unrestricted cash` | State treatment of leases, shareholder loans, and restricted cash |
| Net debt / EBITDA | `net debt / EBITDA` | Not meaningful with negative or unreliable EBITDA |
| Interest coverage | `EBIT or EBITDA / interest expense` | State chosen numerator and whether capitalized interest is included |
| Customer concentration | `top customer revenue / total revenue` | Define revenue period and whether customer groups are consolidated |
| Net burn | `cash outflows - cash inflows excluding financing` | Specify the chosen cash-flow definition |
| Runway | `available unrestricted cash / average monthly net burn` | Scenario only; do not use when burn is unstable without showing the range |

Show numerator and denominator for material ratios. Avoid excessive decimal precision; use the precision supported by the input data.

## 4. Data-quality checks

Run the applicable checks and record pass, fail, not_testable, or needs_explanation:

- balance sheet: `assets = liabilities + equity`;
- cash roll-forward: opening cash + CFO + CFI + CFF + FX/other = closing cash;
- income statement: revenue - cost of sales - operating expenses ± other items = stated profit, subject to the accounting basis;
- cash conversion: profit, CFO, AR, inventory, AP, and one-off items tell a coherent period story;
- detail-to-total: customer/product/segment tables reconcile to reported totals;
- revenue corroboration: contracts/orders, invoices, delivery, receivables, bank receipts, and tax data where available;
- debt: principal, interest, maturity, security, guarantees, and related-party balances reconcile across schedules;
- forecast bridge: historical base, capacity, volume, price, cost, working capital, capex, and financing assumptions are explicit;
- time and unit hygiene: no mixed months/years, currencies, tax-inclusive/exclusive amounts, or thousand/million scales;
- source traceability: every material input has file, sheet/cell/page, table row, or explicit user-provided reference.

A failed check is a request for explanation or evidence, not an automatic finding of misconduct.

## 5. Anomaly register

Every material anomaly must also be represented in the shared issue ledger. Use the common fields below and keep these financial fields as extensions.

Use one record per signal:

```yaml
anomaly_id: ANOM-001
issue_id: FIN-ISSUE-001
domain: financial
issue_type: question | evidence_gap | finding | conflict | assumption | adjustment | decision_item
category: trend | mix | concentration | working_capital | cash_conversion | one_off | related_party | debt_liquidity | forecast_variance | data_integrity
title: "Short issue title"
priority: P0 | P1 | P2
observation: "What the supplied data shows"
question_or_observation: "What remains unknown, observed, or conflicting"
comparison_base: "Prior period, plan, segment, or stated benchmark"
evidence_refs: []
evidence_types: []
source_date_or_period: ""
entity_or_scope: ""
confidence: low | medium | high | unknown
materiality: low | medium | high | unknown
possible_explanations: []
what_it_does_not_prove: ""
required_resolution: "What evidence or human review would close this issue"
next_evidence: []
owner: company | investor | accountant | auditor | tax_adviser | agent | unknown
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
human_review_route: investor | accountant | auditor | tax_adviser | lawyer | technical_expert | other
professional_review_status: not_requested | requested | in_progress | completed | not_applicable
change_log: []
```

Prioritize by materiality, persistence, reversibility, cash/valuation impact, and proximity to the investment thesis. Do not call a number “abnormal” solely because it crosses a memorized ratio threshold.

## 6. Quality-of-earnings adjustment ledger

Keep reported and adjusted views separate:

```yaml
adjustment_id: ADJ-001
period: ""
item: ""
reported_amount: null
adjustment_amount: null
direction: add_back | remove | reclassify | unknown
reason: ""
source_ref: ""
recurrence_assessment: recurring | non_recurring_claim | uncertain
cash_effect: cash | non_cash | mixed | unknown
confidence: high | medium | low
professional_review: not_requested | requested | completed
linked_issue_ids: []
```

An adjustment is not accepted merely because management calls it one-off. Require evidence, explain the economic substance, show the impact on EBITDA/cash/valuation if relevant, and flag professional review.

## 7. Output workspace shape

```json
{
  "workspace_type": "financial_due_diligence_analysis",
  "project_id": "",
  "dataset_metadata": {},
  "decision_questions": [],
  "metrics": [],
  "quality_checks": [],
  "anomalies": [],
  "adjustments": [],
  "scenarios": [],
  "open_requests": [],
  "human_review_items": [],
  "issues": [],
  "reconciliations": [],
  "downstream_feeds": [],
  "status": "data_incomplete",
  "change_log": []
}
```

`open_requests` should include missing field, reason, acceptable evidence, owner, priority, and status. `human_review_items` should explicitly route audit/accounting, tax, legal, technical, or investment judgments to a responsible human.
