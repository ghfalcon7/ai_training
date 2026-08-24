# Prompt Engineering for Developers

# Module 2: AI Developer Productivity Fundamentals

## Module purpose

This module teaches the fundamental working habits an individual developer needs to collaborate effectively with AI on a software task.

It focuses on the developer–AI interaction itself:

- How to frame work clearly
- How to provide the right information
- How to preserve project-specific guidance
- How to plan before changing code
- How to choose an appropriate model
- How to iterate toward a verified result

The module should remain independent of any specific coding harness, AI provider, programming language, or software-development lifecycle activity.

---

## Position within the overall agenda

Module 2 owns the foundational interaction model between a developer and an AI assistant.

It should not teach:

- Company policy, compliance, intellectual property, privacy, or governance, which belong in Module 1
- Harness commands, skills, agents, subagents, sessions, permissions, plugins, or Plan Mode, which belong in Module 3
- Detailed applications such as debugging, refactoring, testing, code review, or incident response, which belong in Module 4
- Multi-agent decomposition, parallel execution, approval checkpoints, workspace isolation, or validation-first architectures, which belong in Module 5
- MCP, retrieval systems, external integrations, or custom tools, which belong in Module 6
- Prompt injection, secrets management, generated-code security, and secure prompting, which belong in Module 7
- Team rollout, shared libraries, productivity metrics, and organizational playbooks, which belong in Module 8

Module 2 may use small coding examples, but only to demonstrate the fundamental workflow.

---

## Key distinctions within Module 2

### AI-assisted development workflow

Describes the complete interaction loop for one development task.

### Prompt engineering

Defines how the developer expresses the task, requirements, constraints, and expected response.

### Context engineering

Defines what information is made available to the model and how that information is selected, organized, and maintained.

### Repository instructions

Provide durable project-specific guidance that should apply across many tasks.

### Plan-first development

Defines how non-trivial work is investigated and sequenced before implementation begins.

### Model selection and cost optimization

Matches task difficulty and quality requirements to an appropriate model while controlling latency and total cost.

---

## Learning outcomes

By the end of this module, participants should be able to:

1. Structure an AI-assisted development task as an iterative workflow rather than a one-shot code-generation request.
2. Write a developer prompt with a clear objective, constraints, acceptance criteria, and expected output.
3. Distinguish prompt engineering from context engineering.
4. Assemble a compact, relevant context package for a coding task.
5. Create or improve an `AGENTS.md` file containing actionable repository guidance.
6. Decide when a task requires a written implementation plan.
7. Produce a grounded plan that names concrete files, symbols, milestones, and acceptance checks.
8. Select a model based on measured task requirements rather than habit or marketing claims.
9. Estimate the total cost of completing a task, including retries and human correction effort.
10. Recognize when a deterministic development tool is more appropriate than an AI model.

---

# Topic 2.1: AI-Assisted Development Workflow

## Objective

Teach developers a repeatable interaction loop for completing an individual software task with AI assistance.

The central idea is that productive AI-assisted development is not:

    Prompt → generated code → accept

It is an evidence-driven loop:

    Frame → orient → plan → act → inspect → refine → close

Current coding-agent guidance consistently emphasizes clear, well-scoped tasks, acceptance criteria, and relevant repository locations. [R1]

---

## The fundamental workflow

### Step 1: Frame the task

Describe the problem before asking for a solution.

The task definition should identify:

- The current behavior
- The desired behavior
- Why the change is needed
- What is inside the task scope
- What is outside the task scope
- Constraints that must remain true
- Observable acceptance criteria

Avoid beginning with an instruction such as:

    Fix the authentication code.

Prefer:

    Users with an expired session are redirected to the login page, but the
    original destination is lost. Preserve the requested URL and return the
    user to it after successful authentication.

### Step 2: Establish the current state

Before changing code, collect evidence about the existing behavior.

Depending on the task, this may include:

- A failing test
- A reproducible command
- A compiler error
- A stack trace
- Relevant log output
- A request and response example
- A screenshot or UI description
- The current output of the affected function

The purpose is to prevent the assistant from solving an assumed problem instead of the observed problem.

This module should introduce the idea of evidence, but formal validation-first development remains in Module 5.

### Step 3: Orient within the relevant code

Ask the assistant to identify the smallest relevant area of the repository.

A useful orientation request might be:

    Locate the request-authentication path for this behavior. Identify the
    entry point, the session validation function, related tests, and any
    redirect helper. Summarize the current flow before proposing changes.

Orientation for one task belongs here. Full codebase onboarding belongs in Module 4.

### Step 4: Select the appropriate planning depth

