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

## Install

Copy the `workstream-plan` folder into your Codex skills directory:

```bash
~/.codex/skills/workstream-plan
```

On Windows:

```powershell
$env:USERPROFILE\.codex\skills\workstream-plan
```

## Use

Invoke it directly:

```text
Use $workstream-plan to turn this product spec into an agent-ready workstream implementation plan.
```

Example:

```text
Use $workstream-plan. I want to add a web command center to my existing CLI product. It should reuse the current backend, preserve billing limits, and split the build into subagent workstreams.
```

## Why

Most implementation plans are too vague for AI coding agents. They say things like "add auth", "connect provider", or "build dashboard" without exact files, contracts, tests, protected behavior, or failure states.

This skill forces the plan to become an execution contract.
