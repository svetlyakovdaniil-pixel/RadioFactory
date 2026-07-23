# Deployment Specification (Update 24A)

## 1. Purpose

Deployment defines how RadioFactory is packaged, delivered, installed and started across supported environments.

Deployment must be deterministic, reproducible and auditable.

---

## 2. Responsibilities

Deployment is responsible for:

- service installation
- application startup
- dependency provisioning
- environment preparation
- release delivery

---

## 3. Non-Responsibilities

Deployment never defines:

- business rules
- domain workflows
- runtime decisions
- user data

---

## 4. Deployment Model

Deployment artifacts are immutable.

Each release is uniquely versioned and traceable.

Rollback always targets a previously released artifact.

---

## 5. Target Environments

Supported environments may include:

- development
- testing
- staging
- production

Environment-specific configuration remains external.

---

## 6. Invariants

Deployment must be:

- reproducible
- versioned
- observable
- deterministic
- recoverable
