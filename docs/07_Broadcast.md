# Broadcast (Update 04)

## Sequence: Recovery (<3 min)

```text
Failure
 │
 ▼
Recovery detects outage
 │
 ▼
Same Broadcast valid?
 │
 ├─ No → New Broadcast
 │
 └─ Yes
      │
      ▼
Restore playback position
      │
      ▼
Continue same LIVE
```

## Recovery Invariant

The recovery procedure must never create a second active Broadcast for the same Station.
