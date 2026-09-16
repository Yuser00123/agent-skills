# Agent Skills Index

> **Purpose:** Skill routing and selection guide for the autonomous software engineering agent.

This file is the entry point to the skill library.

The agent should read this file before performing a non-trivial task, identify the skills relevant to the task, and then read only the necessary `SKILL.md` files.

---

# 1. How to Use This Index

## Mandatory Skill Loading Workflow

Before starting a significant task:

1. Understand the user's request.
2. Inspect the repository when repository access is available.
3. Read this `INDEX.md`.
4. Identify the task category.
5. Select the minimum relevant skills.
6. Read the selected `SKILL.md` files.
7. Execute the task according to those skills.
8. Verify the result.
9. Run additional skills when the task changes scope.

Do **not** read every skill file for every task.

Only load skills relevant to the current task.

---

# 2. Skill Selection Principles

## Principle 1 — Use the Minimum Sufficient Set

Do not load ten skills when three are sufficient.

Example:

```text
Fix a typo
→ Code Search
→ Coding
→ Completion Verification
```

---

## Principle 2 — High-Risk Work Gets More Skills

Tasks involving:

- Security
- Authentication
- Secrets
- Production
- Deployment
- Databases
- External side effects
- Destructive operations

should load additional relevant skills.

---

## Principle 3 — Skills Compose

Skills are not mutually exclusive.

A single task may require several skills.

Example:

```text
"Add Google authentication and deploy the application"

Planning
+
Repo Analysis
+
Code Search
+
Coding
+
Security
+
Secure Coding
+
Secrets Management
+
Testing
+
Build Verification
+
Deployment
+
Platform Skill
+
Completion Verification
```

---

## Principle 4 — Specialized Skills Supplement General Skills

Platform-specific skills do not replace general engineering skills.

For example:

```text
Vercel
    supplements
Deployment + Secrets Management + Build Verification
```

Similarly:

```text
GitHub
    supplements
Git Workflow
```

and:

```text
Code Documentation
    supplements
Documentation
```

---

## Principle 5 — Verification Is Mandatory

A task should not be reported as complete only because code was generated.

Relevant verification skills should be selected whenever implementation occurs.

At minimum, consider:

```text
Testing
Build Verification
Self Review
Completion Verification
```

---

# 3. Priority System

Each skill has an approximate priority.

### P0 — Mandatory Core

Load for most substantial software-engineering tasks.

```text
Repo Analysis
Planning
Coding
Self Review
Completion Verification
```

### P1 — Strongly Recommended

Load when relevant to the task.

```text
Code Search
Debugging
Testing
Build Verification
Safe Command Execution
Git Workflow
Tool Selection
Context Management
Error Recovery
Change Impact Analysis
```

### P2 — Specialized

Load when the task enters the corresponding domain.

```text
Frontend Development
UI/UX
Accessibility
Browser Research
Browser Automation
API Integration
Security
Secure Coding
Performance
Code Quality
Linting
Dependency Management
Deployment
Documentation
```

### P3 — Platform-Specific

Load when the task explicitly involves the platform.

```text
GitHub
Vercel
Cloudflare
Cloud Run
Code Documentation
```

---

# 4. Core Engineering Skills

## 4.1 Repo Analysis

**Path**

```text
core/repo-analysis/SKILL.md
```

**Purpose**

Understand the repository before making changes.

**Use when**

- Starting work in an existing repository
- Adding features
- Debugging
- Refactoring
- Changing architecture
- Deploying an unfamiliar project

**Triggers**

```text
analyze repository
understand codebase
inspect project
existing project
where should I change
how does this work
```

**Usually combine with**

```text
Code Search
Planning
Change Impact Analysis
```

---

## 4.2 Code Search

**Path**

```text
core/code-search/SKILL.md
```

**Purpose**

Find relevant symbols, references, configuration, tests, and execution paths.

**Use when**

- Locating functionality
- Tracing bugs
- Finding callers
- Understanding dependencies
- Searching large repositories

**Triggers**

```text
find
locate
search code
where is
references
usages
implementation
```

**Usually combine with**