Not every task needs a formal plan.

Use:

- Direct execution for a mechanical, localized, low-risk edit
- A short written plan for a small multi-file change
- A detailed execution plan for cross-cutting or uncertain work

Plan-first development is covered in detail later in this module.

### Step 5: Make one coherent increment

Prefer a focused change that has one understandable purpose.

A coherent increment should:

- Address one behavior
- Touch only justified files
- Preserve unrelated behavior
- Include the smallest necessary supporting changes
- Avoid opportunistic cleanup unrelated to the task

This makes the result easier to inspect and makes failures easier to attribute.

### Step 6: Inspect the result

The developer should inspect:

- The changed files
- The complete diff
- New dependencies
- Public API changes
- Configuration changes
- Tests or checks performed
- Warnings, assumptions, and unresolved issues

The assistant should be asked to distinguish between:

- Checks it actually ran
- Checks it could not run
- Conclusions based on direct evidence
- Conclusions based only on code inspection

### Step 7: Refine and close

Corrections should target the specific failed dimension.

Examples:

- The implementation is correct, but it changes an unrelated public interface.
- The behavior works, but the test does not cover the failure path.
- The code follows the requirement, but not the repository convention.
- The solution is too broad; restrict it to the API package.

At completion, create a concise closing summary containing:

- What changed
- Why it changed
- Evidence of the result
- Important decisions
- Remaining limitations or risks

---

## Task brief template

    # Task

    ## Problem
    Describe the observed problem.

    ## Desired behavior
    Describe what should happen instead.

    ## Scope
    State what may be changed.

    ## Out of scope
    State what must not be changed.

    ## Constraints
    List compatibility, dependency, style, or behavior constraints.

    ## Relevant evidence
    Include errors, logs, examples, tests, or reproduction steps.

    ## Acceptance criteria
    State observable conditions that define success.

    ## Requested interaction
    Ask the assistant to inspect, explain, plan, implement, or review.

---

## Common workflow failures

- Asking for implementation before the assistant understands the existing behavior
- Assigning several unrelated changes in one request
- Providing a vague goal such as “clean up” or “improve”
- Accepting plausible-looking code without inspecting the diff
- Allowing unrelated refactoring to expand the task
- Treating generated tests as proof without running them
- Repeating the entire conversation instead of correcting the failed part
- Continuing a task after its assumptions have materially changed without updating the task definition

---

## Practical exercise

Give participants a deliberately vague issue:

    The export feature is broken. Fix it.

Ask them to transform it into:

1. A scoped task brief
2. A request for repository orientation
3. A short implementation plan
4. A request for a focused patch
5. A result-inspection checklist

The exercise evaluates workflow quality, not the export implementation itself.

---

## Overlap guardrail

Do not use this topic to teach:

- Detailed debugging methods
- Test-generation techniques
- Refactoring patterns
- Code-review techniques
- Agent orchestration
- Approval or permission systems
- Specific harness commands

Those subjects appear in later modules.

---

# Topic 2.2: Prompt Engineering for Developers

## Objective

Teach developers how to express a software task as a clear, testable contract with an AI assistant.

A strong developer prompt explains more than what code to write. It communicates what successful work means.

Current model guidance recommends separating instructions, examples, and contextual material, and defining success criteria before repeatedly tuning prompt wording. [R2]

---

## Anatomy of a strong developer prompt

### 1. Objective

State the outcome in direct language.

    Add case-insensitive email lookup to the existing user repository.

### 2. Current state

Explain what the system does now.

    `findByEmail` performs an exact comparison and therefore treats
    `User@example.com` and `user@example.com` as different values.

### 3. Desired behavior

Describe the externally observable result.

    Email lookup should be case-insensitive while preserving the original
    email value stored for display.

### 4. Relevant location

Name known paths, symbols, or modules.

    Start with `src/users/UserRepository.ts` and its tests in
    `tests/users/UserRepository.test.ts`.

Do not invent file locations when they are unknown. Ask the assistant to locate them.

### 5. Constraints

Examples include:

- Do not change the public method signature
- Do not add a new production dependency
- Preserve database portability
- Follow existing repository patterns
- Do not modify generated files
- Do not reformat unrelated code

### 6. Acceptance criteria

Acceptance criteria should describe observable behavior.

    - Lookup succeeds when letter casing differs.
    - The stored email value is not modified.
    - Existing lookup behavior continues to pass.
    - A regression test covers mixed-case input.

### 7. Expected response

State what the assistant should produce.

Examples:

