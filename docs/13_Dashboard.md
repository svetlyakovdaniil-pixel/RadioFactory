# Dashboard Specification (Update 20B)

## 7. Screen Model

Core views:

- Overview
- Stations
- Broadcasts
- Workers
- Logs
- Diagnostics

Each screen consumes read models only.

---

## 8. User Commands

Supported commands:

- Start Station
- Stop Station
- Restart Worker
- Refresh State

Commands are validated by the application layer.

---

## 9. Real-Time Updates

Dashboard subscribes to Event Bus projections.

Updates are incremental and ordered.

Disconnected clients automatically resynchronize.

---

## 10. Error Handling

Errors are classified:

- validation
- authorization
- infrastructure
- transient

User-facing messages remain implementation-agnostic.

---

## 11. Authorization

Permissions are role-based.

UI hides unavailable actions.

Server remains the source of authorization truth.

---

## 12. Application Interaction

Dashboard never bypasses the application layer.

All writes are performed through commands.

All reads use query models.
