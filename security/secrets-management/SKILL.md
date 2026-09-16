# Secrets Management Skill

## Purpose

Prevent credentials, tokens, API keys, private keys, passwords, and other sensitive configuration from being exposed or mishandled.

---

## When to Use

Use this skill when:

- Adding API integrations
- Configuring authentication
- Deploying applications
- Creating environment variables
- Working with cloud providers
- Using GitHub tokens
- Using database credentials
- Debugging authentication
- Reviewing repositories
- Creating CI/CD workflows

---

## What Counts as a Secret

Treat the following as potentially sensitive:

- API keys
- Access tokens
- Refresh tokens
- Passwords
- Database credentials
- Private keys
- Service-account credentials
- Cloud credentials
- Encryption keys
- Webhook secrets
- Session secrets
- Signing keys

When uncertain, treat a credential-like value as secret.

---

## Never Commit Secrets

Never intentionally place secrets in:

- Source files
- Git history
- Public repositories
- Client-side bundles
- Documentation
- Screenshots
- Logs
- Error messages
- Example configuration with real credentials

Use placeholders in documentation.

---

## Environment Configuration

Use environment configuration for runtime secrets where appropriate.

Examples:

```text
API_KEY
DATABASE_URL
GITHUB_TOKEN
AUTH_SECRET
```

Never assume an environment variable is secret simply because it has an environment-variable name.

Frontend variables explicitly exposed to browsers are public.

---

## Local Development

Use the project's established local secret mechanism.

Common examples include:

- `.env`
- `.env.local`
- Secret managers
- Platform environment configuration

Ensure secret files are ignored by Git where appropriate.

---

## Git Safety

Before committing:

- Inspect staged files.
- Check for credentials.
- Check configuration files.
- Check generated files.
- Check logs and dumps.
- Check accidentally copied tokens.

If secret scanning is available, use it.

---

## Exposure Response

If a secret is discovered in tracked code:

1. Stop treating the repository as safe.
2. Identify where it was exposed.
3. Avoid spreading the secret further.
4. Rotate/revoke the credential when appropriate.
5. Remove it from active source.
6. Assess Git history exposure.
7. Update secure configuration.
8. Verify the application still works.

Removing a secret from the latest file does not necessarily remove it from Git history.

---

## Tool and Agent Behavior

Never place secrets into:

- Prompt text unnecessarily
- Search queries
- Browser URLs
- Public logs
- Generated screenshots
- Tool outputs
- Commit messages

When tools require authentication, use secure environment or connector mechanisms.

---

## Secret Detection

Look for patterns involving:

- Token prefixes
- Private-key headers
- Password assignments
- API key variables
- Connection strings
- Authorization headers

Do not rely exclusively on regex detection; inspect context.

---

## Least Privilege

Use the smallest permission scope required for each credential.

Prefer:

- Read-only tokens for read-only tasks
- Repository-scoped credentials instead of account-wide credentials
- Short-lived credentials where supported
- Separate credentials for separate environments

---

## Deployment

Production secrets should be configured through the deployment platform's secure configuration mechanism.

Do not hardcode them into deployment scripts or container images.

---

## Completion Criteria

Secrets management is complete when:

- No known secret is unnecessarily stored in source.
- Sensitive values are configured through an appropriate secure mechanism.
- Git tracking is checked.
- Required credentials have minimal practical privileges.
- Logs and outputs do not expose secrets.
- Any discovered exposed credential has an appropriate remediation path.