- An explanation only
- A proposed plan
- A minimal patch
- A unified diff
- Tests plus implementation
- A review of an existing change
- A list of assumptions and missing information

### 8. Uncertainty protocol

Tell the assistant how to behave when information is missing.

    Do not invent repository conventions. Inspect the existing implementation
    and tests. Clearly label any remaining assumption.

---

## Recommended prompt structure

    # Objective

    <What outcome is required?>

    # Current behavior

    <What happens today?>

    # Desired behavior

    <What should happen after the change?>

    # Relevant context

    <Paths, symbols, versions, errors, examples, and prior decisions>

    # Constraints

    <What must remain unchanged?>

    # Acceptance criteria

    <How can success be observed?>

    # Requested response

    <Explanation, plan, patch, review, or another artifact>

    # Uncertainty handling

    <What should the assistant do when required information is missing?>

---

## Developer-specific prompting techniques

### Use concrete identifiers

Prefer:

    Update `calculateInvoiceTotal()` in `src/billing/invoice.ts`.

Over:

    Update the billing function.

### Include exact evidence

Provide the actual error, failing assertion, request payload, or command output rather than paraphrasing it.

### Separate instructions from reference material

Use headings, delimiters, or tags to distinguish:

- The task
- Repository rules
- Error output
- Code excerpts
- Examples
- Expected output

### Provide examples when the desired pattern is difficult to describe

A small number of representative examples is usually more useful than a long list of verbal exceptions.

Examples should cover genuinely different cases rather than repeating the same pattern.

### Include negative constraints selectively

Negative instructions are useful when they prevent a likely but undesirable change:

    Do not replace the repository's date library.

Avoid long lists of hypothetical prohibitions that are unrelated to the current task.

### Request concise rationale instead of hidden reasoning

Ask for:

- Assumptions
- Alternatives considered
- Decision rationale
- Evidence used
- Remaining uncertainty

Do not require private step-by-step reasoning.

### Use iterative correction

When the first result is partly correct, preserve what worked and correct only the failed dimension.

    Keep the implementation approach, but remove the new dependency and use
    the repository's existing parser.

---

## Prompt anti-patterns

- “Act as the world's best programmer” without substantive requirements
- Combining investigation, implementation, review, deployment, and documentation in one ambiguous request
- Supplying conflicting constraints
- Including large amounts of unrelated code
- Requesting “production-ready” code without defining production requirements
- Using “make it better” without a quality criterion
- Asking for a specific implementation before inspecting the repository
- Treating prompt length as a substitute for clarity
- Repeating failed prompts without changing the missing information

---

## Practical exercise

Participants receive:

- A bug report
- A relevant error message
- Two source files
- One irrelevant source file
- A short list of constraints

They must produce:

1. A weak one-sentence prompt
2. A structured developer prompt
3. A comparison explaining which ambiguities the structured prompt removes

---

## Overlap guardrail

Do not cover:

- Prompt injection
- Jailbreak resistance
- Secret leakage
- Secure system prompts
- Reusable harness commands
- Skills or agent definitions

Those belong in Modules 3 and 7.

---

# Topic 2.3: Context Engineering

## Objective

Teach developers to deliberately select and organize the information available to an AI assistant.

Prompt engineering asks:

    How should the request be written?

Context engineering asks:

    What information should the model have when processing the request?

Context should be treated as a finite attention resource. More context is not automatically better; the objective is the smallest sufficient collection of high-signal information. [R3]

---

## Context layers for a development task

### Stable repository context

Information that applies to many tasks:

- Project structure
- Supported languages and versions
- Build commands
- Test commands
- Coding conventions
- Generated-file rules
- Dependency policy
- Architectural boundaries

This context usually belongs in repository instruction files or canonical project documentation.

### Task context

Information specific to the current change:

- Problem statement
- Desired behavior
- Scope
- Constraints
- Acceptance criteria
- Business terminology

### Code context

The concrete implementation area:

- Entry points
- Relevant functions or classes
- Interfaces
- Callers and consumers
- Related tests
- Configuration
- Data models

### Runtime context

Evidence from the running system:

- Stack traces
- Logs
- Failed commands
- Test output
- HTTP requests and responses
- Performance measurements
- Environment-specific behavior

### Dependency and environment context

Examples:

- Runtime version
- Framework version
- Package manager
- Database engine
- Operating system
- Compiler options
- Feature flags

### Decision context

Important conclusions already reached:

- Rejected approaches
- Compatibility decisions
- Naming decisions
- Agreed constraints
- Known unresolved questions

---

## Context quality criteria

Before adding information, ask:

### Relevance

Does this information affect the current decision?

### Authority

