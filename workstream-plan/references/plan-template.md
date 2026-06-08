# Workstream Plan Template

Use this template for substantial product or engineering plans. Delete sections only when they are genuinely irrelevant.

## 0. Output Artifact

Write the full plan to a Markdown file.

At the top of the file, include:

- plan title
- date
- owner or requesting context if relevant
- objective
- status: `draft`, `ready for review`, or `approved`

If the user did not provide a path, prefer:

- existing repo planning convention, if one exists
- otherwise `docs/plans/YYYY-MM-DD-<slug>.md`

The chat response should summarize the artifact and point to the file path instead of duplicating the full plan inline.

## 1. Title

`<Product/Feature Name> Agent-Ready Workstream Plan`

## 2. Objective

One sentence:

`Build <capability> by extending <existing product/system> so <target user> can <outcome>, while preserving <protected existing behavior>.`

## 3. Product Promise

Define:

- What the user can do after this ships.
- What the system automates.
- What the system guides but cannot automate.
- What the user never has to guess.
- What is explicitly not promised.

## 4. V1 Scope

Include:

- Supported user personas.
- Supported app/project types.
- Supported providers/integrations.
- Supported environments.
- Supported happy paths.
- Supported failure/recovery paths.

## 5. Non-Goals

Include:

- Not supported in V1.
- Coming soon only.
- Manual guided only.
- Deliberately excluded for safety, cost, or complexity.

## 6. Verified Current Architecture

For each item, include status:

- `Verified`: file/function/type exists and behavior was inspected.
- `Partially verified`: file exists but behavior needs implementation-time confirmation.
- `Unverified`: assumption that agents must confirm before editing.
- `Rejected`: plan assumption was false.

Cover:

- Backend runtime.
- Frontend runtime.
- Database/migrations.
- Auth/session.
- Billing/entitlements.
- Existing commands.
- Existing tests.
- Existing provider/integration modules.
- Deployment targets.

## 7. Architecture Decision

State the lowest-risk V1 approach.

Include:

- What runtime owns each API.
- Whether parity is required across runtimes.
- What stays local.
- What stays server-side.
- What is additive.
- What is behind a feature flag.
- What existing code is reused.
- What duplication is intentionally avoided.

## 8. UX / Flow Spec

For every screen or user step, include:

- Purpose.
- Fields.
- Primary buttons.
- Secondary buttons.
- Loading state.
- Empty state.
- Error state.
- Upgrade/entitlement state.
- Success state.
- Verification state.
- Exact text/value/destination for guided actions.

Never end a step with "do this manually" unless the plan also includes:

- exact button
- exact provider URL/destination
- exact value to paste or setting to choose
- exact explanation
- exact done marker
- exact verification state

## 9. Data Models

For each model/table/type, include:

- Name.
- Owner module.
- Fields.
- Field types.
- Required/optional behavior.
- Defaults.
- Indexes.
- Uniqueness constraints.
- Foreign keys.
- Row-level security or owner checks.
- Redaction rules.
- Retention rules.
- Migration notes.

## 10. API Contracts

For each endpoint or command:

- Method/name.
- Path.
- Auth requirement.
- Entitlement requirement.
- Request body.
- Response body.
- Error codes.
- Idempotency behavior.
- Rate/usage behavior.
- Audit/log behavior.
- Tests.

## 11. State Models

For each state machine:

- State name.
- Meaning.
- Entry conditions.
- Exit conditions.
- UI button to show.
- Backend transition owner.
- Verification requirement.
- Failure behavior.
- Retry behavior.

## 12. Action Model

For guided or executable actions, define:

- id
- section
- provider
- title
- risk level
- execution mode
- requires local runner
- requires provider connection
- required inputs
- expected outputs
- exact destination
- exact value to copy
- verification method
- verification state
- rollback behavior
- proof behavior

## 13. Security and Privacy

Be explicit:

