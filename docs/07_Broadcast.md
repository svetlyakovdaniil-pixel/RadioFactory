# Broadcast Specification (Update 14A)

# 1. Purpose

Broadcast represents exactly one YouTube LIVE session.

It is created by Station and exists until cleanup completes.

Broadcast never decides business logic.

---

# 2. Responsibilities

Broadcast is responsible for:

- identity of the LIVE session;
- runtime lifecycle;
- recovery metadata;
- timing information;
- completion status.

Broadcast is NOT responsible for:

- media selection;
- scheduling;
- user commands;
- dashboard rendering.

---

# 3. Lifecycle

Created
↓
Prepared
↓
WaitingStreamReady
↓
Streaming
↓
Recovering
↓
Finishing
↓
Finished

Failed state may be entered from any active phase.

---

# 4. Identity

Required identifiers:

- BroadcastId
- StationId
- YouTubeBroadcastId

These identifiers never change.

---

# 5. Runtime Data

Runtime:

- stream health
- encoder state
- playback position
- recovery attempt count

Persistent:

- creation time
- finish time
- recovery history

---

# 6. Invariants

1. One Broadcast belongs to exactly one Station.
2. One Station owns at most one active Broadcast.
3. Recovery never duplicates Broadcast identity.
4. Finished Broadcasts are immutable.

---

# 7. Domain Events

- BroadcastCreated
- BroadcastStarted
- BroadcastRecovered
- BroadcastFinishing
- BroadcastFinished
- BroadcastFailed

Events describe completed facts only.
