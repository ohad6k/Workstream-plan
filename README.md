# Workstream Plan Skill

A long-form planning skill for turning user prompts into very detailed workstream plans.

The core idea:

> If the request is substantial, the plan should be substantial too.

This skill is designed to write large Markdown planning documents from the user's text alone. It is not meant to default into API contracts, schema design, frontend/backend implementation, or production-readiness engineering specs.

## What It Produces

- very detailed product plans
- long workstream documents
- sequencing and dependency maps
- rollout and adoption thinking
- risks, blockers, and fallback paths
- broad planning depth from a short prompt

## Install In Codex

Copy the `workstream-plan` folder into your Codex skills directory:

```bash
~/.codex/skills/workstream-plan
```

On Windows:

```powershell
$env:USERPROFILE\.codex\skills\workstream-plan
```

## Install In Claude Code

This repo includes a Claude Code command adapter at `adapters/claude-code/workstream-plan.md`.

Install it by copying that file to:

```text
.claude/commands/workstream-plan.md
```

## Install In Cursor

This repo includes a Cursor rule adapter at `adapters/cursor/workstream-plan.mdc`.

Install it by copying that file to:

```text
.cursor/rules/workstream-plan.mdc
```

## Use

Invoke it directly:

```text
Use $workstream-plan to create a very detailed workstream plan from this product idea and write it to a markdown file.
```

Example:

```text
Use $workstream-plan. I want a very detailed workstream plan for a product that helps freelance designers manage client approvals, revisions, handoff, and payments.
```

If you want an explicit artifact path:

```text
Use $workstream-plan and write the full plan to docs/plans/designer-ops-plan.md.
```