```text
Repo Analysis
Coding
Debugging
Change Impact Analysis
```

---

## 4.3 Coding

**Path**

```text
core/coding/SKILL.md
```

**Purpose**

Implement features, fixes, refactors, and other code changes.

**Use when**

- Writing code
- Editing code
- Implementing functionality
- Refactoring
- Fixing implementation issues

**Triggers**

```text
build
implement
add feature
modify
change
create
refactor
fix code
```

**Usually combine with**

```text
Planning
Code Search
Testing
Build Verification
Self Review
Completion Verification
```

---

## 4.4 Debugging

**Path**

```text
core/debugging/SKILL.md
```

**Purpose**

Systematically reproduce, isolate, diagnose, and fix failures.

**Use when**

- Errors occur
- Tests fail
- Builds fail
- Runtime behavior is incorrect
- APIs malfunction

**Triggers**

```text
bug
error
broken
not working
fails
crash
exception
debug
```

**Usually combine with**

```text
Code Search
Testing
Build Verification
Error Recovery
```

---

## 4.5 Testing

**Path**

```text
core/testing/SKILL.md
```

**Purpose**

Verify expected behavior and prevent regressions.

**Use when**

- Implementing functionality
- Fixing bugs
- Refactoring
- Preparing releases

**Triggers**

```text
test
tests
coverage
regression
verify behavior
```

**Usually combine with**

```text
Coding
Debugging
Frontend Testing
Build Verification
Completion Verification
```

---

## 4.6 Build Verification

**Path**

```text
core/build-verification/SKILL.md
```

**Purpose**

Verify that the project actually builds successfully.

**Use when**

- Code changes are made
- Dependencies change
- Configuration changes
- Preparing deployment

**Triggers**

```text
build
compile
production build
typecheck
bundle
build failure
```

**Usually combine with**

```text
Testing
Linting
Dependency Management
Deployment
Completion Verification
```

---

## 4.7 Self Review

**Path**

```text
core/self-review/SKILL.md
```

**Purpose**

Perform a final critical review before reporting success.

**Use when**

- Significant changes are complete
- Multiple files changed
- Before commit
- Before deployment

**Triggers**

```text
review
check my changes
audit changes
final review
ready to ship
```

**Usually combine with**

```text
Security
Code Quality
Testing
Build Verification
Completion Verification
```

---

## 4.8 Completion Verification

**Path**

```text
core/completion-verification/SKILL.md
```

**Purpose**

Act as the final evidence-based gate before declaring a task complete.

**Use when**

- Finishing any non-trivial task
- Reporting deployment success
- Completing a fix
- Completing automated work

**Triggers**

```text
done
complete
finished
verify
ready
completion
```

**Rule**

This is one of the most important skills in the entire library.

The agent must distinguish:

```text
implemented
```

from:

```text
verified
```

---

## 4.9 Safe Command Execution

**Path**

```text
core/safe-command-execution/SKILL.md
```

**Purpose**

Execute shell commands while controlling security, scope, destructive effects, paths, inputs, and resource usage.

**Use when**

- Running shell commands
- Installing dependencies
- Executing generated code
- Using Git commands
- Running deployment commands

**Triggers**

```text
run command
shell
terminal
npm
pnpm
git
execute
install
```

**Important**

This skill governs agent behavior, but actual tool enforcement must still happen inside the orchestrator/tool layer.

---

# 5. Frontend Skills

## 5.1 Frontend Development

**Path**

```text
frontend/frontend-development/SKILL.md
```

**Use when**

- Creating pages
- Building components
- Changing layouts
- React/Next.js/Vue/Angular/Svelte/frontend work

**Triggers**

```text
frontend
component
page
React
Next.js
Vue
Angular
Svelte
HTML
CSS
responsive
```

**Usually combine with**

```text
UI/UX
Accessibility
Frontend Testing
Performance
```

---

## 5.2 UI/UX

**Path**

```text
frontend/ui-ux/SKILL.md
```

**Use when**

- Designing interfaces
- Improving visual hierarchy
- Creating dashboards
- Creating landing pages
- Styling interfaces

**Triggers**

```text
UI
UX
design
layout
style
dashboard
landing page
visual
animation
```

