# Event Bus Specification (Update 18A)

## 1. Purpose

The Event Bus delivers domain events between components.

It provides transport only and contains no business logic.

---

## 2. Responsibilities

- publish events
- deliver events
- route subscribers
- preserve event metadata
- report delivery results

---

## 3. Non-Responsibilities

The Event Bus never:

- makes business decisions
- modifies event payloads
- retries business operations
- stores domain state

---

## 4. Event Contract

Every event contains:

- eventId
- eventType
- timestamp
- correlationId
- source
- payload

Events are immutable.

---

## 5. Delivery Model

Events are published after successful business operations.

Subscribers receive completed facts only.

---

## 6. Invariants

- immutable events
- deterministic routing
- ordered delivery per publisher
- transport independent of domain
