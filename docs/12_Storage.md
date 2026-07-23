# Storage Specification (Update 19C)

## 13. Observability

Storage exposes:

- transaction latency
- commit rate
- rollback rate
- query latency
- lock contention
- storage availability

All telemetry includes correlationId.

---

## 14. Audit

Audit records are immutable.

Each record contains:

- timestamp
- actor
- operation
- aggregateId
- correlationId

Audit history is never rewritten.

---

## 15. Retention Policy

Retention rules define:

- operational data lifetime
- audit retention
- backup retention
- archival policy

Expired data is removed only through approved retention workflows.

---

## 16. Security

Requirements:

- encrypt data at rest where applicable
- least-privilege access
- validated repository access
- secrets never stored in domain objects

---

## 17. Performance

Storage must support predictable latency.

Long-running operations are isolated from critical transactional paths.

---

## 18. Architectural Constraints

Storage is replaceable without changing domain logic.

Repositories remain the only persistence boundary.

Storage Version 1 specification complete.