Is it a canonical source, current source code, or direct runtime evidence?

### Freshness

Could it describe an older version of the system?

### Sufficiency

Does the assistant have enough information to avoid inventing missing details?

### Specificity

Does the context identify concrete files, symbols, commands, or behavior?

### Consistency

Does it conflict with another instruction or document?

### Economy

Can the same information be communicated with fewer, clearer tokens?

---

## Progressive disclosure

Do not begin by loading the entire repository.

Use a staged process:

### Stage 1: Map

Provide or request:

- A small directory tree
- Package or module names
- Likely entry points
- Relevant instruction files

### Stage 2: Focus

Open:

- The affected implementation
- Its direct interface
- Its closest tests
- Immediate callers or consumers

### Stage 3: Expand

Load additional files only when the first inspection reveals a dependency, shared abstraction, or cross-cutting effect.

### Stage 4: Add evidence

Include runtime evidence that confirms or contradicts the code-level hypothesis.

### Stage 5: Compact

Preserve decisions and important evidence while discarding:

- Repeated file contents
- Obsolete hypotheses
- Redundant command output
- Unrelated search results

This is context curation, not harness session management.

---

## Context package template

    # Task

    <Short statement of the required outcome>

    # Repository guidance

    <Applicable instruction-file paths and essential rules>

    # Relevant paths

    - <path>: <why it is relevant>
    - <path>: <why it is relevant>

    # Important symbols

    - <symbol>: <role in the behavior>
    - <symbol>: <role in the behavior>

    # Current behavior

    <Observed behavior>

    # Expected behavior

    <Desired behavior>

    # Runtime evidence

    <Errors, test failures, logs, or examples>

    # Environment

    <Relevant language, runtime, framework, or dependency versions>

    # Constraints

    <Boundaries that must be preserved>

    # Prior decisions

    <Decisions that should not be rediscovered>

    # Explicitly irrelevant

    <Files, systems, or approaches that should be ignored>

---

## Context anti-patterns

- Copying an entire repository into the conversation
- Including generated files when the source definition is available
- Providing stale logs without timestamps or version information
- Mixing evidence from different environments without labeling it
- Including several versions of the same file
- Supplying a code excerpt without its file path or surrounding interface
- Providing only implementation code while omitting tests and consumers
- Relying on an outdated architecture diagram over current code
- Keeping disproven hypotheses in active context
- Assuming the model remembers a decision from another session

---

## Practical exercise

Give participants a repository tree containing approximately 30 files and a narrowly scoped issue.

Ask them to select:

- The first five pieces of context they would provide
- The information they would initially omit
- The event that would justify loading each additional file
- A compact context package for the task

The quality criterion is relevance, not context volume.

---

## Overlap guardrail

Do not cover:

- Retrieval-augmented generation architecture
- Embeddings or vector databases
- MCP resources
- External knowledge integrations
- Multi-agent context isolation
- Harness session compaction commands

Those subjects belong in Modules 3, 5, and 6.

---

# Topic 2.4: Repository Instructions — AGENTS.md and Project Guidelines

## Objective

Teach developers to encode stable repository knowledge in a predictable, version-controlled form that AI coding assistants can consume.

`AGENTS.md` can be treated as a README for coding agents: it provides practical instructions that help an assistant understand how to build, test, and modify a repository. It uses standard Markdown and can be layered for different repository areas. [R4]

---

## What belongs in repository instructions

### Repository map

Provide a concise orientation:

- Main application directory
- Test locations
- Shared libraries
- Generated-code locations
- Documentation locations
- Important package boundaries

Do not reproduce the full repository tree.

### Setup commands

Document commands that actually work:

- Dependency installation
- Local development startup
- Database initialization
- Required code generation
- Environment preparation

### Build and validation commands

Include:

- Targeted test commands
- Full test command
- Lint command
- Type-check command
- Build command
- Formatting command, where applicable

Explain when each command should be used.

### Coding conventions

Document conventions that are not reliably discoverable from formatters or linters:

- Preferred architectural patterns
- Error-handling conventions
- Naming rules
- Public API expectations
- Test organization
- Logging conventions
- Location of shared abstractions

### Change boundaries

Examples:

- Do not edit generated files directly.
- Do not add a production dependency unless the task explicitly requires it.
- Keep package boundaries intact.
- Avoid changing public interfaces for internal fixes.
- Do not perform unrelated cleanup.

### Documentation expectations

State when a change requires:

- Public API documentation
- Migration notes
- Changelog entries
- Architecture documentation
- Example updates

---

## What should usually remain elsewhere

Repository instructions should point to canonical documentation rather than duplicate it completely.

