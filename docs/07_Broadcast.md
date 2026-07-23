# Broadcast Specification (Update 14C)

## 14. Broadcast Completion

Completion begins only after Station issues Finish.

Steps:

1. Stop encoder.
2. Confirm stream termination.
3. Finalize YouTube Broadcast.
4. Persist final metadata.
5. Publish BroadcastFinished.
6. Release runtime resources.

Completion is idempotent.

---

## 15. Cleanup

Cleanup removes only temporary runtime resources.

Persistent audit data is never deleted.

Cleanup may safely execute multiple times.

---

## 16. Idempotency Rules

Repeated requests to:

- Finish
- Cleanup
- Recover

must always produce the same final state.

Duplicate external API calls must be avoided.

---

## 17. Consistency Rules

Broadcast state in memory,
persistent storage,
and Dashboard
must converge to the same confirmed state.

No optimistic UI state is authoritative.

---

## 18. Observability

Metrics:

- startup duration
- streaming duration
- recovery count
- failure count
- cleanup duration

Tracing uses correlationId across all operations.

---

## 19. Implementation Requirements

Business logic is deterministic.
Infrastructure adapters remain replaceable.
No Provider-specific logic leaks into the domain.

Broadcast Version 1 specification complete.
