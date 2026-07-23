# Dashboard (Update 04)

## Real-time Behaviour

Dashboard displays only confirmed backend state.

Optimistic UI must never claim that a Station is running before Backend confirms it.

## Command Feedback

Each command has four visible phases:

- Accepted
- Executing
- Completed
- Failed

The interface must never leave a command indefinitely in an ambiguous loading state.
