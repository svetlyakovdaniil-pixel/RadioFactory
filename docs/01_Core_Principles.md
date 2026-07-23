# Core Principles (Update)

## Architectural Invariants

The following invariants must never be violated.

1. One Station owns at most one active Broadcast.
2. One Broadcast belongs to exactly one Station.
3. A Station never modifies another Station's runtime state.
4. Cleanup of one Broadcast never affects another Station.
5. Manual Stop always survives restart.
6. Automatic recovery never overrides explicit user intent.
7. Waiting for resources is not an Error state.
8. Active LIVE has higher priority than background work.

## Design Philosophy

RadioFactory is designed around isolation, recoverability and observability.

Every implementation decision should preserve these three properties.

If a new feature weakens one of them, the architecture must be reconsidered before implementation.
