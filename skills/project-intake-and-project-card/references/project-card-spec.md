# Initial Review Package Output Specification

Use this specification when composing the initial review package. It defines the output contract, not a fixed extraction algorithm. Fill a field only when the supplied material supports it. The project card, question list, and interview guide must be generated from one shared evidence map.

## Package order

Return the outputs in this order:

1. Project Card
2. Question List
3. Interview Guide
4. Material Quality and Unresolved Items

Do not let the project card hide gaps that are later needed for questions. Do not let the interview guide introduce new factual claims that are absent from the project card or source materials.

## Recommended structure

```markdown
# 项目卡：<项目/公司名称>

## 1. 基本信息
## 2. 项目与融资阶段
## 3. 产品与业务模式
## 4. 市场、客户与商业进展
## 5. 经营与财务数据
## 6. 融资、股权与交易信息
## 7. 团队信息
## 8. 材料明确呈现的项目亮点
## 9. 材料中的重要声明与待验证内容
## 10. 缺失信息与材料矛盾
## 11. 材料质量说明
## 12. 来源索引
```

Do not force every section to contain an answer. An empty or missing field is itself information and should be labeled rather than guessed.

## Field treatment

For every material field, preserve:

| Attribute | Meaning |
|---|---|
| `field` | The project-card field name |
| `value` | Human-readable value using the source’s wording where relevant |
| `normalized_value` | Optional normalized number/date/category, never a replacement for the original |
| `period` | Reporting or forecast period, if stated |
| `unit` | Currency, percentage, count, physical unit, or other measure |
| `status` | `explicit`, `derived`, `ambiguous`, `conflicting`, or `not_found` |
| `source_type` | For example `management_material`, `historical_report`, `forecast`, or `other_provided_material` |
| `source_ref` | File plus page, heading, paragraph, table, or other locator |
| `evidence_quote` | Short supporting excerpt for material claims and figures |
| `notes` | Qualification, derivation, conflict, or limitation |

The machine-readable representation may use this shape:

```json
{
  "field": "revenue",
  "value": "2025年营业收入约5000万元",
  "normalized_value": 50000000,
  "period": "2025",
  "unit": "CNY",
  "status": "explicit",
  "source_type": "management_material",
  "source_ref": "项目BP.pdf, p.12",
  "evidence_quote": "2025年实现营业收入约5000万元",
  "notes": "材料未说明是否为审计口径"
}
```

## Important distinctions

- “公司成立于 2021 年” is an explicit material statement; it is not independently verified.
- “预计 2026 年收入达到 1 亿元” is a forecast/target, not historical revenue.
- “市场规模超过 1000 亿元” is a management or source-material claim unless the supplied material identifies a separate authoritative source.
- “已与头部客户合作” does not necessarily mean paid revenue, recurring orders, or supplier qualification. Preserve the original wording and list the unanswered interpretations.
- If one page says 2024 revenue is 2,000 万元 and another says 3,000 万元, report both with both locations and mark the field `conflicting`.

## Initial-review framework

Use these dimensions as a flexible coverage map. Do not force every dimension to have an answer, and do not ask every possible question in the first meeting.

| Dimension | Core question | Early-stage emphasis | Growth-stage emphasis | Mature-company emphasis |
|---|---|---|---|---|
| Investment and transaction | What is being financed, why now, and what does the money unlock? | Milestones and next financing need | Expansion plan and capital efficiency | Transaction structure, control, debt, and exit |
| Company and ownership | Who owns and controls the company? | Founder commitment and basic cap table | Historical financing and dilution | Beneficial ownership, governance, succession |
| Product and technology | What is being built or sold, and why does it matter? | Problem, prototype, technical feasibility | Product-market fit, roadmap, scalability | Product portfolio, replacement risk, operational dependence |
| Market and competition | Is the market attractive and can this company win? | Market need, segment, substitutes | Growth drivers, share, competitive position | Cyclicality, defensibility, consolidation |
| Customers and commercial traction | Who pays, why do they buy, and will they keep buying? | Pilots, users, early references | Revenue quality, retention, repeat purchase, concentration | Contract durability, customer profitability, churn |
| Business model and economics | How does the company create and retain economic value? | Pricing logic and path to monetization | Gross margin, unit economics, sales efficiency | Normalized margin, cash conversion, operating leverage |
| Team and organization | Can this team deliver the next stage? | Founder-market fit and missing capabilities | Hiring, management depth, execution systems | Succession, incentives, key-person dependence |
| Financial and capital position | What has happened financially and what must happen next? | Burn, runway, milestones, financing dependency | Revenue, cash flow, working capital, forecast quality | Earnings quality, debt, capex, cash generation |
| Risk, compliance, and exit | What could invalidate the case or limit the outcome? | Critical technical, market, legal, or financing risks | Regulatory, customer, execution, and financing risks | Legal, tax, governance, environmental, and exit risks |

