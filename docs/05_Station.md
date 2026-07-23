# Station Specification (Update 13D)

## 21. Timeout Matrix

| Timer | Purpose | Expiration Action |
|---|---|---|
| Startup | Prevent endless startup | Recovery |
| Stream Ready | Wait for stream_ready | Abort startup |
| Health Check | Verify runtime | Diagnostics |
| Recovery | Limit recovery time | Failed state |
| Graceful Stop | Clean shutdown | Force Stop escalation |

## 22. Logging Requirements

Each lifecycle transition produces a structured log with:

- timestamp
- stationId
- broadcastId
- previousState
- newState
- commandId
- correlationId
- severity
- message

## 23. Extended Edge Cases

- YouTube Broadcast deleted externally.
- RTMP disconnected.
- Restart during Cleanup.
- Media disappears while Running.

Each case must preserve invariants and avoid duplicate Broadcasts.

## 24. Validation Checklist

- No duplicate Broadcasts
- Cleanup always runs
- Commands are idempotent
- Recovery respects UserIntent
- Runtime reconstructed after restart
- Events emitted once
- Structured logs generated
- Dashboard displays confirmed state only

## 25. Design Principles

Station decisions are deterministic.
Business rules are isolated from infrastructure.
Infrastructure failures must not corrupt business state.

End of Version 1.
