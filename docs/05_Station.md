# Station Addendum

## Station Invariants

A Station:

- never owns more than one active Broadcast;
- never starts a new Broadcast before Cleanup finishes;
- never loses manual stop intent after reboot;
- never shares runtime state with another Station.

## Responsibilities

Station decides WHAT should happen.

Worker decides HOW it is executed.

Dashboard decides HOW it is displayed.
