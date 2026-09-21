---
name: project-intake-and-project-card
description: "Use when receiving a BP or other project-introduction material in PDF, DOCX, Markdown, plain text, or mixed files and the user needs an initial investment-understanding package before speaking with the project team."
---

# Project Intake, Question List & Interview Guide

## Purpose

Turn supplied project materials into one coherent initial-review package: a source-grounded project card, a prioritized question list, and a semi-structured first-meeting interview guide. All three outputs must come from the same semantic understanding of the original materials. This is an Agent reasoning workflow, not a keyword parser or a deterministic data-extraction script.

## Boundary

This skill may interpret, organize, normalize, compare, and summarize information present in the supplied materials. It must not:

- use external research to fill gaps;
- decide whether the project is investable;
- create a valuation, financial forecast, or diligence conclusion;
- turn management claims, targets, or forecasts into verified facts;
- silently resolve contradictory figures or statements.

If the user also asks for external research, screening, diligence, valuation, or a recommendation, keep that as a separate later workflow.

## Workflow

1. **Inventory the materials.** Identify every provided file and whether it is readable. Read the full material when feasible, including headings, tables, captions, footnotes, and appendices. Use available document/PDF reading capability; do not invent a custom parser.
2. **Build one internal evidence map.** Understand the company, customers, business model, stage, transaction, claims, plans, forecasts, missing information, and contradictions before writing any output. Do not extract by matching a fixed list of words or taking the number nearest to a label.
3. **Classify and reconcile evidence.** Preserve meaning, period, unit, currency, scope, and source location. Mark important fields as explicit, derived, ambiguous, conflicting, or not_found. Distinguish management statements, historical results, plans, and forecasts. Retain competing values instead of silently choosing one.
4. **Determine the review lens.** Use [references/initial-review-framework.md](references/initial-review-framework.md) to identify the company stage and adjust attention to early-stage, growth-stage, or mature-company questions. If stage is uncertain, say so and use a mixed lens.
5. **Compose the three outputs from the same evidence map.** Follow [references/project-card-spec.md](references/project-card-spec.md) for the project card, question list, and interview guide contracts. Do not regenerate facts independently for each output.
6. **Self-audit.** Check for unsupported facts, silent assumptions, lost units or periods, merged stage types, unresolved contradictions presented as settled facts, and questions that have no reason or source. Report OCR, readability, and material limitations.

## Core reasoning rules

- Prefer semantic understanding over keyword matching and read context before interpreting numbers.
- Preserve qualifications such as “预计”, “目标”, “计划”, “约”, “超过”, and “累计”.
- Separate company development stage, financing stage, and investment-process stage.
- Treat BP content as source material or management-provided claims, not independent verification.
- If evidence is insufficient, write “材料未提及” or “无法确认” and state what is missing.
- Do not add external facts merely to make the card look complete.
- Generate a comprehensive question pool first, then select a smaller first-meeting shortlist.
- A question list records what must be learned; an interview guide records how to learn it in a real conversation.
- Use open-ended primary questions, then targeted probes for definitions, time periods, numbers, examples, and evidence. Avoid leading, accusatory, compound, or repetitive questions.
- If an answer resolves a later question, skip it. If an answer creates a contradiction or high-impact uncertainty, branch to the relevant probe.

## Output

Return, in this order:

1. **Project Card** — what the materials say about the company and project.
2. **Question List** — all material gaps, unclear claims, verification needs, and contradictions, prioritized as P0/P1/P2 with reason, source, target person, and desired evidence.
3. **Interview Guide** — meeting objective, assumed duration, participants, conversation sequence, primary questions, optional probes, evidence requests, and closing/next-step questions.

Then provide material-quality and unresolved-items notes. If the runtime supports structured output, also provide JSON using the field contract in the reference. Markdown and JSON must describe the same evidence state.
