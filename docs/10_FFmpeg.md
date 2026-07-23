# FFmpeg Specification (Update 17C)

## 13. Graceful Shutdown

Shutdown sequence:

1. Stop accepting new input.
2. Flush encoder buffers.
3. Close RTMP connection.
4. Wait for process exit.
5. Record exit metadata.

Forced termination is a separate workflow.

---

## 14. Worker Interaction

Worker is the only component allowed to:

- start FFmpeg
- stop FFmpeg
- restart FFmpeg
- collect telemetry

FFmpeg never communicates with Station directly.

---

## 15. Observability

Required telemetry:

- process uptime
- restart count
- average startup time
- average bitrate
- dropped frames
- reconnect count

Every execution is linked by correlationId.

---

## 16. Diagnostics

Diagnostic output includes:

- command line
- sanitized environment
- exit code
- stderr summary
- execution duration

Secrets must never appear in diagnostics.

---

## 17. Security

Validate executable path before launch.

Reject untrusted arguments.

Execute with least required privileges.

---

## 18. Architectural Constraints

FFmpeg is replaceable without changing domain logic.

No business rules may exist in process management.

Version 1 complete.
