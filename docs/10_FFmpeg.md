# FFmpeg Specification (Update 17A)

## 1. Purpose

FFmpeg is the media encoder used by Worker.

It is an infrastructure component only.

---

## 2. Responsibilities

- encode media
- transmit RTMP
- report process status
- expose exit codes

Business logic is outside FFmpeg.

---

## 3. Lifecycle

Created
→ Starting
→ Running
→ Restarting
→ Stopping
→ Stopped

Only one encoder process may exist.

---

## 4. Process Ownership

Worker owns the FFmpeg process.

No other component may start or stop FFmpeg directly.

---

## 5. Command Line

Command generation is deterministic.

Arguments are validated before execution.

---

## 6. Invariants

- one process
- deterministic startup
- reproducible command line
- no business state
