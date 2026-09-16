# GitHub Skill

## Purpose

Use GitHub safely and effectively for repository management, source control collaboration, automation, releases, and project operations.

This skill is specific to GitHub. General Git operations should follow the Git Workflow skill.

---

## When to Use

Use this skill when:

- Creating or inspecting GitHub repositories
- Cloning repositories
- Creating branches
- Committing and pushing changes
- Creating pull requests
- Reviewing pull requests
- Managing GitHub Actions
- Inspecting workflow runs
- Managing repository configuration
- Managing repository or environment secrets
- Creating releases or tags
- Checking repository status remotely
- Working with GitHub APIs

---

## Core Principle

GitHub is an external system.

Actions that modify GitHub are external side effects and must be performed deliberately.

Never assume a local Git operation automatically changes the remote repository.

---

## Before Working With a Repository

Inspect:

- Repository name
- Owner/organization
- Visibility
- Current branch
- Remote URL
- Local Git status
- Existing branches
- Recent commits
- Existing uncommitted changes

Confirm that the target repository is the intended one.

---

## Repository Discovery

Before making changes, determine:

- Repository identity
- Default branch
- Project structure
- Contribution conventions
- Existing CI/CD
- Existing issue/PR workflow
- Existing GitHub Actions
- Existing security configuration

Prefer repository-native conventions.

---

## Cloning

When cloning:

- Verify the repository URL.
- Use secure authentication mechanisms.
- Avoid embedding credentials in URLs when safer authentication is available.
- Clone into the intended workspace.
- Verify the resulting repository and branch.

Never print access tokens.

---

## Branching

For meaningful feature work:

1. Inspect current branch.
2. Determine whether a new branch is appropriate.
3. Create a descriptive branch.
4. Keep unrelated changes out of the branch.

Do not create excessive branches for trivial changes.

---

## Commits

Before committing:

- Inspect `git status`.
- Inspect the diff.
- Check for secrets.
- Check `.gitignore`.
- Verify tests/checks where appropriate.
- Stage intentionally.

Commits should represent coherent changes.

Avoid committing:

- API keys
- Credentials
- `.env` files containing secrets
- Build artifacts unless intentionally tracked
- Temporary debugging files
- User-generated unrelated files

---

## Pull Requests

When creating a pull request:

Include enough information to explain:

- What changed
- Why it changed
- How it was tested
- Important implementation details
- Known limitations

Do not claim tests passed unless they actually ran.

---

## GitHub Actions

When working with Actions:

Inspect:

- Workflow files
- Triggers
- Permissions
- Jobs
- Dependencies
- Environment usage
- Secrets
- Artifacts
- Deployment behavior

Prefer least-privilege workflow permissions.

Do not grant write permissions unnecessarily.

---

## Secrets

GitHub supports secrets at repository, organization, and environment scopes. Secrets are intended to prevent sensitive values from being stored directly in workflow source.

Never:

- Print secrets
- Commit secrets
- Put secrets into workflow source
- Put secrets into public issue/PR content
- Echo sensitive environment variables during debugging

When modifying workflows, confirm that secrets are actually required by the job.

---

## Workflow Debugging

When an Action fails:

1. Identify the failing workflow.
2. Identify the failing job.
3. Inspect the relevant step.
4. Check logs.
5. Determine whether failure is code, dependency, configuration, permission, or infrastructure related.
6. Fix the root cause.
7. Re-run only when justified.

Do not repeatedly re-run a broken workflow without investigating.

---

## Releases and Tags

Before creating a release/tag:

- Verify the target commit.
- Check version consistency.
- Ensure tests/build are appropriate.
- Confirm the release is intended.

Never tag the wrong commit because the local branch was misunderstood.

---

## GitHub API

When using GitHub APIs:

- Authenticate securely.
- Request minimum required permissions.
- Validate responses.
- Respect rate limits.
- Handle pagination.
- Handle errors.
- Do not expose tokens in logs.

---

## Remote State Verification

After operations such as:

- Push
- Pull request creation
- Branch creation
- Release creation
- Workflow dispatch

verify the remote result when possible.

Do not assume the operation succeeded simply because no immediate local exception occurred.

---

## Repository Safety

Never silently:

- Force-push
- Delete remote branches
- Rewrite shared history
- Delete repositories
- Close or merge pull requests
- Change repository visibility

These actions have significant external consequences.

---

## Completion Criteria

A GitHub task is complete when:

- The intended repository was modified.
- The intended branch/commit was used.
- Changes were verified.
- Remote state was checked where appropriate.
- Secrets were not exposed.
- GitHub Actions status is known where relevant.
- The final result accurately describes what actually happened.