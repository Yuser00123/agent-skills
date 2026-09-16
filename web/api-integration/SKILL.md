# API Integration Skill

## Purpose

Integrate frontend and backend applications with APIs safely, predictably, and maintainably.

This skill covers REST APIs, GraphQL, SDKs, webhooks, and other HTTP-based integrations.

---

## When to Use

Use this skill when:

- Connecting a frontend to an API
- Adding a new API endpoint
- Integrating an external service
- Adding authentication
- Handling API errors
- Implementing webhooks
- Replacing an API provider
- Debugging API communication
- Adding API clients or SDKs

---

## Before Integration

Determine:

- API base URL
- Authentication mechanism
- Request format
- Response format
- Required headers
- Error format
- Rate limits
- Timeout behavior
- Environment configuration
- Version requirements

Read official API documentation when available.

---

## Architecture

Avoid scattering raw API requests throughout UI components.

Prefer a clear API boundary such as:

- API client
- Service layer
- Repository layer
- Typed client
- Framework data-fetching layer

Follow the project's existing architecture.

Do not introduce unnecessary abstraction for a tiny integration.

---

## Configuration

Environment-specific values should use environment configuration.

Examples:

- API base URL
- Public configuration
- Server-side credentials

Never place private secrets in client-side bundles.

Remember that frontend environment variables marked public are not secret.

---

## Request Handling

Handle:

- Loading
- Success
- Empty response
- Validation errors
- Authentication errors
- Authorization errors
- Rate limiting
- Server errors
- Network errors
- Timeout
- Malformed responses

Do not assume HTTP success means the returned data has the expected structure.

---

## Validation

Validate external data at appropriate boundaries.

Do not blindly trust API responses.

Check:

- Required fields
- Types
- Nullable values
- Arrays/objects
- Enum-like values
- Unexpected structures

Use the project's existing validation/type system where available.

---

## Authentication

Protect credentials.

Do not:

- Hardcode API keys
- Commit secrets
- Log authorization headers
- Return private credentials to browsers
- Store sensitive tokens in unsafe client-side locations

Use server-side proxying when a secret must remain private.

---

## Retries

Retries should be deliberate.

Consider retrying transient failures such as:

- Temporary network failures
- Certain server errors
- Rate limits when a retry-after mechanism exists

Avoid retrying:

- Invalid authentication
- Validation failures
- Permanent client errors
- Non-idempotent operations without safeguards

Repeated retries can duplicate side effects.

---

## Timeouts

Every external request should have reasonable timeout behavior where the platform allows it.

Never allow an unavailable external service to block the application indefinitely.

---

## Rate Limits

Respect provider limits.

Use:

- Backoff
- Retry-after information
- Request deduplication
- Caching where appropriate
- Batching where supported

Do not attempt to bypass provider rate limits.

---

## Error Translation

Convert low-level API failures into useful application-level errors.

Users should receive understandable feedback without exposing:

- Stack traces
- Secrets
- Internal infrastructure
- Sensitive provider details

Logs may contain additional diagnostic information only when safe.

---

## Webhooks

For webhook integrations:

- Verify authenticity/signatures where supported.
- Validate payloads.
- Handle duplicate delivery.
- Make processing idempotent where possible.
- Return appropriate responses.
- Avoid trusting arbitrary webhook payloads.

---

## Testing

Test:

- Successful response
- Empty response
- Invalid response
- Network failure
- Timeout
- Authentication failure
- Rate limiting
- Server error
- Unexpected payload

Mock external services when appropriate.

---

## Verification

After integration:

1. Test the API boundary.
2. Test the consuming UI/backend behavior.
3. Check error handling.
4. Verify environment configuration.
5. Confirm secrets are not exposed.
6. Run relevant tests.
7. Run build/type checks where available.

---

## Completion Criteria

An API integration is complete when:

- The correct API contract is implemented.
- Authentication is handled securely.
- External data is validated appropriately.
- Failure states are handled.
- Retries/timeouts are appropriate.
- Secrets are protected.
- Tests cover important behavior.
- The application builds successfully when applicable.
- Actual integration behavior has been verified where possible.