## 1. Configuration
- [ ] 1.1 Add orchestrator config for generated spec auto-accept (default: disabled).
- [ ] 1.2 Validate config parsing and fallback behavior when unset.

## 2. Workflow Behavior
- [ ] 2.1 Update generated-spec acceptance flow to bypass manual wait when auto-accept is enabled.
- [ ] 2.2 Preserve existing manual acceptance gate when auto-accept is disabled.
- [ ] 2.3 Ensure downstream phases receive accepted status in both paths.

## 3. Observability
- [ ] 3.1 Emit status/log entry indicating spec was auto-accepted.
- [ ] 3.2 Include acceptance mode (manual/auto) in relevant run metadata if available.

## 4. Validation
- [ ] 4.1 Add/adjust tests for enabled and disabled auto-accept scenarios.
- [ ] 4.2 Add/adjust regression test to ensure default behavior remains manual acceptance.