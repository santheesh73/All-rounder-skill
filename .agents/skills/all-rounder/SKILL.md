---
name: all-rounder
description: >-
  Guide software engineering work in a codebase. Use for project planning,
  architecture, repository analysis, implementation, UI and database changes,
  debugging, testing, code and security review, performance tuning, Git and
  release work, technical documentation, or engineering handoffs.
---

# All-rounder

Use this skill to complete the requested engineering task with evidence appropriate to its impact. Repository conventions and explicit user requirements shape the work within the host's governing instructions and permissions. A skill invocation does not authorize additional changes or external actions.

## Understand the task

- Identify the requested outcome, affected system, constraints, and observable acceptance criteria. Distinguish a request to explain, review, or plan from a request to change or execute.
- Check applicable project instructions and the state of the relevant workspace. Start at the closest entry point, including related tests and configuration. Reuse decisions and findings that still match the current files or revision.
- Proceed with a stated, reversible assumption when it preserves the intended outcome. Ask a focused question when the missing answer changes the deliverable, permission, or safety of the next step.
- Identify which tools and environments are available for the next action. Scope tool use to the requested target.

## Select an execution mode

| Mode | Choose when | Apply |
| --- | --- | --- |
| Lightweight | The task is well scoped, low impact, and readily reversible. | Inspect the affected area, make or explain the focused change, and run a proportionate check. |
| Standard | The change crosses components, alters a contract, or needs incremental verification. | Trace dependencies, define milestones if useful, verify behavior at the affected boundaries, and inspect the final diff. |
| High Assurance | Work is security-sensitive, data-sensitive, production-impacting, or complex enough that failures would be hard to detect or reverse. | Confirm scope, permissions, and failure conditions. Select stronger checks, define recovery where relevant, and reassess remaining risk before any consequential action. |

Use the highest mode warranted by the actual impact. Reassess when new evidence changes the scope or reversibility. Permission and secret-handling rules apply in every mode.

## Route and execute

1. Read [routing](references/routing.md) and start with the playbook for the requested deliverable. Add a supporting playbook only when its distinct decision, procedure, or verification is needed. Load it when that step becomes relevant.
2. Work through the closest usable entry point. Reuse project patterns that satisfy the requirements. Keep changes scoped and confirm behavior at the points where callers or operators experience it.
3. Use [risk policy](references/risk-policy.md) for trust boundaries, permissions, sensitive data, destructive operations, or changes with external effects. Verify the target and authority before crossing a boundary. Use [capability fallbacks](references/capability-fallbacks.md) if a needed tool, environment, or evidence source is missing.
4. Select applicable checks from [quality gates](references/quality-gates.md) before declaring completion. Exercise the original failure or new behavior where applicable and check important preserved behavior. A failed, unavailable, or unrun check leaves a distinct evidence gap.
5. Report the outcome using the [evidence contract](references/evidence-contract.md). For a small change, a short statement of the result, check, and any remaining gap is enough.

If a check exposes a new issue, determine whether it prevents the current acceptance criteria. Fix and recheck issues within scope. Record unrelated issues only when they materially affect the user's decision.

## Playbook index

Use these direct links once you select a playbook.

- [Project Planner](references/playbooks/project-planner.md), [Software Architect](references/playbooks/software-architect.md), [Codebase Analyzer](references/playbooks/codebase-analyzer.md), [Full-Stack Development](references/playbooks/fullstack-development.md)
- [Frontend Design](references/playbooks/frontend-design.md), [Database Engineer](references/playbooks/database-engineer.md), [Systematic Debugging](references/playbooks/systematic-debugging.md), [Test-Driven Development](references/playbooks/test-driven-development.md)
- [Code Review](references/playbooks/code-review.md), [Security Auditor](references/playbooks/security-auditor.md), [Performance Optimizer](references/playbooks/performance-optimizer.md), [Browser Testing](references/playbooks/browser-testing.md)
- [Git Workflow](references/playbooks/git-workflow.md), [Deployment Engineer](references/playbooks/deployment-engineer.md), [Documentation Writer](references/playbooks/documentation-writer.md), [Context Manager](references/playbooks/context-manager.md)
