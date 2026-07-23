# YouTube Provider Specification (Update 16A)

## 1. Purpose

The YouTube Provider isolates all communication with the YouTube API.

The domain layer never accesses YouTube directly.

---

## 2. Responsibilities

- Create Broadcast
- Create Stream
- Bind Stream to Broadcast
- Start monitoring
- Query runtime state
- Complete Broadcast
- Normalize API responses

---

## 3. Non-Responsibilities

The Provider does not:

- make business decisions;
- schedule broadcasts;
- choose media;
- control Station lifecycle.

---

## 4. Provider Contract

All operations return normalized domain results.

No raw Google API objects may leave the Provider boundary.

---

## 5. Core Operations

- CreateBroadcast
- CreateStream
- BindStream
- GetBroadcast
- GetStream
- DeleteTemporaryResources
- CompleteBroadcast

---

## 6. Invariants

Provider is stateless.

Operations are deterministic.

External API details remain hidden behind the contract.
