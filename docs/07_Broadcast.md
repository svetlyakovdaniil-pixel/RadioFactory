# Broadcast Addendum

## Broadcast Invariants

- immutable Pending LIVE Package
- exactly one active Broadcast per Station
- recovery <3 minutes keeps Broadcast identity
- recovery >=3 minutes creates a new Broadcast

## Sequence

Prepare
-> Create LIVE
-> Stream
-> Finish
-> Cleanup
-> Prepare next
