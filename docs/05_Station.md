# Station (Update 07)

## State Machine

Idle
→ Preparing
→ Starting
→ Running
→ Stopping
→ Cleanup
→ Idle

Failure paths:

Preparing → Error
Starting → Error
Running → Recovering → Running
Running → Error

No transition may skip Cleanup after a normal stop.