Keep detailed material in the appropriate source:

- Architecture design in architecture documentation
- Product behavior in requirements or specifications
- Security policy in security documentation
- Contribution process in `CONTRIBUTING.md`
- API reference in generated or maintained API documentation

The instruction file should summarize the rule and identify the canonical path.

---

## Recommended layering model

### Root instruction file

Contains repository-wide guidance:

    /AGENTS.md

### Package or service instruction file

Contains rules that apply only to that subtree:

    /services/payments/AGENTS.md

### Task prompt

Contains temporary requirements for the current task.

A useful hierarchy is:

    Repository-wide rule
        ↓
    Subproject-specific rule
        ↓
    Current task instruction

The more specific rule should clarify or override the general rule where the selected tool supports hierarchical instructions.

---

## Example AGENTS.md

    # AGENTS.md

    ## Repository overview

    This repository contains a TypeScript API and a React web application.

    - `apps/api/`: API entry points and HTTP controllers
    - `apps/web/`: React application
    - `packages/domain/`: framework-independent business logic
    - `packages/testing/`: shared test utilities
    - `docs/`: architecture and operational documentation

    ## Setup

    - Install dependencies with `pnpm install`.
    - Start the API with `pnpm --filter api dev`.
    - Start the web application with `pnpm --filter web dev`.

    ## Working rules

    - Keep business logic in `packages/domain/`.
    - Controllers should translate HTTP input and output, not implement
      business rules.
    - Follow existing naming and error-handling patterns in the affected
      package.
    - Do not edit files under `generated/`.
    - Do not add a production dependency unless the task explicitly permits it.
    - Avoid formatting or refactoring unrelated files.

    ## Testing

    - Run package tests while developing:
      `pnpm --filter <package-name> test`
    - Run type checking after changing public types:
      `pnpm typecheck`
    - Before completion, run:
      `pnpm lint && pnpm test`

    ## Documentation

    - Update `docs/api/` when public API behavior changes.
    - Add migration notes when a change requires consumer action.

    ## Completion report

    State:

    - Files changed
    - Checks run
    - Checks not run
    - Public behavior changed
    - Remaining assumptions or limitations

---

## Instruction-writing principles

Good repository instructions are:

- Actionable
- Specific
- Testable
- Current
- Concise
- Scoped
- Written in direct language
- Stored in version control

Prefer:

    Run `pnpm --filter billing test` after changing the billing package.

Over:

    Ensure billing quality is maintained.

---

## Maintenance practices

- Review instruction changes like source-code changes.
- Update commands when the toolchain changes.
- Remove obsolete rules.
- Resolve contradictions between root and nested files.
- Periodically ask an assistant to summarize the instructions it loaded.
- Test commands copied into the file.
- Keep tool-neutral guidance in the shared file.
- Place tool-specific configuration in the corresponding tool configuration when necessary.

---

## Repository-instruction anti-patterns

- Copying the complete style guide into `AGENTS.md`
- Including commands that no longer work
- Writing aspirational principles without executable guidance
- Repeating the same rule in several files with different wording
- Combining repository rules with one temporary task
- Encoding rules already enforced reliably by automation unless explanation is necessary
- Using one root file for a monorepo whose packages have materially different workflows
- Treating generated instructions as correct without reviewing them

---

## Practical exercise

Provide participants with:

- A README
- A contribution guide
- Package scripts
- A repository tree
- Several unwritten conventions

Ask them to create a concise root `AGENTS.md`.

A second exercise asks them to add a nested instruction file for one package without duplicating the root file.

---

## Overlap guardrail

Do not cover:

- Harness skills
- Slash commands
- Plugins
- Organization-wide instruction libraries
- AI governance policy
- Security-specific instruction design

Those subjects belong in Modules 1, 3, 7, and 8.

---

# Topic 2.5: Plan-First Development

## Objective

Teach developers to investigate and describe a non-trivial change before asking an AI assistant to implement it.

This topic concerns planning as a development discipline. It does not teach the Plan Mode interface of any particular harness.

Current execution-plan guidance emphasizes plans that are self-contained, outcome-focused, kept current during implementation, and divided into independently verifiable milestones. [R5]

---

## When to use a plan

A written plan is valuable when:

- Several files or packages will change
- The task crosses architectural boundaries
- The repository area is unfamiliar
- Requirements contain ambiguity
- A public interface may change
- A migration or compatibility concern exists
- The implementation requires a new abstraction
- There are important technical unknowns
- Different approaches have meaningful trade-offs
- The work may continue across several work periods

---

## When not to over-plan

