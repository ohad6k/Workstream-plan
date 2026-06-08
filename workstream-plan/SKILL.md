---
name: workstream-plan
description: Create exhaustive, implementation-ready workstream plans from product ideas, specs, architecture notes, or roadmap discussions. Use when the user asks for a master plan, build plan, agent-ready plan, subagent workstreams, phased implementation, execution plan, or wants to dispatch coding agents without them guessing architecture, files, tests, ownership, rollout, or risk controls.
---

# Workstream Plan

## Goal

Turn a product idea or rough spec into a build plan that implementation agents can execute without inventing missing architecture. Optimize for clarity, ownership, sequencing, testability, and protection of existing product behavior.

Do not optimize for shortness. For a complex product build, a plan can be thousands of lines. The quality bar is: if an implementation agent could still silently choose a different architecture, miss a constraint, or change protected behavior, the plan is not detailed enough.

## Core Rule

Write the plan as an execution contract, not as strategy prose.

Every major requirement must answer:

- What exactly will be built?
- Where exactly will it live?
- What existing code must be reused?
- What must not be changed?
- Which workstream owns it?
- Which tests prove it?
- Which risks remain?
- What should agents do if repo reality differs from the plan?

## Workflow

1. **Restate the objective**
   - Name the product outcome in one sentence.
   - Identify the current product surface being extended.
   - Separate user-facing promise from implementation mechanism.

2. **Audit before planning when a repo exists**
   - Inspect package structure, runtimes, routes, services, shared types, migrations, tests, commands, and auth/billing boundaries.
   - Verify that named files/functions actually exist before referencing them.
   - Mark unverified assumptions explicitly.
   - Prefer existing architecture over new systems.

3. **Define V1 scope and non-goals**
   - Specify supported app types, providers, frameworks, environments, and workflows.
   - Specify unsupported or future items.
   - Specify what will be shown as manual, guided, coming soon, or blocked.

4. **Define product contract**
   - State the user promise.
   - Define what the product will never leave vague.
   - Convert every manual step into a guided action with exact destination, exact value, exact expected state, and verification behavior.

5. **Define architecture**
   - Identify production runtime, local/dev runtime, frontend surfaces, backend APIs, database tables, CLI/runner/extension responsibilities, and external providers.
   - Avoid duplicated API work unless production truly needs it.
   - Keep existing billing, plan limits, scan behavior, CLI behavior, and extension behavior unchanged unless explicitly assigned.

6. **Define shared data contracts**
   - Include database schema, API request/response shapes, state machines, action models, proof models, event names, and redaction rules.
   - Use names that do not collide with existing billing/subscription/provider concepts.

7. **Break into workstreams**
   - Keep each workstream small enough for one implementation agent.
   - Assign clear ownership of files/modules.
   - Make workstreams additive when possible.
   - Use feature flags, additive routes, or isolated components for risky surfaces.
   - List dependencies between workstreams.

8. **Write dispatch instructions**
   - Every agent must preflight current repo state before editing.
   - Every agent must report mismatches before coding.
   - Every agent must not silently invent alternate architecture.
   - Every agent must protect existing behavior outside its assignment.

9. **Define verification**
   - Include unit, integration, E2E, build, typecheck, smoke, and regression commands.
   - Define acceptance criteria per module and per workstream.
   - Include at least one full happy path and key unhappy paths.

10. **Define rollout**
    - Include feature flag behavior, migration order, fallback, observability, release sequencing, and rollback notes.
    - Include final review gates and merge/PR expectations.

## Required Output Shape

For substantial plans, use this order:

1. Title and objective
2. Product promise
3. V1 scope and non-goals
4. Verified current architecture
5. Architecture decision
6. UX or flow spec
7. Data models and state models
8. Security/privacy rules
9. Workstream dependency map
10. Workstreams, one by one
11. Agent execution rules
12. Regression protection rules
13. Acceptance criteria
14. Test plan
15. Rollout plan
16. Risks and open questions

For a full template, read `references/plan-template.md`.

## Workstream Requirements

Each workstream must include:

- **Objective**: the exact outcome.
- **Preflight**: files/functions/types/routes the agent must confirm before editing.
- **Owned files**: the expected write scope.
- **Read-first files**: files to inspect but not necessarily edit.
- **Protected behavior**: existing behavior the agent must not change.
- **Implementation steps**: ordered, concrete steps.
- **Data/contracts**: exact types, fields, states, or API shapes.
- **Tests**: exact test files to add/update and commands to run.
- **Acceptance criteria**: observable done conditions.
- **Dependencies**: previous workstreams required first.
- **Risks/gaps**: known limitations or follow-up work.
- **Report format**: files changed, tests run, behavior protected, risks, next dependency.

## Agent Guardrail Block

Include this block, adapted to the repo:

```markdown
Before editing, each implementation agent must:
- confirm the files/modules from this plan exist
- confirm current exports/functions/types match the plan
- identify mismatches before coding
- avoid silently inventing alternate architecture
- keep changes scoped to the assigned workstream
- avoid changing existing billing, plan limits, scan behavior, CLI commands, extension behavior, or auth/session behavior unless explicitly assigned
- use additive routes/components/flags for risky surfaces
- run the regression commands for its layer
- report files changed, tests run, existing behavior protected, risks/known gaps, and next dependency
```

## Quality Bar

A good workstream plan lets independent agents implement without follow-up clarification.

Reject or revise a plan when:

- It says "handle auth", "add database", "connect provider", or "make UI" without exact contracts.
- It references files/functions that were not verified.
- It mixes multiple risky surfaces in one workstream.
- It has no protected-behavior list.
- It has no state model.
- It has no exact tests or acceptance criteria.
- It creates a separate product when the user asked to extend the current one.
- It stores secrets, logs, or user data without explicit privacy rules.
- It changes billing or quotas without explicit assignment.

## Communication Style

Be direct and implementation-specific. Avoid hype inside the plan. If the user wants marketing copy for the plan process, keep that separate from the build spec.
