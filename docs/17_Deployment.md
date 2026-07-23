# Deployment Specification (Update 24B)

## 7. Deployment Artifacts

Every release artifact is immutable.

Artifacts include:

- application binaries
- static assets
- manifests
- deployment metadata

Artifacts are uniquely identifiable.

---

## 8. Update Strategy

Updates follow a controlled deployment process.

Requirements:

- ordered rollout
- validation before activation
- automatic failure detection
- rollback support

---

## 9. Rollback

Rollback restores the last verified release.

Rollback procedures are deterministic and documented.

---

## 10. Migrations

Schema and data migrations execute in a controlled sequence.

Migration failures prevent deployment completion.

---

## 11. Health Checks

Services expose:

- startup status
- readiness
- liveness

Traffic is accepted only after readiness succeeds.

---

## 12. Dependency Lifecycle

External dependencies are versioned.

Dependency compatibility is validated before deployment.
