# Architecture (Update 09)

## Domain Event Catalog

Core events:
- StationStarted
- StationStopped
- BroadcastCreated
- BroadcastRecovered
- BroadcastFinished
- MediaSelected
- RecoveryFailed

Rules:
- Events are immutable.
- Events are timestamped.
- Events have unique IDs.
- Events describe facts that already happened.
