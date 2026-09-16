# Cloud Run Skill

## Purpose

Build, deploy, operate, verify, and safely roll back containerized applications on Google Cloud Run.

This skill supplements generic Deployment, Security, Secrets Management, and Build Verification skills.

---

## When to Use

Use this skill when:

- Deploying to Cloud Run
- Creating Cloud Run services
- Updating services
- Managing revisions
- Configuring environment variables
- Configuring secrets
- Changing CPU/memory/concurrency
- Managing traffic
- Performing rollouts
- Rolling back deployments
- Debugging runtime failures

---

## Before Deployment

Determine:

- Google Cloud project
- Region
- Service name
- Container image
- Build process
- Runtime port
- Environment variables
- Secrets
- CPU/memory configuration
- Concurrency
- Minimum/maximum instances
- Authentication/ingress
- Expected traffic behavior

Do not deploy to an unknown project or service.

---

## Container Requirements

Verify:

- Container starts successfully.
- Application listens on the expected port.
- Required dependencies exist.
- Runtime configuration exists.
- Production startup command works.

Cloud Run deployment can create a new immutable revision whenever deployment/configuration changes.

---

## Revisions

Treat revisions as immutable deployment states.

A revision may represent:

- Container image
- Environment variables
- Resource configuration
- Request settings

Do not assume changing service configuration modifies an existing revision in place.

Cloud Run creates a new revision when service configuration changes.

---

## Environment Variables and Secrets

Keep configuration separate from source code.

Protect:

- API keys
- Tokens
- Database credentials
- Service credentials

Never bake secrets into container images.

---

## Resource Configuration

Consider:

- CPU
- Memory
- Request concurrency
- Minimum instances
- Maximum instances
- Startup behavior
- Request timeouts

Choose settings based on actual application requirements.

Do not increase resources blindly to hide application inefficiencies.

---

## Statelessness

Cloud Run can scale service instances automatically.

Do not depend on:

- Local instance memory as permanent storage
- Local filesystem as shared persistent storage
- In-memory maps being globally shared
- One instance handling every request

Use persistent external storage/services when state must survive instance replacement or scaling.

---

## Deployment

Recommended flow:

1. Inspect project/service.
2. Verify container.
3. Run tests.
4. Build container.
5. Deploy.
6. Identify revision.
7. Check deployment status.
8. Verify application.
9. Inspect runtime logs where relevant.

---

## Traffic Management

Cloud Run supports traffic assignment across revisions and can perform gradual rollouts or rollback to previous revisions.

Before changing traffic:

- Identify current serving revision.
- Identify target revision.
- Understand percentage changes.
- Confirm intended environment.

---

## Rollback

When a revision causes a regression:

1. Identify the failing revision.
2. Identify the last known-good revision.
3. Restore traffic safely.
4. Verify application behavior.
5. Preserve the failing revision for investigation.

Do not destroy useful diagnostic evidence unnecessarily.

---

## Debugging

Classify failures:

- Build
- Container startup
- Health/readiness
- Environment configuration
- IAM
- Network
- Application runtime
- Database/external service
- Resource exhaustion

Inspect logs before modifying multiple variables.

---

## IAM and Access

Apply least privilege.

Verify:

- Deployer identity
- Runtime service account
- Invoker permissions
- Secret access
- Registry access

Do not grant broad project-level permissions when narrower permissions are sufficient.

---

## Production Verification

After deployment verify:

- Service is healthy.
- Intended revision exists.
- Traffic reaches intended revision.
- Main endpoint works.
- Critical API functionality works.
- Environment configuration works.
- Logs do not show major runtime failures.

---

## Completion Criteria

Cloud Run work is complete when:

- Correct project/service/region was targeted.
- Container is deployable.
- Intended revision was created.
- Configuration is correct.
- Traffic points to the intended revision.
- Application behavior was verified.
- Rollback path remains available.
- No secrets were exposed.