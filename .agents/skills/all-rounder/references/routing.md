# Playbook routing

Route by the requested result. Select the primary playbook from the table, then add a supporting playbook only when a separate procedure or check would materially change the outcome. Interpret relative links from the file containing them.

| Requested result | Primary playbook | Add only when needed |
| --- | --- | --- |
| Requirements, scope, or an implementation sequence | [Project Planner](playbooks/project-planner.md) | Architecture for costly design decisions. |
| System design, interfaces, or ownership | [Software Architect](playbooks/software-architect.md) | Analysis for an existing system, planning for staged delivery. |
| Explain an existing flow or map affected code | [Codebase Analyzer](playbooks/codebase-analyzer.md) | Stop after analysis when explanation is the deliverable. |
| Implement an application feature or integration | [Full-Stack Development](playbooks/fullstack-development.md) | Analysis for unknown code, design for material UI changes, database guidance for data changes, testing for missing coverage. |
| Design or redesign a UI | [Frontend Design](playbooks/frontend-design.md) | Analysis for unfamiliar existing components, browser testing for actual rendered behavior. |
| Change schema, data integrity, roles, or queries | [Database Engineer](playbooks/database-engineer.md) | Performance for a measurable bottleneck, security for changed access boundaries, testing for data behavior. |
| Find and fix an unexplained benign failure | [Systematic Debugging](playbooks/systematic-debugging.md) | Analysis for an unfamiliar path, testing for a behavior gap. |
| Add tests or define implementation through a test | [Test-Driven Development](playbooks/test-driven-development.md) | The domain playbook if the same task changes production behavior. |
| Review a change for actionable defects | [Code Review](playbooks/code-review.md) | Security for material trust boundaries or authorization, performance when a claim requires measurement. |
| Inspect or remediate a suspected security issue | [Security Auditor](playbooks/security-auditor.md) | Analysis for unclear wiring, database guidance when access policies affect database roles or resources. |
| Improve measured latency, resource use, or throughput | [Performance Optimizer](playbooks/performance-optimizer.md) | Domain guidance for the affected layer, testing for behavior preservation. |
| Check UI journeys and responsive behavior in a browser | [Browser Testing](playbooks/browser-testing.md) | Frontend design for requested visual or interaction changes. |
| Configure a remote or manage staged changes, branches, commits, or pull requests | [Git Workflow](playbooks/git-workflow.md) | Code review if a substantive review is requested. |
| Assess release readiness or perform an authorized rollout | [Deployment Engineer](playbooks/deployment-engineer.md) | Review and testing for evidence gaps, database guidance for migration integrity or recovery, security for material boundary changes. |
| Create or update technical documentation | [Documentation Writer](playbooks/documentation-writer.md) | Analysis when implementation evidence is needed. |
| Resume interrupted work or prepare a handoff | [Context Manager](playbooks/context-manager.md) | The next domain playbook only if execution is in scope. |

## Combine playbooks

- **New application:** Plan the requested scope, settle consequential design decisions, implement in slices, and verify each slice. Load domain references at the relevant slice. For a prototype with settled requirements, skip a separate architecture pass.
- **Bug in unfamiliar code:** Locate the relevant path, then debug it. Use test-driven development when coverage must be added. For suspected vulnerabilities, start with the defensive Security Auditor and use safe control checks.
- **Site redesign:** Inspect existing components if unfamiliar, apply frontend design, then verify rendered journeys when browser tools exist. Measure performance when a budget or bottleneck warrants it.
- **Slow query:** Use Database Engineer for query semantics and execution plans and Performance Optimizer for the comparison. Add test guidance when existing checks do not protect result and access semantics.
- **Authorization review:** Begin with Security Auditor. Add analysis when wiring is unclear and Database Engineer when the database enforces relevant access.
- **Production release:** Establish the release gates with Deployment Engineer. Reuse applicable review, test, and security evidence for the exact candidate revision. Add Database Engineer when a migration affects compatibility, integrity, or recovery.

For an explanation, review, or readiness assessment, stop at the requested result. When a needed capability is missing, keep the intended verification in scope and report the gap using the available fallback.
