# API Specification (Update 21B)

## 7. REST API

Resources expose application capabilities only.

Rules:

- resource-oriented URLs
- versioned endpoints
- explicit HTTP methods
- normalized responses

---

## 8. WebSocket

Server publishes:

- state updates
- domain events
- diagnostics
- notifications

Clients never invoke business logic directly over events.

---

## 9. DTO Model

DTOs are immutable.

Rules:

- explicit schema
- backward compatible additions
- no infrastructure types
- stable identifiers

---

## 10. Error Model

Responses contain:

- errorCode
- message
- correlationId
- details (optional)

Internal exceptions never leak to clients.

---

## 11. Idempotency

Commands may include an idempotency key.

Repeated requests must not duplicate completed operations.

---

## 12. Versioning

Breaking changes require a new API version.

Multiple API versions may coexist.