Stage is a lens, not a conclusion. If the material contains conflicting stage signals, report the conflict and use a mixed lens.

## Question List specification

The question list is the complete research backlog for the next conversation or follow-up. Group each item into one or more of:

- `not_mentioned`: the material does not address it;
- `unclear`: the material mentions it but lacks definition, period, scope, or detail;
- `verify_claim`: the material makes a claim that needs evidence;
- `conflict`: two supplied sources disagree;
- `decision_critical`: the answer could change whether the project proceeds or how it is valued/structured later.

Each important question should carry:

| Field | Meaning |
|---|---|
| `question_id` | Stable identifier such as `Q-001` |
| `question` | One clear question, not multiple questions joined together |
| `category` | Framework dimension |
| `reason_type` | One or more gap types above |
| `priority` | `P0` decision-critical for the first conversation, `P1` important follow-up, `P2` useful later |
| `why_it_matters` | Decision or hypothesis affected |
| `source_ref` | Material page/section that caused the question, or `not_found` |
| `target_person` | CEO, founder, CFO, CTO, sales lead, or other appropriate respondent |
| `desired_evidence` | Document, metric, example, demonstration, or explanation that would resolve it |
| `linked_claim_or_field` | Related project-card field, claim, or contradiction |

Always produce both:

1. an exhaustive question pool; and
2. a short first-meeting shortlist, normally the highest-impact P0 questions that fit the available time.

## Interview Guide specification

The interview guide is a semi-structured conversation plan, not a script that must be read word for word. Its purpose is to collect reliable information while allowing the project team to explain the business naturally.

Include:

- meeting objective and decision context;
- assumed duration and participants; if no duration is supplied, use a stated 45-minute default;
- opening and context-setting questions;
- a logical sequence of topic blocks;
- primary open-ended questions selected from the shortlist;
- optional probes for definitions, numbers, examples, time periods, changes, and evidence;
- questions that test high-impact claims without accusing the respondent;
- evidence or follow-up material to request after the call;
- closing questions about milestones, risks, financing use, and next steps.

Use a funnel shape: begin broad, narrow into specifics, then confirm implications and evidence. Prefer “请介绍一下……” or “能否具体说明……” over questions that suggest the desired answer. Avoid double-barreled questions, leading wording, and asking the respondent to confirm an investor’s conclusion.

For each guide item, preserve:

| Field | Meaning |
|---|---|
| `sequence` | Conversation order |
| `topic` | Topic block |
| `primary_question` | Main question to ask |
| `optional_probes` | Conditional follow-ups, not a second mandatory list |
| `purpose` | What uncertainty or hypothesis it tests |
| `linked_question_ids` | Items from the question list |
| `listen_for` | Specific facts, definitions, numbers, or inconsistencies to capture |
| `evidence_request` | Material to request if the answer requires verification |

The guide should not ask every question in the exhaustive pool. It should select a coherent path for the stated audience and time, while preserving optional branches for high-impact gaps or contradictions.

## Material-quality checks

Report, when applicable:

- files that could not be opened or were only partially read;
- scanned pages or OCR-derived text;
- tables whose headers, merged cells, or units were unclear;
- figures without a period, unit, or denominator;
- references to attachments or data rooms that were not supplied;
- contradictory company names, dates, stages, ownership, financing, or financial figures.

## Completion standard

A good project card is not the one with the most filled fields. It is the one where a reader can tell:

1. what the project says about itself;
2. what the supplied materials actually establish;
3. what was derived or interpreted;
4. what is unknown or contradictory; and
5. where each important statement came from.
