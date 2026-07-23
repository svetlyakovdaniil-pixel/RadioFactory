# Station Specification (Update 13A)

# 1. Purpose

Station is the central domain object of RadioFactory.

A Station represents one autonomous automation pipeline capable of preparing,
starting, monitoring, recovering and stopping one continuous YouTube stream.

Station is responsible for business decisions.

Station is NOT responsible for:

- FFmpeg implementation;
- Dashboard rendering;
- direct YouTube API calls;
- filesystem implementation details.

---

# 2. Responsibilities

Station is responsible for:

- lifecycle management;
- media selection requests;
- recovery decisions;
- runtime supervision;
- event publication;
- interaction with Workspace.

---

# 3. Lifecycle

Idle
↓
Preparing
↓
Creating Broadcast
↓
Waiting Stream Ready
↓
Starting Encoder
↓
Running
↓
Stopping
↓
Cleanup
↓
Idle

Failure may occur from every active state.

---

# 4. Station State

Persistent State

- StationId
- Name
- Configuration
- UserIntent
- Recovery Metadata

Runtime State

- Active Broadcast
- Current Track
- Playback Position
- Active FFmpeg PID
- Runtime Timers

Runtime state must never be considered authoritative after process restart.

It is reconstructed.

---

# 5. Command Processing

Accepted commands:

- Start
- Stop
- Force Stop
- Restart
- Validate Library
- Refresh Media

Rules

Exactly one lifecycle command may execute simultaneously.

Repeated Start while Running returns Success(NoOp).

Repeated Stop while Idle returns Success(NoOp).

Commands are immutable.

---

# 6. Events

Station publishes:

- StationPreparing
- StationStarted
- BroadcastCreated
- BroadcastRecovered
- TrackChanged
- StationStopping
- StationStopped
- StationFailed

Events describe facts.

Events never request work.

---

# 7. Invariants

The following rules MUST NEVER be violated.

1. One Station owns at most one active Broadcast.

2. Station never manipulates another Station.

3. User Stop has priority over automatic recovery.

4. Cleanup always completes before a new Broadcast starts.

5. Pending LIVE Package is immutable once created.

6. Runtime failures never modify configuration.

---

# 8. Edge Cases

Application restart during Preparing.

Required behaviour:

- restore intent;
- inspect state;
- continue preparation if safe;
- otherwise restart preparation cleanly.

Application restart during Running.

Required behaviour:

- inspect Broadcast;
- decide recovery strategy;
- restore playback when allowed.

Unexpected Worker crash.

Required behaviour:

- Worker replaced;
- Station state preserved;
- duplicate Broadcast prohibited.

---

This is Part A of the complete Station specification.
Subsequent updates will extend this SAME file rather than creating new files.
