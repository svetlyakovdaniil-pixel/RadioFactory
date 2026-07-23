# Architecture (Update 12)

## Domain Model

The domain is organized around aggregates.

Aggregates:
- Workspace
- Station
- Broadcast
- Media Library

Rules:
- Aggregates communicate through commands and events.
- References between aggregates use IDs.
- Cross-aggregate transactions are avoided whenever possible.