**Usually combine with**

```text
Frontend Development
Accessibility
Performance
```

---

## 5.3 Accessibility

**Path**

```text
frontend/accessibility/SKILL.md
```

**Use when**

- Building interactive interfaces
- Creating forms
- Implementing navigation
- Reviewing accessibility

**Triggers**

```text
accessibility
a11y
keyboard
screen reader
ARIA
focus
contrast
semantic HTML
```

**Usually combine with**

```text
Frontend Development
UI/UX
Frontend Testing
```

---

## 5.4 Frontend Testing

**Path**

```text
frontend/frontend-testing/SKILL.md
```

**Use when**

- Testing components
- Testing user flows
- Testing browser behavior
- Regression testing frontend features

**Triggers**

```text
component test
frontend test
UI test
browser test
E2E
Playwright
Cypress
```

**Usually combine with**

```text
Frontend Development
Testing
Browser Automation
Accessibility
```

---

# 6. Web Skills

## 6.1 Browser Research

**Path**

```text
web/browser-research/SKILL.md
```

**Use when**

- Researching current information
- Reading documentation
- Investigating APIs
- Investigating errors
- Comparing technologies

**Triggers**

```text
search web
research
documentation
latest
current
API docs
find information
```

**Usually combine with**

```text
Planning
API Integration
Browser Automation
```

---

## 6.2 Browser Automation

**Path**

```text
web/browser-automation/SKILL.md
```

**Use when**

- Interacting with websites
- Testing deployed applications
- Filling forms
- Clicking UI controls
- Taking screenshots
- Verifying web workflows

**Triggers**

```text
open website
click
fill form
browser
screenshot
navigate
web automation
test website
```

**Usually combine with**

```text
Browser Research
Frontend Testing
Deployment
Completion Verification
```

---

## 6.3 API Integration

**Path**

```text
web/api-integration/SKILL.md
```

**Use when**

- Integrating REST APIs
- Integrating GraphQL
- Adding SDKs
- Handling webhooks
- Connecting frontend/backend services

**Triggers**

```text
API
REST
GraphQL
SDK
webhook
endpoint
HTTP
integration
```

**Usually combine with**

```text
Security
Secrets Management
Testing
Frontend Development
```

---

# 7. Security Skills

## 7.1 Security

**Path**

```text
security/security/SKILL.md
```

**Use when**

- Handling user input
- Authentication
- Authorization
- APIs
- Shell commands
- Files
- Production systems
- Security reviews

**Triggers**

```text
security
authentication
authorization
vulnerability
attack
permission
secure
security audit
```

**Usually combine with**

```text
Secure Coding
Secrets Management
Safe Command Execution
Dependency Management
```

---

## 7.2 Secure Coding

**Path**

```text
security/secure-coding/SKILL.md
```

**Use when**

- Writing security-sensitive code
- Handling untrusted input
- Database operations
- File uploads
- Authentication/session logic
- Cryptography

**Triggers**

```text
secure code
SQL
injection
XSS
CSRF
upload
crypto
authentication
session
```

**Usually combine with**

```text
Security
Testing
Code Quality
```

---

## 7.3 Secrets Management

**Path**

```text
security/secrets-management/SKILL.md
```

**Use when**

- API keys
- Environment variables
- Tokens
- Passwords
- Cloud credentials
- Deployment secrets

**Triggers**

```text
API key
token
secret
password
.env
environment variable
credential
```

**Usually combine with**

```text
Security
Deployment
GitHub
Vercel
Cloudflare
Cloud Run
```

---

# 8. Quality Skills

## 8.1 Performance

**Path**

```text
quality/performance/SKILL.md
```

**Use when**

- Application is slow
- Bundle size is large
- Memory/CPU usage is high
- API responses are slow
- Rendering is inefficient

**Triggers**

```text
performance
slow
optimize
latency
bundle size
memory
CPU
rendering
```

**Usually combine with**

```text
Frontend Development
Code Quality
Testing
```

---

## 8.2 Code Quality

**Path**

```text
quality/code-quality/SKILL.md
```

**Use when**

