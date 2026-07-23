# Station Specification (Update 13B)

# 9. Pending LIVE Package

Pending LIVE Package is an immutable snapshot describing everything required
to start exactly one Broadcast.

It contains:

- StationId
- Target YouTube Channel
- Selected audio playlist
- Selected loop video
- Stream title
- Description
- Thumbnail reference
- Stream key reference
- Planned start parameters
- Generated metadata

Once created, the package is never modified.

If any element changes, the package is discarded and a new one is built.

---

# 10. Start Algorithm

Normal start sequence:

1. Verify UserIntent == Running.
2. Verify Station is Idle.
3. Validate media library.
4. Build Pending LIVE Package.
5. Reserve Station runtime.
6. Ask Worker to create YouTube Broadcast.
7. Wait until stream_ready.
8. Launch FFmpeg.
9. Verify encoder health.
10. Publish StationStarted.

If any mandatory step fails,
the sequence stops immediately and enters recovery or error handling.

---

# 11. Worker Interaction

Station never manipulates FFmpeg directly.

Worker responsibilities:

- launch encoder;
- stop encoder;
- monitor encoder;
- report status;
- collect runtime metrics.

Station responsibilities:

- decide WHEN actions happen;
- validate state;
- publish events.

---

# 12. Broadcast Interaction

Station owns Broadcast lifecycle.

Broadcast never decides:

- when to start;
- when to stop;
- which media to use.

Broadcast reports facts.

Station decides actions.

---

# 13. Internal Timers

Station maintains logical timers such as:

- startup timeout;
- stream_ready timeout;
- health check interval;
- recovery timeout;
- graceful stop timeout.

Timer expiration creates domain events.

Timers never execute business logic directly.

---

# 14. State Transition Rules

Idle -> Preparing

Allowed only when:
- UserIntent = Running
- no active Broadcast

Preparing -> Starting

Allowed only after Pending LIVE Package is complete.

Starting -> Running

Allowed only after encoder verification.

Running -> Stopping

Only user request or planned shutdown.

Stopping -> Cleanup

Always mandatory.

Cleanup -> Idle

Only after runtime resources are released.

No transition may bypass Cleanup after a normal stop.

This document replaces the previous version of 05_Station.md and extends it.
