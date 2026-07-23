# System Overview

## Purpose

RadioFactory is an automation platform for operating multiple 24/7 YouTube radio channels with minimal manual intervention.

The system coordinates media libraries, scheduling, stream creation, monitoring, recovery and operational control from a single interface.

---

## Core Goals

- Operate multiple independent channels.
- Automate repetitive workflows.
- Recover automatically from failures.
- Keep channel state persistent.
- Minimize operator actions.

---

## Main Components

### Dashboard

Central management interface.

Responsibilities:
- channel management
- library management
- monitoring
- configuration
- operations

---

### Backend

Coordinates business logic.

Responsibilities:
- API
- authentication
- orchestration
- persistence

---

### Workers

Long-running background processes.

Responsibilities:
- live broadcasting
- uploads
- scheduling
- maintenance
- monitoring

---

### Scheduler

Determines when work should start.

Supports:
- periodic jobs
- delayed execution
- recovery scheduling

---

### Media Library

Stores:
- audio
- loop videos
- thumbnails
- metadata

Each channel owns its own operational library while sharing common concepts.

---

### External Systems

RadioFactory integrates with:

- YouTube
- Telegram
- FFmpeg
- Local filesystem

---

## Design Philosophy

The operator should configure the platform once.

Normal operation should continue automatically without continuous supervision.

---

## Future Documents

This document is the entry point for the RadioFactory knowledge base.

Detailed documents will describe every component individually.
