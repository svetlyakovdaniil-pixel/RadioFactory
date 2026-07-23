# Architecture (Update 11)

## Extension Model

External integrations must communicate through provider interfaces.

Core domain must never depend on a specific provider implementation.

### Provider Categories

- Streaming Provider
- Video Platform Provider
- Notification Provider
- Media Provider
- Authentication Provider

Providers are replaceable without changing the domain model.
