# Architecture (Update)

## Responsibility Boundaries

Workspace
- global coordination
- resource limits
- recovery queue

YouTube Channel
- YouTube integration
- publication defaults

Station
- business logic
- media selection
- runtime state
- lifecycle

Broadcast
- one LIVE session

Worker
- executes commands

Dashboard
- visualizes state
- never talks directly to FFmpeg

## Forbidden Dependencies

Dashboard -> FFmpeg
Station -> another Station runtime
Worker -> UI
Broadcast -> Workspace configuration