A detailed plan is usually unnecessary for:

- A spelling correction
- A localized configuration value change
- A mechanical rename supported by tooling
- A one-line test expectation update
- A well-understood single-file edit with obvious acceptance criteria

Planning has a cost. The planning depth should be proportional to uncertainty and scope.

---

## Planning-depth ladder

### Level 0: Direct execution

Use for a small, mechanical, reversible edit.

### Level 1: Short plan

Use a brief sequence of approximately three to seven steps.

Suitable for a known multi-file change.

### Level 2: Grounded implementation plan

Include:

- Current-state findings
- Affected files and symbols
- Proposed approach
- Alternatives
- Milestones
- Acceptance checks

### Level 3: Living execution plan

Use for substantial or uncertain work.

Maintain:

- Progress
- Discoveries
- Decisions
- Changes to the original approach
- Outcomes
- Remaining work

---

## Investigation before planning

A plan should be based on repository evidence rather than the issue description alone.

Before writing it, inspect:

- Repository instructions
- Existing implementation
- Related interfaces
- Closest tests
- Callers or consumers
- Similar patterns elsewhere in the repository
- Dependency and configuration constraints

A plan that invents the current architecture is not useful, even if it is detailed.

---

## Contents of a strong plan

### Goal and user-visible outcome

Explain what becomes possible after the change.

### Current state

Describe how the relevant code works today.

### Assumptions and unknowns

Separate verified facts from assumptions.

### Proposed approach

Explain the intended technical direction and why it fits the existing repository.

### Affected files and symbols

Name concrete paths, classes, functions, interfaces, or configuration keys.

### Sequence of work

Order changes so that each increment has a clear purpose.

### Milestones

Each milestone should state:

- What will exist afterward
- Which files or interfaces change
- How the milestone can be checked
- What evidence demonstrates completion

### Acceptance checks

Describe observable success rather than saying only “tests pass.”

### Decisions and discoveries

For longer tasks, record changes in direction and the evidence that caused them.

### Completion state

Define what “finished” means and what may remain outside the task.

---

## Plan template

    # Goal

    <Describe the behavior or capability delivered by this change.>

    # Current state

    <Summarize the relevant existing implementation.>

    # Scope

    <State what the plan changes.>

    # Out of scope

    <State what the plan deliberately excludes.>

    # Assumptions and unknowns

    - Verified:
    - Assumed:
    - Still unknown:

    # Proposed approach

    <Explain the selected approach and why it fits the repository.>

    # Affected areas

    - `<path or symbol>`: <planned change>
    - `<path or symbol>`: <planned change>

    # Milestones

    ## Milestone 1

    Outcome:
    Changes:
    Acceptance evidence:

    ## Milestone 2

    Outcome:
    Changes:
    Acceptance evidence:

    # Validation

    <Commands and observable behavior that demonstrate success.>

    # Decisions

    - Decision:
      Rationale:
      Evidence:

    # Remaining risks or limitations

    <Known gaps that are not silently ignored.>

---

## Plan review questions

Before approving a plan, ask:

1. Is the plan grounded in inspected repository evidence?
2. Does it describe an observable outcome?
3. Does it identify concrete files and symbols?
4. Does it preserve the task's scope boundaries?
5. Are assumptions clearly separated from facts?
6. Can each milestone be verified independently?
7. Does the plan explain why the approach fits the existing system?
8. Does it identify important unknowns?
9. Could another developer resume the task using the plan?
10. Is the planning effort proportional to the task?

---

## Plan anti-patterns

- Rephrasing the issue as a numbered list
- Listing files without explaining why they change
- Choosing an architecture before inspecting the repository
- Describing implementation details while omitting the desired behavior
- Producing a plan so abstract that it cannot guide edits
- Producing a plan so detailed that it copies the future implementation
- Treating the original plan as immutable after discovering new evidence
- Hiding unresolved assumptions
- Using a large execution plan for a trivial edit

---

## Practical exercise

Provide a feature request and a small repository.

Ask participants to:

1. Inspect the relevant implementation.
2. Produce a five-step plan before editing.
3. Mark which statements are facts and which are assumptions.
4. Identify one event that would require changing the plan.
5. Define observable acceptance evidence for each milestone.

---

## Overlap guardrail

Do not cover:

- Tool-specific Plan Mode
- Multi-agent task assignment
- Parallel execution
- Approval checkpoints
- Workspace isolation
- Detailed design-exploration methods
- Formal validation-first architectures

Those belong in Modules 3, 4, and 5.

---

# Topic 2.6: Model Selection and Cost Optimization

## Objective

