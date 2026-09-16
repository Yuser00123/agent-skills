# Safe Command Execution Skill

## Purpose

This skill defines how the agent should use shell/command execution safely.

This skill is especially important for autonomous agents because command execution can modify files, consume resources, access networks, destroy data, or affect external systems.

The skill governs agent behavior; actual security boundaries must also be enforced by the orchestrator/tool implementation.

---

## When to Use This Skill

Use this skill whenever the agent intends to execute a shell command or system command.

---

## Core Principle

**Never execute a command merely because it is syntactically valid.**

Before execution, determine:

- what the command does
- what directory it affects
- what files it modifies
- whether it accesses the network
- whether it can destroy data
- whether it uses user-controlled input
- whether it affects external systems
- whether the command is necessary

---

## Workspace Boundary

The normal project workspace should be the default working directory.

Commands should operate inside the intended project directory unless there is an explicit, legitimate need to access another approved location.

The agent must not use arbitrary directories simply because they are technically accessible.

---

## Untrusted Inputs

Treat these as untrusted:

- user-provided command fragments
- model-generated paths
- model-generated URLs
- repository names
- branch names
- filenames
- environment-derived strings
- external data

Do not construct shell commands unsafely from untrusted strings.

---

## Prefer Structured Operations

When a direct tool exists, prefer it over shell commands.

For example:

Use file tools for:

```text
read_file
write_file
patch_file
list_files
```

instead of shell operations when the corresponding direct operation exists.

Use Git-specific tools when available instead of constructing complex Git shell commands unnecessarily.

---

## Shell Injection

Never embed arbitrary user/model-controlled values directly into a shell command.

Dangerous conceptual pattern:

```text
git clone https://host/<user-input>
```

constructed through unsafe string interpolation.

Prefer structured arguments or validated values.

If shell execution is unavoidable:

- strictly validate input
- use safe escaping/quoting
- restrict allowed characters
- avoid shell evaluation features when possible

---

## Dangerous Commands

Treat commands such as these as high risk:

```text
rm -rf
mkfs
dd
shutdown
reboot
kill
chmod -R
chown -R
git reset --hard
git clean -fd
git checkout -- .
```

Also treat recursive deletion, mass permission changes, and destructive database commands as high risk.

Do not execute destructive commands unless the task explicitly requires them, the scope is understood, and the operation is authorized by the agent's environment/policy.

---

## Git Destruction

Never run destructive Git cleanup merely to obtain a clean state.

Preserve user work.

Before destructive Git actions, determine:

- what would be lost
- whether changes are user-owned
- whether a backup exists
- whether the action is actually required

Prefer non-destructive alternatives.

---

## Network Commands

Before executing network-affecting commands, consider:

- destination
- authentication
- data being transmitted
- whether the request is necessary
- whether it could alter external state

A command such as:

```text
curl
wget
npm publish
git push
```

may affect systems outside the sandbox.

Do not treat all network commands as read-only.

---

## External Side Effects

Classify commands as:

### Read-only

Examples:

```text
ls
pwd
cat
git status
git diff
```

### Local mutation

Examples:

```text
npm install
build commands
file generation
database migrations
```

### External mutation

Examples:

```text
git push
deployment
publishing packages
remote database writes
```

External mutation requires greater caution and verification.

---

## Timeouts

Use reasonable command timeouts.

Do not create enormous timeouts by default.

For long-running commands:

- understand why they take time
- use the project's normal command
- monitor actual output where possible

A timeout does not automatically prove the command failed.

---

## Environment Variables

Never print secrets.

Avoid commands such as:

```text
env
printenv
cat .env
```

unless specifically necessary and the output can be handled safely.

Do not include API keys or tokens in logs, commits, tool output, or final responses.

---

## File Paths

Validate paths before using them.

Watch for:

```text
..
absolute paths
symlinks
unexpected mount points
```

The agent should not use path manipulation to escape its intended workspace.

The orchestrator/tool layer should enforce this independently of the skill.

---

## Package Installation

Before installing packages:

1. Determine package manager.
2. Confirm package necessity.
3. Use project-local installation.
4. Avoid arbitrary install scripts when unsafe or unexpected.
5. Verify resulting dependency changes.

Never install software merely to solve an unrelated problem.

---

## Code Execution

Executing generated code can have side effects.

Before running unfamiliar code, consider:

- filesystem access
- network access
- subprocess creation
- resource consumption
- secrets exposure

Use the sandbox as the security boundary where available.

---

## Database Commands

Treat database mutation as high risk.

Before running migrations or write operations:

- identify target database/environment
- confirm expected scope
- verify migration or command
- avoid production unless explicitly authorized
- prefer test/local databases during development

Never assume a database command is harmless because it was generated by another tool.

---

## Recovery From Failed Commands

When a command fails:

1. inspect actual error
2. identify whether anything changed
3. determine whether a partial side effect occurred
4. fix the underlying issue
5. retry only when justified

Do not blindly retry destructive commands.

---

## Command Verification

After a mutating command, verify the expected result.

Examples:

```text
mkdir → check directory
write → read file
git commit → inspect git status/log
build → inspect exit status/output
deploy → verify deployment
```

---

## Tool-Level Security

Skills are not a security boundary.

The orchestrator should independently enforce:

- workspace restrictions
- command validation
- timeouts
- path restrictions
- authentication
- rate limits
- environment isolation
- secret handling

The model must not be able to grant itself additional permissions simply by interpreting this skill differently.

---

## Final Rule

**Every command should be necessary, scoped, observable, and as non-destructive as practical.**