# Architecture (Update 04)

## Sequence: Start Station

```text
User
 │
 ▼
Dashboard
 │ Start
 ▼
Backend/API
 │ Validate command
 ▼
Workspace
 │ Queue command
 ▼
Station
 │ Prepare
 │ Create Pending LIVE Package
 ▼
Worker
 │ Create YouTube LIVE
 │ Start FFmpeg
 ▼
Broadcast
 │ Running
 ▼
Dashboard updates status
```

### Rules

- Every command is acknowledged exactly once.
- Only Backend/API may accept user commands.
- Worker reports progress, never changes UI.
- Dashboard only visualizes confirmed state.
