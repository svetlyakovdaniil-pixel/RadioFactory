# Worker Specification (Update 15B)

## 7. FFmpeg Lifecycle

Worker owns the encoder process.

Lifecycle:

Created
→ Starting
→ Running
→ Restarting
→ Stopping
→ Stopped

A single active encoder process is allowed.

---

## 8. Command Processing

Commands are processed sequentially.

Rules:

- FIFO queue
- exactly one active command
- cancellation is explicit
- completion is acknowledged

---

## 9. Heartbeat

Worker periodically publishes:

- uptime
- current state
- active broadcast
- encoder status
- last successful health check

Missing heartbeats trigger diagnostics.

---

## 10. Watchdog

Watchdog detects:

- hung encoder
- stalled startup
- dead process
- excessive restart rate

Watchdog never performs business decisions.

---

## 11. Retry Policy

Transient failures use exponential backoff.

Permanent failures immediately transition to Failure.

Retry history is persisted.

---

## 12. Thread Safety

Worker state is modified only inside the execution loop.

External components communicate through commands and events.

Shared mutable state is prohibited.
