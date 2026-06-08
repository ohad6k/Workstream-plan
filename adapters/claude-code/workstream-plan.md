# Workstream Plan

Create an exhaustive, implementation-ready workstream plan from the user's product idea, spec, architecture notes, or roadmap discussion.

Rules:

- Write the full plan to a Markdown file by default.
- If the user provides a target file path, use it.
- If the repo already has a planning convention such as `docs/plans/` or `docs/superpowers/plans/`, reuse it.
- Otherwise default to `docs/plans/YYYY-MM-DD-<slug>.md`.
- Keep the chat reply short and point to the generated file.
- Do not leave the plan only in chat unless the user explicitly asks for chat-only output.
- Treat the plan as an execution contract, not strategy prose.
- Verify named files, modules, exports, routes, commands, and tests before referencing them.
- Prefer existing architecture over inventing new systems.
- For every manual user step, convert it into a guided action with exact destination, exact value, exact setting, and exact verification behavior.
- Break implementation into small additive workstreams with owned files, protected behavior, exact tests, dependencies, and acceptance criteria.
- Require implementation agents to preflight repo reality before editing and report mismatches instead of silently inventing alternate architecture.

Required plan sections:

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
