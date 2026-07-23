# Broadcast Specification (Update 14B)

## 8. Broadcast Creation Sequence

1. Station requests Broadcast creation.
2. Provider validates configuration.
3. YouTube Broadcast is created.
4. Stream is bound.
5. Runtime metadata is persisted.
6. Broadcast enters Prepared.

If any step fails, partial resources must be cleaned up.

---

## 9. State Transition Rules

Created -> Prepared
Prepared -> WaitingStreamReady
WaitingStreamReady -> Streaming
Streaming -> Recovering
Recovering -> Streaming
Streaming -> Finishing
Finishing -> Finished

Invalid transitions are rejected.

---

## 10. Recovery Model

Recovery reconstructs runtime using persisted metadata.

Recovery never creates a second Broadcast while one already exists.

Recovery resumes from the last confirmed state.

---

## 11. Provider Interaction

Broadcast never calls YouTube APIs directly.

All external operations go through the Provider abstraction.

Provider returns normalized results and domain errors.

---

## 12. Failure Categories

- Configuration
- Authentication
- API
- Network
- Stream
- Unknown

Each failure maps to a deterministic recovery policy.

---

## 13. Sequence Overview

Station
 -> Broadcast
 -> Provider
 -> YouTube
 <- Provider
 <- Broadcast
 <- Station

Every request has a matching completion event.
