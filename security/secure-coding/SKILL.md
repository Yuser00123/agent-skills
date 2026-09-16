# Secure Coding Skill

## Purpose

Apply secure implementation practices directly while writing and modifying code.

This skill complements the broader Security skill by focusing on implementation-level decisions.

---

## When to Use

Use this skill whenever writing or modifying code that:

- Processes external input
- Executes commands
- Accesses files
- Handles authentication
- Communicates over networks
- Uses databases
- Serializes data
- Processes uploaded files
- Handles sensitive information
- Creates APIs
- Uses third-party libraries

---

## Secure-by-Default Implementation

Prefer implementations that are safe without requiring every caller to remember additional security rules.

Examples:

- Validate inputs inside sensitive functions.
- Restrict filesystem access.
- Use parameterized database queries.
- Escape output appropriately.
- Use secure cookie settings where applicable.
- Use explicit authorization checks.

Do not rely solely on documentation telling future developers to "call this safely."

---

## Injection Prevention

Consider:

- SQL injection
- Command injection
- HTML injection
- JavaScript injection
- Template injection
- Header injection
- Path injection

Never concatenate untrusted input into an interpreted language or command when a structured alternative exists.

---

## Database Security

Prefer parameterized queries or the framework's safe query API.

Validate:

- IDs
- Filters
- Sort fields
- Pagination
- User-controlled query inputs

Do not construct arbitrary SQL from raw user input.

---

## Output Encoding

Encode data according to its output context.

Contexts include:

- HTML
- JavaScript
- URL
- CSS
- HTTP headers
- SQL

Do not assume that escaping appropriate for one context is safe for another.

---

## File Uploads

For uploaded files, consider:

- File size
- File type
- File extension
- Content validation
- Storage location
- File names
- Execution permissions
- Path traversal
- Malware scanning where appropriate

Never trust a filename or MIME type alone for sensitive processing.

---

## Authentication and Sessions

Use established libraries and protocols.

Consider:

- Session expiration
- Token validation
- Secure storage
- Cookie flags
- CSRF protections
- Password hashing
- Brute-force resistance

Never implement cryptographic primitives yourself.

---

## Cryptography

Use established cryptographic libraries.

Do not:

- Invent encryption algorithms
- Create custom password hashing
- Hardcode keys
- Reuse nonces improperly
- Roll your own authentication protocol

Use secure defaults provided by established libraries.

---

## Error Handling

Security-sensitive failures should fail closed where appropriate.

Do not convert security failures into successful behavior.

Avoid:

```text
authentication fails -> continue anyway
authorization fails -> return all data
validation fails -> process anyway
```

---

## Race Conditions

Consider concurrency around:

- File operations
- Authentication
- Resource creation
- Payments
- Permissions
- Deployment
- Token usage

Do not assume sequential execution when the system is concurrent.

Use appropriate locks, transactions, idempotency, or atomic operations when required.

---

## Safe Defaults

Prefer:

- Deny by default
- Minimal permissions
- Explicit allowed operations
- Explicit configuration
- Short-lived credentials where appropriate
- Restricted network access where practical

---

## Code Review Checklist

Before completion, inspect for:

- Injection
- Missing authorization
- Unsafe shell commands
- Unsafe filesystem access
- Secret exposure
- Unsafe deserialization
- Insecure redirects
- Weak validation
- Missing error handling
- Dangerous dependencies
- Debug configuration left enabled

---

## Completion Criteria

Secure coding is complete when the implementation follows the project's security requirements, sensitive boundaries are protected, unsafe input handling is addressed, and security-critical operations use established safe mechanisms.