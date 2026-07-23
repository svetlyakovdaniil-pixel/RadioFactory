# API Specification (Update 21C)

## 13. Authentication

Clients authenticate before invoking protected endpoints.

Supported mechanisms are implementation-specific but the domain remains authentication-agnostic.

---

## 14. Authorization

Authorization is enforced by the application layer.

Every request is evaluated against the caller's permissions.

---

## 15. Observability

API exposes:

- request latency
- error rate
- throughput
- active connections
- websocket sessions

Every request carries a correlationId.

---

## 16. Rate Limiting

Rate limits protect system stability.

Limit responses are deterministic and include retry guidance.

---

## 17. Security

Requirements:

- TLS for transport
- input validation
- output encoding
- no secret leakage
- audit of privileged operations

---

## 18. Architectural Constraints

API remains a thin application boundary.

No business rules or infrastructure-specific behavior belong in controllers.

API Version 1 specification complete.
