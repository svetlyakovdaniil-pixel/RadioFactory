# Integration Guidelines (Update 36B)

## 7. Integration Contracts

Every integration defines a documented contract covering supported operations, payloads and compatibility expectations.

---

## 8. Message Exchange

Message formats remain consistent and version-aware.

Required and optional fields are explicitly documented.

---

## 9. Error Handling

Integration failures return predictable error information.

Retries distinguish transient failures from permanent errors.

---

## 10. Timeouts and Retries

Timeouts and retry policies are documented for every integration.

Retry strategies avoid duplicate processing.

---

## 11. Idempotency

Repeated requests produce predictable results where supported.

Idempotent operations are clearly identified.

---

## 12. Integration Monitoring

Integrations expose operational metrics, health status and logging sufficient for diagnostics and auditing.
