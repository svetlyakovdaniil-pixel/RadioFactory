# 03_Live_Worker_Lifecycle

## Purpose

The Live Worker is responsible for keeping a YouTube LIVE channel running continuously with minimal operator intervention.

---

## Startup Sequence

1. Worker process starts.
2. Configuration is loaded.
3. Channel configuration is validated.
4. `state.json` is loaded.
5. Existing broadcast state is evaluated.
6. Recovery logic decides whether to resume or create a broadcast.

---

## Main Lifecycle

```text
Worker starts
      ↓
Load configuration
      ↓
Load persistent state
      ↓
Recover active broadcast (if possible)
      ↓
Select next audio track
      ↓
Select loop video
      ↓
Prepare FFmpeg command
      ↓
Start RTMP publishing
      ↓
Verify stream health
      ↓
Monitor continuously
      ↓
Track rotation
      ↓
Broadcast deadline reached
      ↓
Finish current broadcast
      ↓
Create next broadcast
      ↓
Repeat
```

## Persistent State

The worker stores operational information in `state.json`.

Typical responsibilities include:
- active broadcast identifier
- stream identifier
- current media position
- current track index
- timestamps
- recovery information

The persistent state allows recovery after process or server restarts.

---

## Continuous Monitoring

The worker continuously checks:

- FFmpeg process health
- RTMP availability
- YouTube broadcast state
- playback progress
- configured deadlines

Failures trigger recovery procedures instead of requiring operator action.

---

## Recovery Philosophy

Recovery always attempts to preserve the existing broadcast before creating a new one.

Typical order:

1. Restore worker state.
2. Validate existing broadcast.
3. Resume streaming if possible.
4. Create a replacement only when recovery is impossible.

---

## Track Rotation

When a track finishes:

- choose the next eligible track
- update persistent state
- continue streaming without interrupting the broadcast

---

## Broadcast Rotation

Broadcasts have a finite lifetime.

When the configured duration expires:

- finish the current broadcast cleanly
- prepare the next broadcast
- bind the stream
- continue transmission

The transition should require no manual intervention.

---

## Design Goals

- automatic recovery
- deterministic behaviour
- persistent state
- no duplicate broadcasts
- minimal downtime
- predictable operation

