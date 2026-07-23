# API Specification (Update 21A)

## 1. Purpose

The API exposes RadioFactory capabilities to external clients.

The API is an application boundary and contains no domain logic.

---

## 2. Responsibilities

- accept commands
- execute queries
- authenticate callers
- authorize operations
- return normalized responses

---

## 3. Non-Responsibilities

The API never:

- modifies domain rules
- bypasses application services
- accesses infrastructure directly
- persists domain state

---

## 4. API Model

The API follows Command/Query separation.

Commands modify state.

Queries never modify state.

---

## 5. Transport

Supported transports may include:

- REST
- WebSocket

Transport technology never changes application contracts.

---

## 6. Invariants

- deterministic responses
- versioned contracts
- immutable DTO definitions
- application boundary isolation
