# Testing Specification (Update 25B)

## 7. Unit Testing

Unit tests validate isolated components.

Requirements:

- deterministic execution
- no external dependencies
- fast execution
- clear assertions

---

## 8. Integration Testing

Integration tests verify interaction between components.

External services may be replaced by controlled test doubles where appropriate.

---

## 9. End-to-End Testing

End-to-end tests validate complete user workflows.

Scenarios represent production behavior.

---

## 10. Test Data

Test data must be:

- reproducible
- isolated
- versioned
- disposable

Sensitive production data is never used directly.

---

## 11. Performance Testing

Performance tests measure:

- latency
- throughput
- resource usage
- scalability

---

## 12. Continuous Integration

Automated tests execute during CI before release.

Failing tests block deployment.
