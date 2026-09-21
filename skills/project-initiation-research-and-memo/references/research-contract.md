# Initiation Research Contract

This is a reasoning contract for an iterative investment-initiation workspace. It is not a rigid parser schema. The agent should adapt the questions and evidence standard to the project, stage, sector, geography, and available materials.

## 1. Research state

The structured workspace should contain:

```json
{
  "project": {},
  "workspace_meta": {
    "revision": 1,
    "as_of_date": "YYYY-MM-DD",
    "status": "researching",
    "mandate_constraints": []
  },
  "decision_questions": [],
  "evidence_ledger": [],
  "evidence_requests": [],
  "findings": [],
  "recommendation": {},
  "change_log": []
}
```

Each material statement in `findings` should link to one or more `decision_questions` and `evidence_ledger` records.

## 2. Decision questions

Create only questions that can affect whether the project should proceed. Typical dimensions are:

- company identity, history, ownership, governance, and public records;
- investment fit, financing need, transaction form, and use of funds;
- product, technology route, maturity, IP, and independent validation;
- customers, orders, revenue quality, channels, delivery, and retention;
- industry, market, regulation, competition, and defensibility;
- team, key-person dependence, hiring, and execution ability;
- financial quality, cash runway, capital needs, and financing history;
- risks, compliance, environmental/safety exposure, and exit plausibility.

Adapt emphasis by stage:

| Stage | Higher-weight questions |
|---|---|
| Early | team, real problem, technical feasibility, pilots, milestones, next financing |
| Growth | repeatable revenue, customer quality, gross margin, unit economics, capacity, cash |
| Mature | normalized earnings, cash flow, debt, governance, compliance, valuation, exit |

Each question should have `id`, `question`, `why_it_matters`, `priority`, `expected_evidence`, `route`, `status`, and `decision_impact`. Use `route` values `search`, `request`, `both`, or `open`.

## 3. Evidence ledger

For each material record preserve:

| Field | Meaning |
|---|---|
| `evidence_id` | Stable ID such as `E-001` |
| `claim` | What the evidence supports or challenges |
| `source_type` | `original_material`, `user_provided`, `management_statement`, `official_public_source`, `professional_source`, `media_or_aggregator`, `agent_inference`, or `commitment` |
| `source_ref` | File/page, meeting/speaker, URL, or other traceable reference |
| `published_at` / `accessed_at` | Dates when available |
| `authority_tier` | `A_primary`, `B_professional`, `C_lead_or_claim`, or `internal_unverified` |
| `evidence_status` | `explicit`, `supported`, `derived`, `ambiguous`, `conflicting`, `not_found`, or `superseded` |
| `quote_or_excerpt` | Short supporting passage or exact data reference |
| `linked_questions` | Decision-question IDs |
| `limitations` | Scope, period, definition, missing context, or conflict |

An answer from management can be explicit without being independently verified. A user-provided file can be highly relevant without being an official external source. Keep those dimensions separate.

## 4. Evidence-request queue

Every request should include:

| Field | Meaning |
|---|---|
| `request_id` | Stable ID such as `R-001` |
| `request` | Missing data or document needed |
| `reason` | Decision question and consequence |
| `priority` | `P0`, `P1`, or `P2` |
| `route` | `search`, `user_or_project_team`, `both`, or `manual_decision` |
| `acceptable_evidence` | Minimum useful material |
| `owner` | Agent, user, project team, or not assigned |
| `status` | `open`, `requested`, `partially_received`, `received_unreviewed`, `verified`, `conflicting`, `not_obtainable`, or `closed` |
| `received_refs` | Evidence IDs or file references |
| `next_action` | Smallest useful follow-up |

Generate requests for decision-critical gaps, not every missing detail. A request should tell the user what to provide and why it matters. When a public search is unlikely to reveal private information, say so directly.

## 5. Search protocol

For each search task:

1. state the decision question and the claim to test;
2. identify aliases, legal entity names, product names, geography, and time window;
3. search primary sources first, then use professional sources for context and triangulation;
4. inspect the source itself rather than relying on the search snippet;
5. capture the exact claim, date, scope, and source tier;
6. run a contradiction or independent-corroboration search for P0 claims;
7. stop when the question is sufficiently supported, when a source boundary is reached, or when the remaining gap is private and should become a request.

Do not search for the sake of filling every blank. Do not infer current company information from stale pages. Use an explicit as-of date.

## 6. Finding status and decision gates

Use finding statuses:

- `confirmed`: supported by appropriate evidence;
- `supported_not_fully_verified`: credible but material verification remains;
- `management_claim`: supplied by the project team without independent support;
- `derived`: an inference, with linked evidence;
- `conflicting`: materially inconsistent evidence;
- `open`: insufficient evidence;
- `not_applicable`: explain why.

Universal P0 gates include:

- company identity, ownership, and transaction fit are not fundamentally unclear;
- the core business and customer/problem claim are coherent;
- no known fatal legal, regulatory, technical, or integrity issue is ignored;
- the core investment thesis has evidence that can be tested;
- the next stage and financing need are understandable.

The report may recommend formal due diligence only when the remaining uncertainty is stated and the recommendation is not blocked by an unresolved P0 gate. A missing P1/P2 item can support a conditional recommendation if the condition is specific.

## 7. Output contract

The Markdown output must use this order:

```markdown
# 当前立项研究报告：<项目名称>

## 0. 研究状态与口径
## 1. 结论摘要
## 2. 项目与投资机会概况
## 3. 行业、市场与竞争
## 4. 产品、技术与知识产权
## 5. 商业化、客户与经营质量
## 6. 公司、团队与治理
## 7. 财务、融资、估值与交易结构
## 8. 投资逻辑、关键假设与风险
## 9. 立项建议与条件
## 10. 当前资料需求清单
## 11. 本轮研究与更新摘要
## 12. 证据与来源索引
```

The report should show `事实`, `分析`, and `建议` separately where confusion is likely. If no reliable valuation range can be formed, state the missing inputs and do not manufacture a number.

The user-facing package should also include:

```markdown
# 当前资料需求清单：<项目名称>
...
# 本轮研究与更新摘要：<项目名称>
...
```

If the project already has an established output convention, preserve it while keeping the exact primary heading **当前立项研究报告**.

## 8. Incremental update rules

- Increment `workspace_meta.revision` on each material update.
- Preserve prior values, evidence, and conclusions in the change log.
- For changed data, store before/after values, source references, and downstream impact.
- Never close a request merely because the user mentioned the answer; attach the supplied evidence and assess its status.
- Never delete a conflict because one source is newer; explain why the newer source is preferred, if it is.
- The current report, request queue, and JSON workspace must agree.

