# Architecture (Update 07)

## Domain Commands

All changes enter the system as commands.

Examples:
- StartStation
- StopStation
- ForceStopStation
- RestartStation
- ImportMedia
- ValidateLibrary
- StartRecovery

Rules:
- Commands are immutable.
- Commands have unique IDs.
- Commands produce events but never modify UI directly.
