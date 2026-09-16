# Cloudflare Skill

## Purpose

Work safely with Cloudflare Workers, Pages, Wrangler, deployments, environments, bindings, and related configuration.

This skill supplements generic Deployment, Security, API Integration, and Secrets Management skills.

---

## When to Use

Use this skill when:

- Deploying Cloudflare Workers
- Working with Wrangler
- Configuring Workers environments
- Managing bindings
- Managing Worker secrets
- Configuring Pages or related Cloudflare deployment workflows
- Debugging Worker deployments
- Inspecting versions
- Managing traffic deployments

---

## Before Working

Determine:

- Worker/project name
- Account
- Environment
- Wrangler configuration
- Runtime compatibility
- Bindings
- Variables
- Secrets
- Build command
- Deployment command

Verify that the account and project are the intended targets.

---

## Wrangler

Inspect the existing Wrangler configuration before modifying it.

Look for:

- Worker name
- Compatibility settings
- Environment configuration
- Variables
- Secrets references
- Bindings
- Build settings

Do not regenerate or replace configuration blindly.

---

## Environments

Cloudflare Workers supports separate environments through Wrangler configuration. Environment-specific configuration can represent a distinct deployed Worker environment.

Keep:

- Development
- Staging
- Production

configuration clearly separated.

Do not accidentally deploy development configuration as production configuration.

---

## Variables and Secrets

Cloudflare distinguishes regular environment variables from encrypted secrets.

Plaintext variables should not be used for sensitive information; secrets should be used for sensitive values.

Never:

- Put API tokens into `[vars]`
- Commit `.env` or `.dev.vars` files containing secrets
- Print secret values
- Store secrets in client-side assets

---

## Bindings

When working with bindings, determine the resource type and environment.

Examples may include:

- KV
- R2
- D1
- Durable Objects
- Service bindings
- Environment variables
- Secrets

Verify that the binding name used in code matches deployment configuration.

---

## Deployment Model

Cloudflare Workers separates versions from deployments.

A version represents a captured state of code/configuration, while a deployment determines which version serves traffic. Cloudflare can also support traffic splits between versions in applicable deployment workflows.

Use this distinction when diagnosing deployment problems.

---

## Deployment Workflow

Recommended sequence:

1. Inspect configuration.
2. Verify environment.
3. Run local checks.
4. Build if required.
5. Deploy.
6. Capture deployment result.
7. Verify Worker/version.
8. Test actual behavior.

---

## Local Development

Use the project's existing local development configuration.

Do not assume local environment variables match production.

When working with `.env` or `.dev.vars`, ensure sensitive files remain outside source control. Cloudflare documents environment-specific configuration and recommends keeping local secret files out of Git.

---

## Deployment Failures

Classify failures such as:

- Wrangler configuration
- Authentication
- Account/project mismatch
- Build
- Binding configuration
- Runtime
- Resource limits
- Environment mismatch

Inspect actual deployment output before changing configuration.

---

## Runtime Debugging

When a deployed Worker fails:

- Check request behavior.
- Inspect available logs.
- Verify environment variables/bindings.
- Verify compatibility settings.
- Compare deployed version with expected code.

Do not assume local success means deployed success.

---

## Traffic and Versions

When using gradual or multi-version deployment capabilities:

- Identify the exact version.
- Confirm intended traffic allocation.
- Monitor behavior.
- Restore previous configuration/version when necessary.

Do not modify production traffic casually.

---

## Completion Criteria

Cloudflare work is complete when:

- Correct account/project/environment was targeted.
- Configuration is understood.
- Secrets are protected.
- Bindings are valid.
- Deployment succeeded.
- Resulting version/deployment was identified.
- Runtime behavior was verified where possible.