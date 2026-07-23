# 02_Component_Catalog

## Overview

This document describes the major runtime components of RadioFactory and their responsibilities.

## Dashboard

Purpose:
- Single operational interface.

Responsibilities:
- Channel management
- Library management
- Configuration
- Monitoring
- Manual operations
- System status

Inputs:
- User actions
- Backend API responses

Outputs:
- API requests
- Configuration changes

## Backend

Purpose:
Central orchestration layer.

Responsibilities:
- Business logic
- Authentication
- Configuration
- Persistent state
- API endpoints
- Worker coordination

## Live Worker

Purpose:
Operate continuous YouTube broadcasts.

Responsibilities:
- Restore previous state
- Create or resume broadcasts
- Select media
- Launch FFmpeg
- Monitor stream
- Recover after failures
- Rotate tracks

## Scheduler

Purpose:
Execute delayed and periodic jobs.

Responsibilities:
- Planned tasks
- Retry scheduling
- Recovery scheduling

## Media Library

Stores:
- audio tracks
- loop videos
- thumbnails
- metadata

Each channel owns an isolated operational library.

## Telegram Integration

Purpose:
Operational notifications.

Examples:
- stream started
- stream stopped
- failures
- recovery events

## YouTube Integration

Responsibilities:
- broadcast lifecycle
- stream binding
- metadata
- monitoring

## FFmpeg

Responsibilities:
- encode
- multiplex
- publish RTMP
- reconnect

## Relationships

Dashboard
    ↓
Backend
    ↓
Workers
    ↓
FFmpeg
    ↓
YouTube

Workers also communicate with:
- Media Library
- Scheduler
- Telegram

## Notes

Each component owns a clearly defined responsibility and communicates through explicit interfaces.
