# API Guidelines (Update 34B)

## 7. Resource Naming

Endpoints use consistent, descriptive resource names.

Naming conventions remain stable across API versions.

---

## 8. Request and Response Structure

Requests and responses follow a consistent schema.

Optional fields are explicitly documented.

---

## 9. Error Handling

Errors return:

- consistent status codes
- machine-readable error identifiers
- human-readable messages
- traceable request identifiers where applicable

---

## 10. Pagination and Filtering

Collection endpoints support documented pagination and filtering mechanisms.

Behavior remains predictable across endpoints.

---

## 11. Idempotency

Operations intended to be idempotent behave consistently across repeated requests.

Idempotency requirements are documented.

---

## 12. Backward Compatibility

Breaking API changes require explicit versioning.

Backward compatibility is maintained whenever practical.
