# Architecture (Update 03)

## Component Interaction

```text
Dashboard
    │
    ▼
 Backend/API
    │
    ├─────────────► Workspace
    │                  │
    │                  ▼
    │              Scheduler
    │                  │
    ▼                  ▼
  Station ◄──────── Worker
    │
    ▼
 Broadcast
```

## Dependency Rules

Allowed:
- Dashboard → Backend/API
- Backend/API → Workspace
- Workspace → Station
- Station → Worker
- Worker → Broadcast

Forbidden:
- Dashboard → FFmpeg
- Dashboard → Filesystem
- Station → Station
- Broadcast → Dashboard
- Worker → UI
