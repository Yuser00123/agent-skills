# Vercel Skill

## Purpose

Deploy and operate web applications on Vercel using safe, reproducible, and verifiable workflows.

This skill supplements the generic Deployment, Frontend Development, Security, and Secrets Management skills.

---

## When to Use

Use this skill when:

- Deploying to Vercel
- Creating or configuring a Vercel project
- Managing preview deployments
- Managing production deployments
- Configuring domains
- Configuring environment variables
- Debugging Vercel builds
- Inspecting deployment logs
- Verifying a deployed application

---

## Before Deployment

Inspect:

- Framework
- Package manager
- Build command
- Output configuration
- Repository connection
- Vercel project configuration
- Runtime requirements
- Environment variables
- Existing deployment settings

Do not overwrite existing deployment configuration without understanding it.

---

## Deployment Environments

Treat these environments separately:

- Development
- Preview
- Production

Vercel supports environment-specific variables, allowing configuration to differ by environment. Changes to environment variables require a new deployment to take effect.

Never assume a Preview configuration is identical to Production.

---

## Environment Variables

Before deployment identify:

- Required variables
- Public variables
- Server-side secrets
- Environment-specific values

Never place private credentials into frontend-exposed configuration.

When changing environment variables:

1. Identify target environment.
2. Change the intended variable.
3. Redeploy.
4. Verify behavior.

Do not print secret values during debugging.

---

## Project Linking

Before running platform commands, verify:

- Correct Vercel project
- Correct account/team
- Correct project directory

A command executed in the wrong project can modify an unrelated deployment.

---

## Preview Deployments

Use preview deployments to validate important changes before production where practical.

Check:

- Correct build
- Main routes
- API behavior
- Environment configuration
- Authentication
- Responsive UI
- Important user flows

---

## Production Deployment

Before production deployment:

- Run relevant tests.
- Run lint/type checks where applicable.
- Run the production build.
- Check secrets/configuration.
- Review Git state.
- Confirm intended branch/commit.

Do not deploy accidental local changes.

---

## Build Failures

Classify the failure:

- Dependency installation
- Build command
- Type checking
- Environment variable
- Framework configuration
- Runtime
- External service

Inspect the actual Vercel build logs.

Do not randomly change versions or configuration until the failure is understood.

---

## Domains

When working with domains:

- Verify the intended Vercel project.
- Verify the domain.
- Check DNS state.
- Check SSL/TLS status where applicable.
- Verify the resulting URL.

Never report a domain as successfully configured without evidence.

---

## Serverless / Runtime Constraints

When application behavior depends on runtime capabilities:

Consider:

- Execution time
- Memory
- Cold starts
- Request size
- Streaming behavior
- Node/runtime compatibility
- File-system limitations
- Network access

Do not assume a local development environment behaves identically to a Vercel runtime.

---

## Deployment Verification

After deployment:

1. Obtain the actual deployment result.
2. Verify deployment status.
3. Open the resulting URL.
4. Test important routes.
5. Test critical API interactions.
6. Inspect runtime/browser errors when possible.

Deployment status alone does not prove application correctness.

---

## Rollback / Recovery

When a deployment introduces a regression:

- Identify the known-good deployment.
- Confirm the rollback target.
- Restore safely using the platform-supported mechanism.
- Verify the restored application.

Do not delete deployment history as a substitute for rollback.

---

## Completion Criteria

A Vercel deployment is complete when:

- Correct project/environment was targeted.
- Build completed.
- Required environment configuration exists.
- Deployment result was observed.
- The deployed application was tested where possible.
- The final URL is genuine and verified.
- No secret was exposed.