- Refactoring
- Reviewing code
- Improving maintainability
- Cleaning architecture

**Triggers**

```text
code quality
clean code
refactor
maintainability
readability
technical debt
```

**Usually combine with**

```text
Coding
Self Review
Testing
Linting
```

---

## 8.3 Linting

**Path**

```text
quality/linting/SKILL.md
```

**Use when**

- Running linters
- Formatting code
- Type checking
- Static analysis

**Triggers**

```text
lint
ESLint
Prettier
format
typecheck
static analysis
```

**Usually combine with**

```text
Code Quality
Build Verification
Testing
```

---

## 8.4 Dependency Management

**Path**

```text
quality/dependency-management/SKILL.md
```

**Use when**

- Adding packages
- Removing packages
- Updating versions
- Resolving dependency conflicts
- Auditing dependencies

**Triggers**

```text
dependency
package
npm
pnpm
yarn
bun
upgrade
update package
package conflict
```

**Usually combine with**

```text
Security
Build Verification
Testing
```

---

# 9. Deployment Skills

## 9.1 Generic Deployment

**Path**

```text
deployment/deployment/SKILL.md
```

**Use when**

- Deploying applications
- Preparing production builds
- Configuring hosting
- Verifying deployments

**Triggers**

```text
deploy
deployment
production
hosting
release
publish
```

**Usually combine with**

```text
Build Verification
Testing
Security
Secrets Management
Platform-specific deployment skill
```

---

## 9.2 Vercel

**Path**

```text
deployment/vercel/SKILL.md
```

**Use when**

```text
Vercel
vercel.json
preview deployment
production deployment
Vercel environment variables
Vercel domain
```

**Load with**

```text
Deployment
Build Verification
Secrets Management
```

---

## 9.3 Cloudflare

**Path**

```text
deployment/cloudflare/SKILL.md
```

**Use when**

```text
Cloudflare
Workers
Wrangler
Pages
KV
R2
D1
Durable Objects
```

**Load with**

```text
Deployment
Security
Secrets Management
```

---

## 9.4 Cloud Run

**Path**

```text
deployment/cloud-run/SKILL.md
```

**Use when**

```text
Cloud Run
Google Cloud Run
container deployment
revision
traffic
GCP
```

**Load with**

```text
Deployment
Build Verification
Security
Secrets Management
```

---

# 10. Git and GitHub Skills

## 10.1 Git Workflow

**Path**

```text
git/git-workflow/SKILL.md
```

**Use when**

- Committing
- Branching
- Merging
- Reviewing diffs
- Pushing changes
- Managing repository history

**Triggers**

```text
git
commit
branch
merge
rebase
push
pull
diff
```

**Usually combine with**

```text
Self Review
Security
GitHub
```

---

## 10.2 GitHub

**Path**

```text
git/github/SKILL.md
```

**Use when**

- GitHub repositories
- Pull requests
- GitHub Actions
- GitHub releases
- Remote branches
- GitHub API
- Repository configuration

**Triggers**

```text
GitHub
repository
pull request
PR
Actions
workflow
release
GitHub API
```

**Usually combine with**

```text
Git Workflow
Secrets Management
Security
Documentation
```

---

# 11. Documentation Skills

## 11.1 Documentation

**Path**

```text
documentation/documentation/SKILL.md
```

**Use when**

- Writing README files
- Setup documentation
- Architecture docs
- API docs
- Deployment documentation
- Configuration documentation

**Triggers**

```text
documentation
README
docs
setup guide
architecture
API documentation
```

**Usually combine with**

```text
Code Documentation
Deployment
GitHub
```

---

## 11.2 Code Documentation

**Path**

```text
documentation/code-documentation/SKILL.md
```

**Use when**

- Adding code comments
- Documenting functions/classes
- Documenting public APIs
- Recording non-obvious implementation decisions

**Triggers**

```text
comment
JSDoc
code documentation
document function
document class
explain code
```

**Usually combine with**

```text
Code Quality
Documentation
Coding
```

---

# 12. Autonomous Agent Skills

These skills govern how the agent operates rather than what programming language or platform it uses.

---

## 12.1 Planning

**Path**

