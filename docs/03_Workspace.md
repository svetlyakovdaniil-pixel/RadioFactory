# Workspace (Update 06)

## Domain Model

Workspace is the root aggregate.

It owns:
- Stations
- global configuration
- shared media libraries
- scheduler
- recovery queue

Workspace never owns runtime state of individual Broadcasts.

## Identity Rules

Workspace ID is immutable.
Station IDs are unique within a Workspace.
