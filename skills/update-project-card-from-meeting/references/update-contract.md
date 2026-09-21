# Update Contract

This contract defines how post-meeting updates are represented. It is a reasoning and evidence contract, not a code schema that determines what the model should extract.

## Output structure

```markdown
# 更新后的项目卡：<项目名称>

## 0. 更新元数据
## 1. 项目当前状态
## 2. 本次更新后的事实与声明
## 3. 当前关键数据
## 4. 当前投资假设与影响
## 5. 问题状态更新
## 6. 本次变更摘要
## 7. 新增问题与未闭环事项
## 8. 来源与证据索引
```

The title must use the exact phrase **更新后的项目卡**. Do not call the primary output “会议纪要” or “项目摘要”.

## Evidence record

For each changed material field, preserve:

| Field | Meaning |
|---|---|
| `field` | Project-card field being updated |
| `previous_value` | Value in the prior card, or `not_found` |
| `new_value` | What the new material states |
| `status` | `explicit`, `derived`, `ambiguous`, `conflicting`, or `not_found` |
| `source_type` | `meeting_statement`, `new_document`, `historical_data`, `forecast_or_plan`, `commitment`, or `investor_interpretation` |
| `source_ref` | Meeting date/speaker/file/page/section |
| `evidence_quote` | Short supporting excerpt |
| `update_effect` | `new`, `confirmed_against_prior`, `changed`, `explained_pending_verification`, or `still_open` |
| `notes` | Qualification, limitation, or downstream impact |

Example:

```json
{
  "field": "revenue_2025",
  "previous_value": "材料未提及",
  "new_value": "2025年收入约8000万元，其中核心产品收入约5600万元",
  "status": "explicit",
  "source_type": "meeting_statement",
  "source_ref": "2026-09-21管理层会议，CFO",
  "evidence_quote": "总收入约8000万，核心产品约5600万，其余为贸易及代销收入",
  "update_effect": "new",
  "notes": "仍需财务明细或审计材料验证"
}
```

## Question status model

Use stable question IDs from the prior question list.

| Status | Meaning |
|---|---|
| `answered_verified` | Answered and supported by an independent or supplied document/record |
| `answered_unverified` | Management or other party answered, but evidence is not yet sufficient |
| `partially_answered` | Some sub-points answered; material parts remain open |
| `unchanged_open` | No new information addressed it |
| `contradicted` | New material conflicts with prior material or answer |
| `superseded` | The old question is no longer the right question; explain why and create a replacement if needed |

Do not use `answered_verified` merely because the answer was specific or confident.

## Commitments

Track commitments separately:

| Field | Meaning |
|---|---|
| `commitment_id` | Stable ID such as `C-001` |
| `owner` | Person or company responsible |
| `promised_item` | Document, data, action, or introduction promised |
| `promised_date` | Date if stated; otherwise `not_stated` |
| `status` | `promised`, `received`, `partially_received`, `overdue`, or `cancelled` |
| `investment_impact` | What decision or question it affects |

A promised document remains `promised` until it is actually supplied and reviewed.

## New issue rules

Create a new question or issue when:

- an answer introduces a fact not covered by the prior question list;
- a new number changes a forecast, valuation input, stage, or risk;
- a speaker introduces a related-party, ownership, legal, technical, or compliance concern;
- a commitment has a deadline or is necessary to close a P0/P1 question;
- a contradiction cannot be explained from the current materials.

## Completion standard

A good update lets a reader answer five questions:

1. What did we know before?
2. What new information arrived?
3. What is now better understood?
4. What is still only a claim or promise?
5. Which questions and risks remain open?
