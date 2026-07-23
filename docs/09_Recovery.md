# Recovery (Update 09)

## Consistency Rules

Recovery completes only after runtime state, persisted metadata and Broadcast state agree.

Partial recovery must never be reported as success.

Consistency verification is the final recovery step.