Teach developers to choose models based on task requirements, measured quality, latency, and total completion cost.

The goal is not to memorize a provider's current model catalog. Model names, prices, and rankings change too frequently.

The durable principle is:

    Establish the required quality level, then find the least expensive and
    fastest model that continues to meet it.

Current model-selection guidance recommends optimizing for accuracy first, then testing whether smaller and faster models preserve the required quality. Cost guidance emphasizes fewer requests, fewer unnecessary tokens, and appropriate use of smaller models. [R6]

---

## Model-selection dimensions

### Task ambiguity

How much interpretation is required?

A mechanical transformation requires less reasoning than an underspecified cross-cutting change.

### Reasoning depth

Does the task require several dependent decisions or trade-offs?

### Repository scope

Is the work limited to one known function, or must the model understand several packages and interfaces?

### Context volume

How much source code, documentation, or runtime evidence must be considered simultaneously?

### Output precision

Does the output need to follow a strict schema, API, patch format, or compatibility rule?

### Tool capability

Does the task require repository search, file editing, command execution, image understanding, or another capability?

Tool configuration itself belongs in Module 3.

### Latency

Is the developer waiting interactively, or can the task tolerate slower processing?

### Volume

Is this a single task or a repeated high-volume workload?

### Consequence of error

How expensive is an incorrect answer in terms of developer time and rework?

---

## Generic model classes

### Fast, economical model

Appropriate when:

- The task is narrow and explicit
- Relevant context is small
- The transformation is repetitive
- The expected output is highly constrained
- Incorrect output is easy to detect and correct

### Balanced general-purpose model

Appropriate when:

- The task follows existing repository patterns
- Several related files must be considered
- Moderate reasoning is required
- The developer needs an interactive balance of speed and quality

### High-capability reasoning model

Appropriate when:

- Requirements are ambiguous
- The change is cross-cutting
- Several approaches have significant trade-offs
- The relevant architecture is unfamiliar
- Errors are difficult or expensive to detect
- The task has repeatedly failed with a smaller model

These are workload categories, not permanent labels for particular products.

---

## Quality-first selection process

### Step 1: Define success

Establish task-specific criteria.

Examples:

- Correct behavior
- Compatibility
- Required test coverage
- Maximum acceptable human correction
- Output-format compliance
- Maximum latency

### Step 2: Establish a reference result

Use a sufficiently capable model to determine whether the task and prompt can meet the quality target.

### Step 3: Test a smaller or faster model

Run the same representative task set with a less expensive model.

### Step 4: Compare accepted results

Do not compare only the first response.

Compare:

- First-pass correctness
- Number of retries
- Human correction time
- Unnecessary changes
- Context consumed
- Output consumed
- Time to an accepted result

### Step 5: Define escalation rules

Examples:

- Start with the economical model for a localized task.
- Escalate after one failed attempt involving repository misunderstanding.
- Use the stronger model immediately when the task crosses several packages.
- Use a deterministic tool instead when the operation is mechanical.

---

## Total cost of completion

The cheapest individual response does not necessarily produce the cheapest completed task.

A useful mental model is:

    Total completion cost =
        model input cost
        + model output cost
        + repeated requests
        + repeated context
        + tool execution cost
        + developer review time
        + developer correction time
        + cost of rework caused by errors

A stronger model may be less expensive overall when it substantially reduces retries and correction effort.

A smaller model may be more efficient when the task is clear, repetitive, and easy to verify.

---

## Cost-optimization techniques

### Reduce irrelevant context

Do not repeatedly send files that do not affect the task.

### Request appropriately sized output

Ask for a patch or focused explanation instead of a complete rewrite when only a small change is needed.

### Avoid redundant turns

Combine tightly related questions when they can be answered from the same context.

Do not combine unrelated work merely to save a request.

### Preserve stable instructions

Keep durable repository guidance in instruction files instead of repeating it manually in every prompt.

### Structure repeated API prompts for caching

For API workflows that support prompt caching, place stable repeated instructions and examples before changing task-specific information. Exact provider behavior should be checked against current documentation. [R7]

### Route by task class

Use a smaller model for predictable work and escalate when task complexity requires it.

### Use deterministic tools for deterministic work

An AI model is usually unnecessary for:

- Formatting already handled by a formatter
- Exact text replacement
- Dependency graph generation
- Static type checking
- Running tests
- Sorting data
- Schema validation
- Code generation already provided by an official generator

### Control retries

When a response fails, diagnose why before sending another request.

Possible causes include:

- Weak prompt
- Missing context
- Wrong model class
- Incorrect repository instructions
- Tool failure
- Unsuitable task scope

