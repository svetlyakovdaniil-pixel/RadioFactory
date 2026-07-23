# YouTube Provider Specification (Update 16B)

## 7. Broadcast Creation Workflow

1. Validate request.
2. Create YouTube Broadcast.
3. Create Stream.
4. Bind Stream.
5. Verify binding.
6. Return normalized identifiers.

Partial failures require compensating cleanup.

---

## 8. Resource Recovery

Provider restores existing resources using persisted identifiers.

Missing resources return domain-specific recovery errors.

Provider never silently creates replacements.

---

## 9. Error Normalization

All external errors are mapped into:

- AuthenticationError
- AuthorizationError
- QuotaError
- ValidationError
- NetworkError
- TemporaryProviderError
- PermanentProviderError

No Google-specific exceptions leave the Provider.

---

## 10. Retry Policy

Only transient failures are retried.

Retries use exponential backoff with jitter.

Permanent failures fail immediately.

---

## 11. Idempotency

Repeated Create, Bind and Complete requests must not create duplicate YouTube resources.

Operations are safe to repeat after process restart.

---

## 12. Adapter Requirements

The adapter encapsulates API version changes.

The domain contract remains stable even if the YouTube API changes.
