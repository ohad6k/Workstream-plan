# Workstream Plan Skill

An agent-ready planning skill for turning product ideas, rough specs, or architecture discussions into detailed implementation workstreams.

The core idea:

> If implementation agents still have to guess, the plan is not done.

This skill helps Codex write build plans that include:

- verified architecture assumptions
- V1 scope and non-goals
- screen-by-screen UX or flow specs
- data models and API contracts
- state models
- security and privacy rules
- entitlement and billing guardrails
- small workstreams with owned files
- exact tests and acceptance criteria
- subagent execution rules
- regression protection

It now defaults to writing the full plan into a Markdown file instead of leaving the full output only in chat.

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

Then invoke it in Claude Code as a custom command or by pasting the command contents into your session context.

## Install In Cursor

This repo includes a Cursor rule adapter at `adapters/cursor/workstream-plan.mdc`.

Install it by copying that file to:

```text
.cursor/rules/workstream-plan.mdc
```

Use it as a project rule or paste its contents into a project-specific Cursor rule.

## Use

Invoke it directly:

```text
Use $workstream-plan to turn this product spec into an agent-ready workstream implementation plan.
```

Example:

```text
Use $workstream-plan. I want to add a web command center to my existing CLI product. It should reuse the current backend, preserve billing limits, and split the build into subagent workstreams.
```

If you want an explicit artifact path:

```text
Use $workstream-plan and write the full plan to docs/plans/web-cockpit-master-plan.md.
```

## Why

Most implementation plans are too vague for AI coding agents. They say things like "add auth", "connect provider", or "build dashboard" without exact files, contracts, tests, protected behavior, or failure states.

This skill forces the plan to become an execution contract.