Changing the model is only one possible correction.

---

## Small model-evaluation worksheet

    # Task set

    <List 10–20 representative tasks or examples.>

    # Required quality

    <Define the minimum acceptable result.>

    | Measure | Model A | Model B | Model C |
    |---|---:|---:|---:|
    | First-pass accepted results | | | |
    | Average retries | | | |
    | Average input tokens | | | |
    | Average output tokens | | | |
    | Average elapsed time | | | |
    | Average human correction time | | | |
    | Unnecessary-file changes | | | |
    | Estimated cost per accepted result | | | |

    # Selection

    Selected model:
    Reason:
    Escalation condition:
    Re-evaluation trigger:

---

## Model-selection anti-patterns

- Always selecting the most capable model
- Always selecting the cheapest model
- Choosing from leaderboard position alone
- Comparing models using one anecdotal task
- Ignoring retries and correction time
- Using a long-context model as permission to provide unfiltered context
- Switching models while also changing the prompt and context, making comparison impossible
- Treating an old model comparison as permanently valid
- Using an AI model for work already solved reliably by deterministic tooling

---

## Practical exercise

Give participants three task descriptions:

1. A precise, single-file mechanical change
2. A known multi-file change following an existing pattern
3. An ambiguous cross-package change with architectural trade-offs

Ask them to select a model class for each task and justify the choice using:

- Accuracy requirement
- Context requirement
- Latency
- Expected retry rate
- Human correction cost
- Escalation condition

The exercise should not depend on specific model names.

---

## Overlap guardrail

Do not cover:

- Provider account configuration
- API key setup
- Harness model configuration
- Organization-wide spend controls
- Team productivity metrics
- Procurement policy
- Security-based model restrictions

Those belong in Modules 1, 3, 7, and 8.

---

# Integrated Module Exercise

## Scenario

Participants receive:

- A small repository
- An issue describing one behavior change
- A failing test or reproducible error
- Existing project documentation
- An incomplete or outdated `AGENTS.md`
- Access to at least two model classes

## Deliverables

Each participant produces:

1. A scoped task brief
2. A structured developer prompt
3. A context package
4. An improved `AGENTS.md`
5. A plan at the appropriate level of detail
6. A model-selection decision
7. One focused implementation attempt
8. A closing report describing evidence and limitations

The coding task should remain intentionally simple. The assessment concerns the interaction process, not advanced implementation technique.

---

## Assessment rubric

### Task framing — 20%

- Problem and desired behavior are clear
- Scope and exclusions are explicit
- Acceptance criteria are observable

### Prompt quality — 15%

- Prompt has a clear objective
- Constraints and expected output are stated
- Uncertainty is handled explicitly

### Context quality — 20%

- Selected information is relevant
- Evidence and versions are identified
- Irrelevant material is excluded

### Repository instructions — 15%

- Instructions are actionable and scoped
- Commands are concrete
- Stable guidance is separated from task-specific guidance

### Plan quality — 15%

- Plan is grounded in the repository
- Milestones are concrete
- Acceptance evidence is defined
- Planning depth matches task complexity

### Model decision — 10%

- Selection is based on task requirements
- Total completion cost is considered
- An escalation rule is defined

### Completion report — 5%

- Actual checks are distinguished from assumptions
- Remaining limitations are stated clearly

---

# Suggested delivery format

Recommended duration: approximately 4 to 5 hours.

- Module positioning and terminology: 20 minutes
- AI-assisted development workflow: 40 minutes
- Prompt engineering: 45 minutes
- Context engineering: 45 minutes
- Repository instructions: 40 minutes
- Plan-first development: 40 minutes
- Model selection and cost optimization: 35 minutes
- Integrated exercise and review: 60 minutes

---

# Recommended emphasis

Spend the most instructional time on the distinctions between:

- Prompt and context
- Temporary task instructions and durable repository instructions
- Planning discipline and tool-specific Plan Mode
- Cheapest response and cheapest accepted result
- More context and better context

These distinctions provide the conceptual foundation required by all later modules.

---

# Research references

[R1] Clear task framing, acceptance criteria, and relevant-file guidance.

[R2] Structured instructions, examples, contextual material, and measurable success criteria.

[R3] Context as a finite resource; high-signal context and progressive disclosure.

[R4] AGENTS.md as durable repository guidance, including hierarchical instructions.

[R5] Self-contained, living, outcome-focused execution plans and verifiable milestones.

[R6] Accuracy-first model selection followed by cost and latency optimization.

[R7] Reuse of stable prompt prefixes and placement of variable context later.