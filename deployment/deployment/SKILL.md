# Deployment Skill

## Purpose

Deploy applications safely and verify that the deployed system actually works.

Deployment is an external side effect and should be treated as a production operation rather than simply running a command.

---

## When to Use

Use this skill when:

- Deploying an application
- Updating a deployment
- Configuring hosting
- Creating production builds
- Configuring environment variables
- Setting domains
- Modifying deployment infrastructure
- Investigating failed deployments
- Verifying a deployed application

Platform-specific skills such as Vercel, Cloudflare, and Cloud Run should supplement this skill when available.

---

## Pre-Deployment Inspection

Before deployment, identify:

- Framework
- Build command
- Start command where applicable
- Output directory
- Runtime version
- Environment variables
- Required services
- Database dependencies
- API dependencies
- Hosting platform
- Deployment configuration

---

## Pre-Deployment Checks

Run relevant checks such as:

- Tests
- Lint
- Type checks
- Production build
- Dependency checks

Do not deploy known-broken code merely because the deployment platform accepts it.

---

## Environment Variables

Confirm required configuration exists.

Separate:

- Public configuration
- Server-side configuration
- Secrets
- Environment-specific values

Never print secrets while verifying configuration.

---

## Deployment Safety

Before triggering deployment, understand:

- Which project will be deployed.
- Which branch/commit will be deployed.
- Which environment is targeted.
- Whether the operation changes production.
- Whether deployment can cause downtime.

Do not deploy an unintended branch or workspace.

---

## Build Reproducibility

Use the repository's declared dependencies and configuration.

Avoid relying on:

- Untracked local files
- Local machine state
- Undeclared global packages
- Manual modifications outside the repository

A deployment should be reproducible from the project state.

---

## Deployment Failure

When a deployment fails:

1. Capture the error.
2. Determine whether failure occurred during build, upload, startup, configuration, or runtime.
3. Inspect relevant logs.
4. Fix the root issue.
5. Redeploy only when safe.
6. Verify the new deployment.

Do not repeatedly redeploy without understanding the failure.

---

## Post-Deployment Verification

Deployment success is not equivalent to application success.

Verify:

- Deployment status
- Application URL
- Main page
- Important routes
- API behavior
- Authentication where applicable
- Critical workflows
- Console/runtime errors where observable

Use browser-based verification when available.

---

## Rollback

When a deployment causes a serious regression and rollback is supported:

- Identify the known-good release.
- Confirm rollback target.
- Execute rollback safely.
- Verify the restored deployment.
- Investigate the original failure afterward.

Do not casually delete production resources as a rollback strategy.

---

## Deployment URLs

Only report a deployment URL that was actually returned or verified.

Never fabricate a URL.

If a deployment tool returns no URL, state that the deployment result did not provide a shareable URL.

---

## Completion Criteria

A deployment is complete when:

- The intended project/version was deployed.
- Required configuration was available.
- Deployment completed successfully.
- The resulting application was verified where possible.
- Critical failures are known and reported.
- The reported deployment URL is genuine and verified.