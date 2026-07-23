# Event Bus Specification (Update 18C)

## 13. Ordering

Ordering is guaranteed per publisher.

Cross-publisher ordering is undefined unless explicitly coordinated.

---

## 14. Observability

Required metrics:

- published events
- delivered events
- failed deliveries
- replay count
- queue depth
- delivery latency

All telemetry includes correlationId.

---

## 15. Performance

Publishing must be non-blocking for independent subscribers.

Slow consumers must not block unrelated event processing.

---

## 16. Security

Only trusted publishers may publish events.

Payload integrity must be verifiable.

Sensitive fields are protected from unauthorized consumers.

---

## 17. Scalability

Multiple Event Bus implementations may exist.

Domain contracts remain unchanged regardless of transport technology.

---

## 18. Architectural Constraints

Business logic never depends on the messaging implementation.

Event Bus Version 1 specification complete.