```text
agent/planning/SKILL.md
```

**Use when**

- Starting significant work
- Multiple steps are required
- Requirements are unclear
- Several files/systems are involved

**Triggers**

```text
plan
planning
implement feature
complex task
multiple steps
```

**Priority**

```text
P0
```

---

## 12.2 Tool Selection

**Path**

```text
agent/tool-selection/SKILL.md
```

**Use when**

- Multiple tools could solve a task
- Choosing between read/write/browser/command/deployment tools

**Triggers**

```text
which tool
choose tool
tool
automation
```

**Priority**

```text
P1
```

---

## 12.3 Context Management

**Path**

```text
agent/context-management/SKILL.md
```

**Use when**

- Long-running tasks
- Many files
- Many tool calls
- Provider fallback
- Large amounts of information

**Triggers**

```text
context
long task
history
state
remember
summarize
```

**Priority**

```text
P1
```

---

## 12.4 Error Recovery

**Path**

```text
agent/error-recovery/SKILL.md
```

**Use when**

- A tool fails
- Builds fail
- Deployments fail
- An API fails
- An assumption becomes invalid

**Triggers**

```text
failure
failed
retry
recover
error recovery
fallback
```

**Priority**

```text
P1
```

---

## 12.5 Change Impact Analysis

**Path**

```text
agent/change-impact-analysis/SKILL.md
```

**Use when**

- Modifying shared code
- Changing architecture
- Changing APIs
- Changing configuration
- Making high-risk changes

**Triggers**

```text
impact
dependencies
breaking change
architecture
shared code
```

**Priority**

```text
P1
```

---

## 12.6 Workspace / Snapshot Management

**Path**

```text
agent/workspace-management/SKILL.md
```

**Use when**

- Major refactoring
- Risky automated changes
- Snapshotting workspace
- Recovery
- Long-running work

**Triggers**

```text
snapshot
workspace
restore
backup
checkpoint
recovery
```

**Priority**

```text
P1/P2
```

---

## 12.7 Autonomous Decision Making

**Path**

```text
agent/autonomous-decision-making/SKILL.md
```

**Use when**

- The agent must choose between multiple valid approaches
- The agent is operating without continuous user input
- Risk must be evaluated before acting

**Triggers**

```text
autonomous
agent decide
choose approach
make decision
```

**Priority**

```text
P1
```

---

# 13. Skill Chains

The following chains are recommended combinations.

## New Feature

```text
Planning
→ Repo Analysis
→ Code Search
→ Coding
→ Testing
→ Build Verification
→ Self Review
→ Completion Verification
```

---

## Bug Fix

```text
Planning
→ Repo Analysis
→ Code Search
→ Debugging
→ Coding
→ Testing
→ Build Verification
→ Self Review
→ Completion Verification
```

---

## Frontend Feature

```text
Planning
→ Repo Analysis
→ Frontend Development
→ UI/UX
→ Accessibility
→ Coding
→ Frontend Testing
→ Performance
→ Build Verification
→ Self Review
→ Completion Verification
```

---

## API Integration

```text
Planning
→ Repo Analysis
→ API Integration
→ Security
→ Secrets Management
→ Coding
→ Testing
→ Build Verification
→ Self Review
→ Completion Verification
```

---

## Dependency Update

```text
Planning
→ Repo Analysis
→ Dependency Management
→ Security
→ Coding
→ Testing
→ Build Verification
→ Self Review
→ Completion Verification
```

---

## Production Deployment

```text
Planning
→ Repo Analysis
→ Testing
→ Linting
→ Build Verification
→ Security
→ Secrets Management
→ Deployment
→ Platform Skill
→ Browser Automation
→ Completion Verification
```

---

## GitHub Release

```text
Repo Analysis
→ Git Workflow
→ Self Review
→ Security
→ GitHub
→ Completion Verification
```

---

## Frontend Deployment

```text
Repo Analysis
→ Frontend Development
→ Accessibility
→ Frontend Testing
→ Performance
→ Linting
→ Build Verification
→ Security
→ Secrets Management
→ Deployment
→ Platform Skill
→ Browser Automation
→ Completion Verification
```

