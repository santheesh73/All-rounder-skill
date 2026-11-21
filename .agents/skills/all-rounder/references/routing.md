# Playbook routing

Route by the result the user requested. Choose one primary playbook for the current phase. Add a support playbook when it owns a distinct decision or check that the primary workflow cannot cover. Reassess after a change in evidence, scope, or risk, using prior findings that still apply.

Use Code Review for general defect review. Route a concern-specific review to its domain owner, such as Database Engineer for migration compatibility, Security Auditor for access controls, or Test-Driven Development for coverage and contract checks. Route a request to define one implementable feature slice to Full-Stack Development, even if the user wants a design only. Use Project Planner when the deliverable is scope, ordering, or milestones.

| Requested result | Primary playbook | Add only when needed |
| --- | --- | --- |
| Requirements, scope, or an implementation sequence | [Project Planner](playbooks/project-planner.md) | Architecture for costly design decisions. |
| System design, interfaces, or ownership | [Software Architect](playbooks/software-architect.md) | Analysis for an existing system, planning for staged delivery. |
| Explain an existing flow or map affected code | [Codebase Analyzer](playbooks/codebase-analyzer.md) | Stop after analysis when explanation is the deliverable. |
| Implement an application feature or integration | [Full-Stack Development](playbooks/fullstack-development.md) | Analysis for unknown code, design for material UI changes, database guidance for data changes, testing for missing coverage. |
| Design or redesign a UI | [Frontend Design](playbooks/frontend-design.md) | Analysis for unfamiliar existing components, browser testing for actual rendered behavior. |
| Change schema, data integrity, roles, or queries | [Database Engineer](playbooks/database-engineer.md) | Performance for a measurable bottleneck, security for changed access boundaries, testing for data behavior. |
| Explain or fix a benign runtime failure or a failing test whose cause is unclear | [Systematic Debugging](playbooks/systematic-debugging.md) | Analysis for unfamiliar wiring, test development when new coverage is needed. |
| Add tests or define implementation through a test | [Test-Driven Development](playbooks/test-driven-development.md) | The domain playbook if the same task changes production behavior. |
| Review a change for actionable defects | [Code Review](playbooks/code-review.md) | Security for material trust boundaries or authorization, performance when a claim requires measurement. |
| Inspect or remediate a suspected security issue | [Security Auditor](playbooks/security-auditor.md) | Analysis for unclear wiring, database guidance when access policies affect database roles or resources. |
| Improve measured latency, resource use, or throughput | [Performance Optimizer](playbooks/performance-optimizer.md) | Domain guidance for the affected layer, testing for behavior preservation. |
| Check UI journeys and responsive behavior in a browser | [Browser Testing](playbooks/browser-testing.md) | Frontend design for requested visual or interaction changes. |
| Configure a remote or manage staged changes, branches, commits, or pull requests | [Git Workflow](playbooks/git-workflow.md) | Code review if a substantive review is requested. |
| Assess release readiness or perform an authorized rollout | [Deployment Engineer](playbooks/deployment-engineer.md) | Review and testing for evidence gaps, database guidance for migration integrity or recovery, security for material boundary changes. |
| Create or update technical documentation | [Documentation Writer](playbooks/documentation-writer.md) | Analysis when implementation evidence is needed. |
| Resume interrupted work or prepare a handoff | [Context Manager](playbooks/context-manager.md) | The next domain playbook only if execution is in scope. |

## Resolve overlaps

| Decision | Owner |
| --- | --- |
| What must be delivered, in what order, and how success is observed | Project Planner. Software Architect owns interfaces, component boundaries, and tradeoffs. |
| What the current code does | Codebase Analyzer. Context Manager reconciles prior decisions and work state for resumption or handoff. |
| Application behavior, contracts, and implementation across layers | Full-Stack Development. Frontend Design owns visual hierarchy, component states, and interaction patterns. |
| Where and how to add automated behavior coverage | Test-Driven Development. Browser Testing owns verification in the rendered browser. Systematic Debugging owns diagnosis of an unexplained failing test. |
| General defects and compatibility regressions | Code Review. Security Auditor owns trust boundaries and defensive evaluation of access controls or suspected vulnerabilities. |
| Query semantics, locking, role visibility, and migration integrity | Database Engineer. Performance Optimizer owns measurement design and claims about resource use, throughput, and latency. |
| Branch, index, commit, and publication state | Git Workflow. Deployment Engineer owns release evidence, target health, and recovery. |

## Typical sequences

- **New application:** Start with planning. Add architecture for consequential design choices, then switch to Full-Stack Development and verify each implemented slice when authorized.
- **Single-file edit with a known cause:** Use Lightweight, inspect the affected path, and run a focused check. Skip a separate planning, architecture, or debugging pass unless new evidence warrants it.
- **Visual redesign:** Start with Frontend Design. Use Browser Testing for rendered acceptance, or report that gap if no browser is available. Load Performance Optimizer only when a budget or measured problem is in scope.
- **Slow query:** Start with Database Engineer when preserving query semantics or changing access paths. Add Performance Optimizer for a measured before-and-after claim.
- **Release assessment:** Start with Deployment Engineer. Reuse review and test evidence for the exact candidate. Add Database Engineer when migration compatibility or recovery matters.

An explanation stops when the behavior is supported. A handoff stops after reporting current state unless work resumption was requested. A specialist already covering the task can own its procedure under the host's selection rules. Keep duplicate guidance and unrelated playbooks unloaded, even when their files are available.
