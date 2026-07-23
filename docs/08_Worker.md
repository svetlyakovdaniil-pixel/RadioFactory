# Worker Specification (Update 15C)

## 13. Recovery After Restart

Worker startup recovery:

1. Load persisted Station state.
2. Load persisted Broadcast state.
3. Detect active encoder process.
4. Reconcile runtime with persisted state.
5. Resume monitoring loop.

Recovery must never create duplicate runtime objects.

---

## 14. Runtime Reconciliation

Worker compares:

- persisted state
- provider state
- local runtime
- operating system process state

Conflicts are resolved using deterministic reconciliation rules.

---

## 15. Graceful Shutdown

Shutdown sequence:

1. Stop accepting new commands.
2. Finish active command.
3. Flush pending events.
4. Stop monitoring.
5. Stop encoder.
6. Persist final runtime.
7. Exit.

Forced termination is handled separately.

---

## 16. Failure Escalation

Repeated failures move through:

Warning
→ Recovery
→ Failure
→ Manual Intervention

Escalation policy is configurable.

---

## 17. Observability

Required metrics:

- worker uptime
- queue length
- recovery duration
- restart count
- command latency
- shutdown duration

Every operation carries a correlationId.

---

## 18. Implementation Constraints

Worker is stateless regarding business rules.

Only Station determines lifecycle decisions.

Worker Version 1 specification complete.
