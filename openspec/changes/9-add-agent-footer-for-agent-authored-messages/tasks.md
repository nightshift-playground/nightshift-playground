## 1. Author Metadata Plumbing
- [ ] Identify the canonical message author source in orchestrator message models.
- [ ] Ensure transcript/render view models include `author.type`, `author.displayName`, and optional `author.role` for agent-authored messages.
- [ ] Add fallback derivation in view-model mapping:
- [ ] Missing `displayName` -> `Agent`
- [ ] Missing `role` -> `Unknown role`

## 2. Footer Rendering
- [ ] Add footer rendering for messages where `author.type === "agent"`.
- [ ] Footer format: `<displayName> · <role>` using resolved fallback values.
- [ ] Keep footer styling consistent with existing message metadata/secondary text patterns.
- [ ] Ensure non-agent messages never render the agent footer.

## 3. Validation
- [ ] Add/extend unit tests for:
- [ ] agent-authored message renders footer with explicit metadata.
- [ ] agent-authored message renders footer with missing role fallback.
- [ ] agent-authored message renders footer with missing displayName fallback.
- [ ] non-agent-authored messages do not render footer.
- [ ] Add/extend integration/snapshot tests for transcript surfaces that render messages.
- [ ] Run relevant test suites and verify pass.