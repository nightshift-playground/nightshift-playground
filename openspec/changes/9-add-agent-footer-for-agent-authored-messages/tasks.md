## 1. Message Author Data
- [ ] Locate canonical message author source used by transcript rendering.
- [ ] Ensure message view model exposes `author.type`, `author.displayName`, and `author.role`.
- [ ] Implement fallback resolution in mapping layer:
- [ ] `displayName` => `Agent` when empty or missing.
- [ ] `role` => `Unknown role` when empty or missing.

## 2. Footer UI
- [ ] Render agent footer only when `author.type === "agent"`.
- [ ] Use resolved text format: `<displayName> · <role>`.
- [ ] Keep styling aligned with existing secondary/meta text patterns.
- [ ] Verify non-agent messages never render the footer.

## 3. Verification
- [ ] Add unit tests for:
- [ ] Agent message with explicit metadata.
- [ ] Agent message with missing `role` fallback.
- [ ] Agent message with missing `displayName` fallback.
- [ ] Agent message with both fields missing (`Agent · Unknown role`).
- [ ] Non-agent messages (user/system/assistant) do not show footer.
- [ ] Add or update transcript-level integration/snapshot coverage on affected surfaces.
- [ ] Run relevant test suites and confirm all pass.