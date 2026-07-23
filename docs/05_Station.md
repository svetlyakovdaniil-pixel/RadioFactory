# Station (Update 09)

## Command Idempotency

Receiving the same lifecycle command twice must not create duplicate side effects.

Examples:
- StartStation while Running -> no-op.
- StopStation while Idle -> no-op.

Each command returns an explicit result.
