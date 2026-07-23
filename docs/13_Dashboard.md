# Dashboard Specification (Update 20A)

## 1. Purpose

Dashboard provides the operational interface for RadioFactory.

It visualizes confirmed system state without owning business logic.

---

## 2. Responsibilities

- display Station state
- display Broadcast state
- display Worker health
- submit user commands
- present diagnostics

---

## 3. Non-Responsibilities

Dashboard never:

- executes business rules
- talks directly to providers
- modifies aggregates
- stores runtime state

---

## 4. Data Model

Dashboard consumes read models only.

Write operations are performed through application commands.

---

## 5. Update Model

UI reflects confirmed events from the Event Bus.

Optimistic state is prohibited unless explicitly marked.

---

## 6. Invariants

- read-only projections
- deterministic rendering
- command/query separation
- infrastructure independence