---

## Major Refactor

```text
Planning
→ Repo Analysis
→ Code Search
→ Change Impact Analysis
→ Workspace/Snapshot Management
→ Coding
→ Testing
→ Build Verification
→ Code Quality
→ Self Review
→ Completion Verification
```

---

## Security-Sensitive Change

```text
Planning
→ Repo Analysis
→ Code Search
→ Security
→ Secure Coding
→ Secrets Management
→ Change Impact Analysis
→ Coding
→ Testing
→ Self Review
→ Completion Verification
```

---

# 14. Platform Routing

When the platform appears in the task, load the corresponding platform skill.

| Detected Platform | Skill |
|---|---|
| GitHub | `git/github/SKILL.md` |
| Vercel | `deployment/vercel/SKILL.md` |
| Cloudflare | `deployment/cloudflare/SKILL.md` |
| Cloud Run | `deployment/cloud-run/SKILL.md` |

Platform skills should normally be combined with their general parent skill.

Example:

```text
"Deploy this Next.js app to Vercel"

Deployment
+
Vercel
+
Build Verification
+
Secrets Management
+
Completion Verification
```

---

# 15. Frontend Routing

| Task | Primary Skills |
|---|---|
| New page | Frontend Development, UI/UX |
| New component | Frontend Development |
| Visual redesign | UI/UX, Frontend Development |
| Accessibility fix | Accessibility, Frontend Development |
| Frontend bug | Frontend Development, Debugging, Frontend Testing |
| Browser UI testing | Frontend Testing, Browser Automation |
| Slow page | Performance, Frontend Development |
| API-driven page | Frontend Development, API Integration |

---

# 16. Security Routing

| Situation | Skills |
|---|---|
| User input | Security, Secure Coding |
| API key | Secrets Management, Security |
| Authentication | Security, Secure Coding |
| Shell command | Safe Command Execution, Security |
| File access | Security, Secure Coding |
| Dependency vulnerability | Security, Dependency Management |
| Deployment secrets | Secrets Management, Deployment |
| GitHub Actions secret | Secrets Management, GitHub |
| Public API | Security, API Integration |

---

# 17. Risk-Based Skill Expansion

Start with the minimum required skills.

Then expand the skill set when risk increases.

### Low Risk

Example:

```text
Rename a variable
```

Load:

```text
Code Search
Coding
Completion Verification
```

---

### Medium Risk

Example:

```text
Refactor authentication middleware
```

Load:

```text
Planning
Repo Analysis
Code Search
Change Impact Analysis
Security
Secure Coding
Coding
Testing
Self Review
Completion Verification
```

---

### High Risk

Example:

```text
Modify production deployment configuration
```

Load:

```text
Planning
Repo Analysis
Change Impact Analysis
Security
Secrets Management
Deployment
Platform Skill
Build Verification
Testing
Self Review
Completion Verification
```

---

# 18. Skill Loading Rules

## Rule 1

Never assume a skill was followed merely because it exists.

The agent must actually read the relevant `SKILL.md`.

---

## Rule 2

Do not load irrelevant skills.

For example:

```text
Fix Python algorithm bug
```

does not require:

```text
Vercel
Cloudflare
UI/UX
Browser Automation
```

unless the task expands into those areas.

---

## Rule 3

Load dependent skills when required.

Example:

```text
Vercel deployment
```

should normally include:

```text
Deployment
Build Verification
Secrets Management
Vercel
Completion Verification
```

---

## Rule 4

Do not duplicate instructions unnecessarily.

A specialized skill should contain platform/domain-specific instructions.

General principles should remain in the general skills.

---

## Rule 5

Higher-risk operations require stronger verification.

The more dangerous the action, the more evidence the agent should require.

---

# 19. Dynamic Skill Selection

The agent should classify the task before selecting skills.

Use the following conceptual pipeline:

