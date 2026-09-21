---
name: due-diligence-intake-and-request-list
description: "Use when an equity investment project has passed or is preparing for an investment decision and the team needs to scope due diligence, open a data-room request list, or organize the first round of commercial, financial, legal, technical, tax, ESG, or other verification work."
---

# Due Diligence Intake & Request List

Turn the current project evidence into a tailored due-diligence starting package. This is a bridge between project initiation and formal diligence: it defines what must be collected, why it matters, how it can be verified, who should handle it, and what remains unresolved.

## 输出语言

默认所有面向用户的报告、分析、表格标题、字段显示名、问题、结论、建议、警示和解释均使用简体中文。用户明确要求其他语言时才切换。公司/人名、官方机构和产品名、文件名、URL、代码、公式、JSON/YAML键、稳定ID，以及必要的专业缩写（如 DCF、EBITDA、IRR、MOIC）可以保留原文；首次出现的专业缩写要附中文释义。机器可读字段或状态值可以保留英文，但旁边必须有中文说明；若 JSON 或表格也直接面向用户，必须同时提供对应的中文显示值或中文说明。原始材料引文可保留原语言，Agent 的分析和结论必须使用中文。

This is an Agent reasoning workflow, not a fixed checklist generator. The request list must be shaped by the project stage, industry, transaction structure, investment thesis, known gaps, and material risks.

**REQUIRED SHARED CONTRACT:** Use [due-diligence-workspace-and-issue-ledger](../due-diligence-workspace-and-issue-ledger/SKILL.md) as the persistent coordination layer. Every material inherited issue, evidence gap, contradiction, and decision-critical request must have or create a stable `issue_id`; request status is not a substitute for issue status.

## Boundary

This skill may scope work, organize requests, extract known facts, identify missing evidence, compare materials, and prepare questions. It must not:

- declare that commercial, financial, legal, technical, tax, or regulatory diligence has passed;
- provide a legal opinion, audit opinion, tax opinion, valuation approval, or investment-committee decision;
- treat a management statement, forecast, promise, or uploaded document as independently verified;
- make every standard request mandatory when the project facts do not justify it;
- silently close a contradiction or mark a request complete because a related document exists.

## Inputs

Read the latest available versions of:

- project card and original BP/company materials;
- current initiation research report and structured research workspace;
- meeting notes, answers, commitments, corrections, and prior question status;
- investment mandate, approved ticket, target ownership, geography, stage, and timing, if supplied;
- known transaction structure, proposed instrument, and existing data-room index, if supplied.
- the current shared due-diligence workspace and issue/impact ledger, if one exists.

If prior structured state is available, update it rather than rebuilding a new list from the last prose summary. If a required input is absent, record the absence and continue with an explicitly provisional scope.

## Operating model

1. **Establish the starting gate.** Determine whether the project is approved for formal diligence, conditionally preparing, or still awaiting an initiation condition. Do not assume approval merely because the user says “next stage”.
2. **Reconstruct the decision context.** Identify the investment thesis, transaction assumptions, project stage, business model, industry-specific risks, and every unresolved P0/P1 issue from earlier work.
3. **Choose the workstreams.** Start with commercial, financial, and legal. Add technical/operational, IP, tax, management/HR, ESG/EHS, data/cyber, integrity/background, or regulatory workstreams only when the project facts, transaction, jurisdiction, or open questions justify them. State why each selected workstream is in scope and why an obvious workstream is out of scope.
4. **Design a hypothesis-driven request list.** For each material question, request the smallest set of evidence that can answer it. Separate company-provided materials, public research, interviews, site visits, structured data entry, and specialist review. Do not copy a generic checklist without adapting it.
5. **Prioritize and route.** Use P0 for items that can invalidate the thesis, ownership/identity, legal ability to transact, core technical feasibility, customer reality, or transaction fit; P1 for items needed before an investment decision; P2 for matters that can be handled through conditions, representations, remediation, or post-close monitoring. Assign a route and a human owner where known.
6. **Define acceptance criteria.** A request is not complete because it was uploaded. State what must be present, what period/version/scope it must cover, what cross-check is required, and whether independent or professional verification is needed.
7. **Create the first-round plan.** Convert the highest-priority gaps into management questions, external verification tasks, site-visit tasks, specialist tasks, and a short sequence of work. Keep dependencies visible.
8. **Open or update the shared issue ledger.** For every material request, link the request to a stable issue record. Distinguish an unresolved question/evidence gap from a finding or risk. Record the potential effects on investability, valuation, structure, closing, investor-protection terms, and post-close monitoring as `unknown` when the evidence is not yet sufficient. Create cross-domain links when one request is needed to reconcile commercial, financial, or legal records.
9. **Prepare downstream feeds.** Summarize which request or issue IDs will later feed valuation, investment terms, and the investment committee. Include assumptions, uncertainty, and the human decision owner; do not convert a request into a recommendation.
10. **Self-audit.** Check that every P0/P1 issue from the initiation materials is mapped to a request or an explicit reason for deferral; that requests do not smuggle in unsupported facts; that evidence type, period, unit, entity scope, and confidentiality are clear; that issue IDs and statuses are stable; and that professional judgment is assigned to a human.

