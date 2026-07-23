# Security Specification (Update 23A)

## 1. Purpose

Security protects RadioFactory assets, services and users.

Security requirements apply across every architectural layer.

---

## 2. Responsibilities

Security is responsible for:

- authentication
- authorization
- secret protection
- secure communication
- auditing

---

## 3. Non-Responsibilities

Security does not define:

- business rules
- application workflows
- domain behavior

---

## 4. Trust Model

Every external actor is considered untrusted until authenticated.

Trust is explicitly established and continuously verified.

---

## 5. Security Domains

Primary domains:

- client
- API
- application
- infrastructure
- external services

Boundaries are explicitly defined.

---

## 6. Invariants

Security must be:

- least privilege
- deny by default
- auditable
- deterministic
- versioned
