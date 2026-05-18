## Why
Agent-authored messages are not clearly distinguishable from other assistant messages in the transcript UI. This reduces provenance, operator trust, and debugging clarity in multi-actor workflows.

## What Changes
- Add an agent footer to messages authored by `author.type = "agent"`.
- Footer content format: `<displayName> · <role>`.
- Apply deterministic fallbacks when metadata is missing:
- `displayName` fallback: `Agent`
- `role` fallback: `Unknown role`
- Render the footer consistently anywhere orchestrator transcript messages are displayed.
- Do not render this footer for non-agent-authored messages.

## Impact
- Improves traceability and operator confidence in message provenance.
- Introduces a small, intentional UI metadata addition on agent-authored messages.
- Requires view-model plumbing updates for author metadata and fallback resolution.
- Requires unit and transcript-surface regression coverage for gating and fallback behavior.