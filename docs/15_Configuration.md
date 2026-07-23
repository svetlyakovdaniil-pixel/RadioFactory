# Configuration Specification (Update 22B)

## 7. Configuration Files

Configuration files use explicit schemas.

Unknown fields are rejected.

Required values are validated during startup.

---

## 8. Validation

Validation includes:

- required fields
- type checking
- range validation
- dependency validation
- duplicate detection

Startup fails if validation fails.

---

## 9. Secrets

Secrets are separated from regular configuration.

Requirements:

- no hardcoded secrets
- no logging of secrets
- secure providers preferred

---

## 10. Environment Profiles

Supported profiles may include:

- development
- testing
- staging
- production

Profiles inherit common configuration where appropriate.

---

## 11. Reloading

Reloadable configuration is explicitly marked.

Unsafe configuration requires service restart.

---

## 12. Compatibility

Configuration changes must preserve backward compatibility whenever possible.

Breaking changes require migration guidance.