## Evidence and status rules

Keep these distinctions visible:

- `management_statement`: supplied by the company or management;
- `documented_claim`: stated in a supplied file but not independently verified;
- `public_source`: found in an external source;
- `independently_verified`: corroborated through an appropriate external, customer, site, accountant, lawyer, or specialist route;
- `agent_inference`: analysis that is not itself evidence;
- `forecast_or_commitment`: future-looking information;
- `conflict`: materially inconsistent values or descriptions.

Use request statuses such as `not_requested`, `requested`, `partially_received`, `received`, `under_review`, `needs_clarification`, `independent_check_pending`, `specialist_review_pending`, `resolved`, and `deferred_with_reason`. Do not use `verified` unless the acceptance criteria and verification route are actually satisfied.

For each request, explicitly state one or more Agent roles: `organize`, `extract`, `compare`, `calculate`, `reconcile`, `research`, `draft_questions`, or `no_independent_conclusion`. A professional or investor remains accountable for `legal_opinion`, `audit_assurance`, `tax_position`, `technical_acceptance`, `customer_reference`, `site_condition`, `fraud_judgment`, `valuation`, and `investment_decision`.

## Required output

Return the following sections in order. Read [references/due-diligence-intake-contract.md](references/due-diligence-intake-contract.md) for field definitions, routing vocabulary, and the initial request bank.

1. **尽调启动判断** — starting status, decision context, project stage, transaction assumptions, selected workstreams, excluded workstreams with reasons, and material caveats.
2. **尽调资料清单** — a tailored table or structured list. Every row must include an ID, workstream, request, purpose, priority, acceptable evidence, period/entity/scope, collection route, suggested owner, status, dependency, review/verification action, Agent role, and escalation condition.
3. **首轮尽调问题与核验计划** — management questions, public-research tasks, interview/customer/supplier tasks, site-visit tasks, specialist tasks, and the evidence each task is intended to produce.
4. **尽调工作流建议** — sequence, parallel work, dependencies, review gates, and the smallest useful next action.
5. **当前待解决事项与启动门槛** — unresolved P0/P1 items, what would resolve them, and whether formal diligence can start, start conditionally, or should wait.
6. **统一尽调问题与投资影响台账** — issue IDs, linked requests, evidence state, priority, owner, status, uncertainty, resolution condition, and downstream investment impacts.
7. **估值、投资条款与投决会输入** — only traceable inputs and open questions, each linked to issue IDs and a human owner.

If structured output is supported, also maintain the JSON workspace described in the reference. Markdown and JSON must describe the same list, statuses, priorities, and unresolved items.

## Quality bar

The result should be a working intake package, not a generic encyclopedia. Prefer fewer, decision-linked requests with clear acceptance criteria over a long list with no owner or purpose. Preserve the original evidence and source location for every inherited claim. When information is missing, say `材料未提供` or `无法确认` and create a request rather than filling the gap from model knowledge.
