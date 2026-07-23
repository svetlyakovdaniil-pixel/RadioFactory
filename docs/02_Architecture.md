# Architecture (Update 10)

## API Contract Principles

All communication between components occurs through explicit contracts.

Rules:
- Every request has a correlation ID.
- Every response references the originating request.
- APIs are versioned.
- Unknown fields must be ignored for forward compatibility.
- Breaking changes require a new API version.
