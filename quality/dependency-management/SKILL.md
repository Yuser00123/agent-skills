# Dependency Management Skill

## Purpose

Add, remove, update, and audit dependencies safely while minimizing unnecessary project complexity and supply-chain risk.

---

## When to Use

Use this skill when:

- Installing a package
- Updating a dependency
- Removing a package
- Changing package versions
- Fixing dependency conflicts
- Auditing vulnerabilities
- Modifying lockfiles
- Upgrading frameworks

---

## Before Adding a Dependency

Ask:

- Is the dependency actually necessary?
- Can existing project code solve the problem?
- Does the project already use an equivalent library?
- Is the package maintained?
- Is it compatible with the current runtime?
- Does it introduce significant bundle or infrastructure cost?
- Does it create security concerns?

Do not add dependencies simply for convenience.

---

## Package Manager

Identify and use the project's existing package manager.

Examples include:

- npm
- pnpm
- yarn
- bun
- pip
- Poetry
- Cargo

Do not casually switch package managers.

---

## Version Management

Respect:

- Existing version strategy
- Lockfiles
- Framework compatibility
- Runtime requirements
- Peer dependencies

Do not make unnecessary major-version upgrades during unrelated work.

---

## Lockfiles

Treat lockfiles as important source-controlled artifacts.

When dependencies change:

- Update the lockfile using the package manager.
- Review unexpected changes.
- Avoid manually editing generated dependency resolution.

---

## Dependency Conflicts

When conflicts occur:

1. Identify the conflicting packages.
2. Inspect version constraints.
3. Check framework/runtime compatibility.
4. Determine whether an upgrade or downgrade is appropriate.
5. Test after resolving the conflict.

Do not use `--force` or equivalent bypasses as the default solution.

---

## Security

Consider:

- Known vulnerabilities
- Suspicious packages
- Abandoned dependencies
- Unexpected install scripts
- Transitive dependencies

Use available package-manager auditing tools when appropriate.

Do not blindly upgrade everything to eliminate a warning.

---

## Dependency Removal

Before removing a dependency:

- Search all references.
- Check configuration.
- Check scripts.
- Check generated artifacts.
- Run tests/build afterward.

---

## Framework Upgrades

Framework upgrades may require:

- Migration guides
- Configuration changes
- API changes
- Dependency updates
- Runtime changes
- Test updates

Do not assume a version number change is sufficient.

---

## Completion Criteria

Dependency work is complete when:

- The dependency change is necessary and justified.
- Compatible versions are selected.
- Lockfiles are correctly updated.
- Security implications are considered.
- Relevant tests/build/type checks pass.
- Unrelated dependencies were not unnecessarily changed.