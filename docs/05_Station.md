# Station (Update 04)

## Command Processing

Station processes one lifecycle command at a time.

If another command arrives:

- incompatible command is rejected or queued;
- compatible read-only operations may continue.

## Ownership

Only Station may transition its lifecycle state.

External components request changes but do not mutate state directly.

## Events

Station emits domain events such as:

- StationStarted
- BroadcastPrepared
- BroadcastStarted
- BroadcastFinished
- RecoveryStarted
- RecoveryCompleted
- StationFailed

Consumers react to events instead of polling Station internals whenever possible.