- What metadata may be sent to the web/server.
- What must never be sent.
- How secrets/env values are handled.
- How logs are redacted.
- How proof is redacted.
- How provider tokens are stored.
- How provider tokens are never stored, if applicable.
- How local runner trust is established.
- How repo ownership is checked.
- How private repo behavior works.
- How audit events are recorded.

## 14. Entitlements and Billing

Define:

- Existing plans reused.
- Limits per plan.
- When usage is consumed.
- When usage is not consumed.
- Upgrade state.
- Limit reached behavior.
- Cross-surface consistency across web/CLI/extension.
- Protected billing behavior that must not change.

Keep product billing separate from user app provider billing. Do not reuse subscription names or payment state concepts across those domains.

## 15. Workstream Dependency Map

Example:

```text
W0 Audit/spec guardrails
  -> W1 Database/API foundation
  -> W2 Frontend shell
  -> W3 Provider selection
  -> W4 Runner pairing
  -> W5 Runner jobs/proof
  -> W6 Guided provider playbooks
  -> W7 Readiness/rescan
  -> W8 Entitlement/security hardening
  -> W9 Demo/marketing real states
  -> W10 Regression/final review
```

Use the actual dependency graph for the project.

## 16. Workstream Template

### W<n>. `<Name>`

**Objective**

Build `<specific outcome>`.

**Preflight**

Before editing, confirm:

- `<file/module>` exists.
- `<function/export/type>` exists.
- `<route/command/component>` behavior matches this plan.
- `<test command>` currently passes or known failures are documented.

If any preflight item is false, stop and report the mismatch. Do not invent alternate architecture silently.

**Owned Files**

Expected write scope:

- `<path>`
- `<path>`

**Read-First Files**

Inspect before editing:

- `<path>`
- `<path>`

**Protected Behavior**

Do not change:

- `<billing/auth/CLI/extension/scan/session/provider behavior>`
- `<specific command/route/UI behavior>`

**Implementation Steps**

1. `<step>`
2. `<step>`
3. `<step>`

**Contracts**

Types, fields, routes, commands, or state changes owned by this workstream:

```ts
type Example = {
  id: string;
};
```

**Tests**

Add/update:

- `<test file>`

Run:

```bash
<command>
```

**Acceptance Criteria**

- `<observable condition>`
- `<observable condition>`

**Risks / Known Gaps**

- `<risk>`

**Report Format**

The agent must report:

- files changed
- tests run
- existing behavior protected
- risks/known gaps
- next dependency

## 17. Regression Protection

List commands by layer:

```bash
<api tests>
<api typecheck>
<frontend tests>
<frontend build>
<cli tests>
<cli build>
<extension tests>
<extension compile>
<smoke/e2e>
```

List behavior that must be protected:

- Current auth/session behavior.
- Current billing/plan limits.
- Current scan behavior.
- Current CLI commands.
- Current extension behavior.
- Current provider detection behavior.
- Current marketing/demo behavior, if relevant.

## 18. Acceptance Criteria

Before calling the full plan complete:

- Every V1 scope item has a workstream.
- Every workstream has preflight, owned files, tests, and acceptance criteria.
- Every data model has owner/auth/privacy rules.
- Every user flow has error/loading/empty/upgrade states.
- Every manual step is guided with destination/value/verification.
- Every provider/integration has failure states.
- Existing product behavior has explicit regression protection.
- Final review includes spec compliance and code quality review.

## 19. Final Review Loop

For subagent-driven implementation:

1. Dispatch one implementation agent per workstream.
2. Require preflight before editing.
3. Require commit or clear patch report.
4. Dispatch spec compliance review.
5. Fix spec gaps.
6. Dispatch code quality review.
7. Fix quality issues.
8. Repeat until approved.
9. Run controller-owned regression.
10. Dispatch final whole-implementation review.
11. Fix final blockers.
12. Run final regression.

## 20. Risks and Open Questions

Separate:

- Blockers before coding.
- Risks that can be handled during implementation.
- Product decisions needed from the user.
- Technical debt intentionally deferred.
- Cost or operational risks.

Ask only questions that block a correct plan. For everything else, make a conservative assumption and label it.
