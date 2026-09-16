# Git Workflow Skill

## Purpose

This skill defines how the agent should safely work with Git during software development.

Git should provide traceability and reversible change history without destroying the user's existing work.

---

## When to Use This Skill

Use this skill when:

- Beginning work on a Git repository.
- Creating or reviewing changes.
- Preparing commits.
- Creating branches.
- Inspecting repository state.
- Recovering from changes.
- Preparing code for collaboration or deployment.

---

## Core Principle

**Git is a safety and history mechanism, not a reason to destroy workspace state.**

Never use destructive Git commands simply for convenience.

---

## Initial Git Inspection

Before significant work, inspect:

```text
git status
git branch
```

and when relevant:

```text
git diff
git log
```

Determine:

- current branch
- modified files
- staged files
- untracked files
- repository cleanliness
- recent relevant history

---

## Existing User Changes

Pre-existing changes belong to the user unless there is evidence otherwise.

Do not:

```text
git reset --hard
git checkout -- .
git clean -fd
```

just to obtain a clean workspace.

Preserve existing modifications.

---

## First Commit Check

Before creating the first commit for a project, inspect the repository's Git workflow guidance if available.

Check for:

```text
/home/user/skills/git-workflow.md
```

or the current equivalent skill documentation.

Ensure a suitable `.gitignore` exists before committing.

---

## `.gitignore`

Before committing, ensure that sensitive/generated material is excluded as appropriate.

Common examples include:

```text
node_modules/
.env
.env.*
dist/
build/
coverage/
.next/
logs/
temporary files
```

Do not blindly add patterns that would hide legitimate source files.

Inspect existing `.gitignore` before modifying it.

---

## Staging Changes

Stage intentionally.

Before staging, inspect:

```text
git status
git diff
```

Do not use broad staging commands when unrelated user changes may exist.

Prefer staging the files belonging to the task.

---

## Commit Scope

A commit should represent a coherent change.

Avoid mixing:

```text
feature
+
unrelated refactor
+
formatting entire repository
+
temporary debugging
```

in the same commit unless the task genuinely requires all of them.

---

## Commit Message

Use a clear message describing the change.

Examples:

```text
fix: handle missing session token
feat: add project settings page
test: add authentication regression coverage
refactor: simplify API client error handling
```

Choose the project's existing convention when one exists.

---

## Before Commit

Run an appropriate verification sequence:

```text
git diff
tests
build
self-review
git status
```

Do not commit obviously broken code merely because the task deadline is near.

---

## Secret Check

Before committing, inspect the diff for:

- API keys
- access tokens
- passwords
- private keys
- `.env` contents
- credentials
- generated secret files

Never commit secrets.

---

## Generated Files

Determine whether generated output is intentionally tracked.

Do not commit:

```text
build artifacts
temporary files
cache files
coverage output
```

unless the project explicitly tracks them.

---

## Lockfiles

Do not modify lockfiles manually unless necessary.

Use the project's package manager to update them.

Unexpected lockfile changes should be reviewed before commit.

---

## Branching

Use the repository's existing branch strategy when known.

When creating a branch:

- use a meaningful name
- avoid ambiguous names
- do not delete another branch without authorization

Example:

```text
feature/project-settings
fix/auth-session
chore/update-dependencies
```

---

## Merging and Rebasing

Treat history-changing operations carefully.

Before:

```text
rebase
merge
reset
cherry-pick
```

understand the current branch state and potential user changes.

Do not rewrite shared history without appropriate authorization.

---

## Git Diff Review

After implementation, inspect:

```text
git diff
```

Look for:

- unintended files
- accidental deletions
- secret values
- debug code
- huge formatting changes
- incorrect imports
- temporary changes

---

## Git Status After Commit

After committing, check:

```text
git status
```

Confirm what remains modified/untracked.

A clean status is not mandatory if unrelated user changes existed.

---

## Git Push

Pushing is an external side effect.

Before pushing:

- verify the branch
- inspect commits
- verify remote
- ensure secrets are absent
- ensure tests/build are appropriately validated

Never push unrelated user work accidentally.

---

## Remote Configuration

Inspect the configured remote when necessary.

Do not assume that the repository's remote belongs to the expected destination.

Before pushing important changes, verify the remote.

---

## GitHub Interaction

When GitHub tools are available, prefer dedicated structured tools for GitHub operations when appropriate.

Do not build unsafe shell commands from uncontrolled repository/user input.

---

## Recovery

If an agent makes an unwanted Git change:

1. determine exactly what changed
2. protect user-owned modifications
3. use the least destructive recovery method
4. verify restored state

Do not blindly reset the entire repository.

---

## Commit Completion Criteria

Before considering Git workflow complete:

- intended changes are present
- unrelated changes are preserved
- `.gitignore` is appropriate
- no secrets are staged
- tests/build checks are appropriate
- diff has been reviewed
- commit message is accurate
- branch/remote are understood if pushing

---

## Final Rule

**Never sacrifice user work for a cleaner Git state. Preserve, inspect, verify, then commit deliberately.**