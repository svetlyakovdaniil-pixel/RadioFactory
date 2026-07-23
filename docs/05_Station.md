# Station (Update 08)

## Runtime State

Runtime state exists only while the Station is active.

Persistent state:
- configuration
- user intent
- recovery metadata

Runtime state:
- current track
- playback position
- ffmpeg process
- current Broadcast reference

After a restart, runtime state is reconstructed rather than trusted blindly.

## Concurrency Rules

Only one lifecycle operation may execute at a time.

Read operations must never block lifecycle transitions.
