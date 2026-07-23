# Workspace (Update 09)

## Queue Rules

Workspace owns lifecycle queues.

Rules:
- FIFO by default.
- One active lifecycle command per Station.
- Failed commands never block unrelated Stations.
- Queue processing is deterministic.
