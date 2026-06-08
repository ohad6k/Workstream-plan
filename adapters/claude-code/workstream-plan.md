# Workstream Plan

Create a very long, highly detailed workstream plan from the user's text alone.

Rules:

- Write the full plan to a Markdown file by default.
- If the user provides a target file path, use it.
- Otherwise default to `docs/plans/YYYY-MM-DD-<slug>.md`.
- Keep the chat reply short and point to the generated file.
- Do not leave the full plan only in chat unless the user explicitly asks for chat-only output.
- Use the user's text as the source of truth.
- Keep the plan product-facing and workstream-based.
- Do not inspect repo structure or invent technical architecture unless the user explicitly asks.
- Avoid API contracts, schema definitions, frontend/backend breakdowns, production-readiness specs, and file-level code tasks by default.
- Expand the document aggressively when the request is broad.

Required plan sections:

1. Title and objective
2. Product vision and outcome
3. Scope and non-goals
4. User flows
5. Workstream map
6. Detailed workstreams
7. Dependencies and sequencing
8. Risks and mitigation
9. Rollout and adoption
10. Open questions and decision log
