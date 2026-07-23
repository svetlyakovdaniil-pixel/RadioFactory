# FFmpeg Specification (Update 17B)

## 7. Command Construction

Arguments are built from validated configuration only.

Rules:

- deterministic ordering
- validated paths
- explicit codecs
- explicit bitrate
- explicit reconnect settings

---

## 8. Process Monitoring

Worker continuously monitors:

- stdout
- stderr
- exit code
- CPU usage
- memory usage
- process lifetime

Unexpected termination generates a domain event.

---

## 9. Exit Codes

Exit codes are classified into:

- Success
- Configuration Failure
- Input Failure
- Network Failure
- Encoder Failure
- Unknown Failure

---

## 10. Restart Policy

Transient failures use exponential backoff.

Permanent configuration errors are never retried.

Restart history is persisted.

---

## 11. Performance Requirements

Startup time must be measurable.

Encoding latency and resource usage are exported as metrics.

---

## 12. Constraints

FFmpeg never owns business state.

Process replacement must not affect domain logic.
