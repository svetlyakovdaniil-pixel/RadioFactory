# Worker Specification (Update 15A)

## 1. Purpose

Worker executes the Station lifecycle.

Worker contains orchestration only and never owns business decisions.

---

## 2. Responsibilities

- execute lifecycle commands
- coordinate Provider operations
- control encoder processes
- monitor runtime health
- publish execution events

Worker never stores business state.

---

## 3. Startup

1. Load configuration.
2. Restore Station.
3. Restore active Broadcast.
4. Validate runtime.
5. Start monitoring loop.

---

## 4. Main Loop

Worker repeatedly:

- processes commands
- checks timers
- verifies health
- dispatches events

Loop iterations must be deterministic.

---

## 5. Invariants

- One Worker controls one Station.
- Commands execute sequentially.
- No concurrent lifecycle transitions.
- Runtime decisions are reproducible.

---

## 6. Domain Events

- WorkerStarted
- WorkerStopped
- WorkerRecovered
- WorkerHealthChanged
- WorkerFailureDetected
