# Storage Specification (Update 19A)

## 1. Purpose

Storage persists domain state independently of runtime.

Business logic never depends on a specific database technology.

---

## 2. Responsibilities

- persist aggregates
- load aggregates
- maintain consistency
- support transactions
- preserve audit history

---

## 3. Non-Responsibilities

Storage never:

- executes business rules
- calls external services
- publishes events
- controls lifecycle

---

## 4. Repository Contract

Repositories expose aggregate-oriented operations only.

Infrastructure entities never leak into the domain.

---

## 5. Aggregate Persistence

Each aggregate is persisted atomically.

Partial aggregate updates are prohibited unless explicitly defined.

---

## 6. Invariants

- aggregate consistency
- deterministic persistence
- stable identifiers
- infrastructure isolation
