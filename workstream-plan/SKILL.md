---
name: workstream-plan
description: Create very long, highly detailed workstream plans from the user's text only. Use when the user wants a master plan, phased plan, big plan, strategy plan, workstream plan, or execution outline that is rich in scope, sequencing, dependencies, risks, rollout, and ownership, but not technical production-ready specs unless explicitly requested.
---

# Workstream Plan

## Goal

Write a very detailed workstream plan from the user's prompt alone.

Default output should be long-form planning depth. For substantial requests, expand the plan aggressively and aim for a document that is large enough to guide thinking across many workstreams, typically 1500+ lines when the request supports that level of detail.

## Source Of Truth

Use the user's text as the primary source of truth.

Do not inspect the repo, infer architecture from code, or introduce product-specific implementation details unless the user explicitly asks for that.

Do not turn this skill into a production-readiness spec by default.

## Output Contract

Always write the full plan to a Markdown file first, then reply in chat with:

- the plan file path
- a short summary
- any major assumptions

If the user gives a path, use it.

If the user does not give a path, prefer an existing planning folder if one is already obvious from context. Otherwise default to `docs/plans/YYYY-MM-DD-<slug>.md`.

Do not leave the full plan only in chat unless the user explicitly asks for chat-only output.

## What This Skill Should Produce

Produce plans that are:

- very detailed
- workstream-based
- rich in sequencing and dependencies
- rich in product reasoning
- rich in rollout thinking
- rich in user outcomes, failure cases, and open questions
- readable by humans without prior context

## What This Skill Should Avoid By Default

Do not include these unless the user explicitly asks:

- API contracts
- database schemas
- frontend/backend architecture
- provider integration details
- deployment plans
- production-readiness checklists
- file-level code tasks
- exact tests or command lists
- repo audits
- technical implementation contracts

This skill is for large strategic product plans with workstreams, not for technical production specs by default.

## Required Plan Shape

At minimum, cover:

1. Title
2. Objective
3. Product vision and outcome
4. User problem and target user
5. Success criteria
6. Scope
7. Non-goals
8. Assumptions
9. Core user flows
10. Workstream map
11. Workstreams in full detail
12. Dependencies and sequencing
13. Risks and mitigation
14. Rollout and adoption
15. Open questions and decision log

## Workstream Requirements

Every workstream should be expanded with:

- purpose
- target outcome
- why it matters
- core tasks
- sub-phases
- dependencies
- risks
- fallback paths
- blockers
- acceptance signals
- owner suggestion
- questions still unresolved

Expand each workstream until it feels operationally useful, not just summarized.

## Depth Rule

Do not compress for brevity.

If the prompt is broad, use that breadth to expand:

- multiple user segments
- multiple phases
- launch path
- failure modes
- adoption concerns
- decision points
- tradeoffs
- workstream sequencing
- communication needs
- operational assumptions

If the request is substantial, prefer a very large plan over a short neat one.

## Planning Style

Be concrete, structured, and exhaustive.

Stay product-facing by default.

Do not drift into technical production planning unless the user explicitly asks for it.
