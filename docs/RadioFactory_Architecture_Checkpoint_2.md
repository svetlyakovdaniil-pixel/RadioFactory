# RadioFactory Architecture

## Checkpoint 2 (Decisions 12--16)

### Decision 12 --- Music Engine

The Music Engine is independent from LIVE duration.

#### Playback cycle

-   Every cycle contains every track from the Station library exactly
    once.
-   Track order is randomized.
-   No repeats inside a cycle.
-   After a cycle finishes, a completely new random order is generated.

#### Library changes

If tracks are added, removed or otherwise changed during a cycle: - the
current cycle is **not** modified; - the cycle finishes normally; - the
next cycle is built from the updated library.

#### LIVE behavior

Each LIVE owns its own playback cycles.

When a new LIVE starts: - a completely new random cycle is generated; -
it never continues the unfinished cycle from the previous LIVE.

#### LIVE duration

Configured duration is the target duration.

The system starts the next track **only if it fits completely** into the
remaining time.

Rules: - never cut a track; - never stop a track early; - if the next
track does not fit, the LIVE ends after the current track finishes.

------------------------------------------------------------------------

### Decision 13 --- Random Resource Selection

Each LIVE randomly selects: - music cycle; - loop video; - thumbnail; -
title; - description.

Rules: - the same loop cannot be selected for two consecutive LIVEs if
alternatives exist; - the same thumbnail cannot be selected for two
consecutive LIVEs if alternatives exist; - the same title cannot be
selected for two consecutive LIVEs if alternatives exist; - the same
description cannot be selected for two consecutive LIVEs if alternatives
exist.

Each LIVE therefore has its own unique combination of resources.

------------------------------------------------------------------------

### Decision 14 --- Pending LIVE Package

Before creating a LIVE, RadioFactory prepares one immutable package
containing: - music queue; - selected loop; - selected thumbnail; -
selected title; - selected description.

If LIVE creation fails: - the package is reused; - resources are **not**
regenerated.

A new package is created only when: - the previous LIVE completed
successfully; - preparation was cancelled by the user; - required
resources changed and invalidate the prepared package.

------------------------------------------------------------------------

### Decision 15 --- Continuous Radio Mode

Stations always operate in continuous mode.

Lifecycle:

1.  LIVE starts.
2.  Broadcast runs.
3.  Broadcast finishes naturally.
4.  Cleanup.
5.  Prepare next LIVE.
6.  Start next LIVE.

There is no schedule-based waiting.

------------------------------------------------------------------------

### Decision 16 --- Waiting States

Missing required resources are not treated as errors.

Possible waiting states: - Waiting for Music - Waiting for Loop Video -
Waiting for Thumbnail - Waiting for Titles - Waiting for Descriptions

A Station automatically continues preparation once all required
resources become available.

Required resources: - at least one processed music track; - at least one
loop video; - at least one thumbnail; - at least one title; - at least
one description.
