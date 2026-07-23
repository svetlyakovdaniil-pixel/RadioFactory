# Station Specification (Update 13C)

# 15. Recovery Workflow

Recovery is initiated only after Station determines that automatic restoration is
allowed by the current UserIntent.

Sequence:

1. Detect failure.
2. Freeze runtime state.
3. Verify active Broadcast.
4. Classify failure.
5. Decide recovery strategy.
6. Restore playback when applicable.
7. Publish RecoveryCompleted or StationFailed.

Recovery must never create a second active Broadcast.

---

# 16. Workspace Interaction

Workspace may:

- request Start;
- request Stop;
- enqueue lifecycle commands;
- provide shared configuration.

Workspace must never modify Station runtime state directly.

---

# 17. Dashboard Interaction

Dashboard is an observer.

Dashboard may:
- send commands through Backend;
- subscribe to Station events.

Dashboard must never infer Station state locally.

---

# 18. Sequence: Normal Stop

User
 ↓
Dashboard
 ↓
Backend
 ↓
Workspace
 ↓
Station
 ↓
Worker stops encoder
 ↓
Broadcast finalized
 ↓
Cleanup
 ↓
Idle

---

# 19. Forbidden Operations

Station must never:

- access another Station's runtime;
- bypass Cleanup;
- modify Pending LIVE Package;
- publish fake events;
- ignore explicit Stop requests;
- start a second Broadcast while one is active.

---

# 20. Developer Guidelines

When changing Station logic:

- preserve all invariants;
- keep commands idempotent;
- prefer events over direct coupling;
- isolate infrastructure from business rules;
- document every new lifecycle state.

This file replaces the previous version and extends the Station specification.
