# Storage Specification (Update 19B)

## 7. Transaction Model

Transactions guarantee atomic aggregate updates.

Rules:

- begin
- validate
- commit
- rollback

Nested business transactions are prohibited unless explicitly supported.

---

## 8. Concurrency

Supported strategies:

- optimistic concurrency
- pessimistic locking

Conflict detection is deterministic.

---

## 9. Failure Recovery

After failures Storage guarantees:

- committed data remains committed
- rolled back data remains invisible
- partial writes are rejected

---

## 10. Schema Migrations

Schema evolution is versioned.

Every migration is repeatable, auditable and reversible when possible.

---

## 11. Backup and Restore

Backups preserve:

- aggregate state
- audit history
- schema version

Restore validates consistency before activation.

---

## 12. Repository Rules

Repositories expose domain aggregates only.

Infrastructure details never cross repository boundaries.
