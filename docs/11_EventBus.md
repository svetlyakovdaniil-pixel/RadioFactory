# Event Bus Specification (Update 18B)

## 7. Delivery Guarantees

Supported guarantees:

- at-most-once
- at-least-once
- exactly-once (logical, via idempotency)

The transport implementation defines the physical guarantee.

---

## 8. Subscriber Model

Subscribers:

- register interest in event types
- acknowledge completed processing
- remain isolated from publishers

Subscriber failures never corrupt event payloads.

---

## 9. Idempotency

Every event carries a unique eventId.

Consumers must safely ignore duplicate deliveries.

Processing the same event twice must produce the same final state.

---

## 10. Dead Letter Strategy

Events that repeatedly fail processing are moved to a Dead Letter Queue.

Original payload and metadata are preserved.

---

## 11. Replay

Replay is supported using immutable stored events.

Replay never changes historical event content.

---

## 12. Error Handling

Delivery errors are classified as:

- transient
- permanent
- configuration

Recovery policy depends on the classification.