```text
USER REQUEST
     │
     ▼
TASK CLASSIFICATION
     │
     ├── Coding?
     ├── Frontend?
     ├── Browser?
     ├── API?
     ├── Security?
     ├── Dependency?
     ├── Git/GitHub?
     ├── Deployment?
     └── Documentation?
     │
     ▼
RISK ASSESSMENT
     │
     ├── Low
     ├── Medium
     └── High
     │
     ▼
SKILL SELECTION
     │
     ▼
READ SKILL FILES
     │
     ▼
EXECUTE
     │
     ▼
VERIFY
     │
     ▼
COMPLETION VERIFICATION
```

---

# 20. Keyword Routing Map

The following keywords should strongly influence skill selection.

```text
auth
→ Security
→ Secure Coding

token
→ Secrets Management

API
→ API Integration

browser
→ Browser Automation
→ Browser Research

React
→ Frontend Development

UI
→ UI/UX

accessibility
→ Accessibility

test
→ Testing
→ Frontend Testing when applicable

build
→ Build Verification

lint
→ Linting

package
→ Dependency Management

slow
→ Performance

deploy
→ Deployment
→ relevant platform skill

Git
→ Git Workflow

GitHub
→ GitHub

README
→ Documentation

comment
→ Code Documentation

refactor
→ Planning
→ Change Impact Analysis
→ Code Quality

error
→ Debugging
→ Error Recovery

snapshot
→ Workspace/Snapshot Management
```

---

# 21. Never-Do Rules

The presence of a skill does not grant permission to perform an action.

Skills provide **behavioral guidance**.

Tools must enforce actual permissions and security boundaries.

The agent must never assume that:

```text
skill available
=
permission available
```

For example:

```text
Security skill
≠
permission to access production

GitHub skill
≠
permission to delete repositories

Deployment skill
≠
permission to deploy anything

Browser skill
≠
permission to bypass authentication
```

Tool-level authorization remains authoritative.

---

# 22. Final Verification Rule

Before reporting task completion, the agent should ask:

```text
1. Did I satisfy the user's actual request?
2. Did I modify the intended files?
3. Did I preserve unrelated user changes?
4. Did relevant tests run?
5. Did the build/checks run where appropriate?
6. Did I verify the actual result?
7. Did I introduce a security issue?
8. Did I leave placeholders or unfinished work?
9. Did an external side effect actually succeed?
10. Can I provide evidence for my completion claim?
```

If the answer to an important verification question is unknown, the agent must report that uncertainty rather than inventing success.

---

# 23. Skill Library Map

```text
agent-skills/
│
├── INDEX.md
│
├── core/
│   ├── repo-analysis/
│   ├── code-search/
│   ├── coding/
│   ├── debugging/
│   ├── testing/
│   ├── build-verification/
│   ├── self-review/
│   ├── completion-verification/
│   └── safe-command-execution/
│
├── frontend/
│   ├── frontend-development/
│   ├── ui-ux/
│   ├── accessibility/
│   └── frontend-testing/
│
├── web/
│   ├── browser-research/
│   ├── browser-automation/
│   └── api-integration/
│
├── security/
│   ├── security/
│   ├── secure-coding/
│   └── secrets-management/
│
├── quality/
│   ├── performance/
│   ├── code-quality/
│   ├── linting/
│   └── dependency-management/
│
├── deployment/
│   ├── deployment/
│   ├── vercel/
│   ├── cloudflare/
│   └── cloud-run/
│
├── git/
│   ├── git-workflow/
│   └── github/
│
├── documentation/
│   ├── documentation/
│   └── code-documentation/
│
└── agent/
    ├── planning/
    ├── tool-selection/
    ├── context-management/
    ├── error-recovery/
    ├── change-impact-analysis/
    ├── workspace-management/
    └── autonomous-decision-making/
```

---

# 24. Final Principle

The skill library should make the agent behave like an experienced engineer:

```text
UNDERSTAND
   ↓
PLAN
   ↓
SELECT SKILLS
   ↓
INSPECT
   ↓
ACT
   ↓
TEST
   ↓
VERIFY
   ↓
REVIEW
   ↓
REPORT
```

The agent should not optimize for:

```text
"finish quickly"
```

It should optimize for:

```text
"complete the requested task correctly,
safely, and with evidence."
```

---

# Version

```text
Skill Library Index: v1.0
Skills: 38
Primary routing file: INDEX.md
```