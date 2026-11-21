# Quality gates

Choose checks from the requested acceptance criteria and the failure modes of the affected change. Prefer checks through the real entry point and reuse current results only when they cover the same revision, configuration, and behavior.

| Gate | Apply when | Evidence to seek |
| --- | --- | --- |
| Requirements | Any task with an expected outcome | Inspect the deliverable against acceptance criteria and exercise observable behavior where applicable. |
| Regression | An existing behavior, caller, or data shape can be affected | Exercise one relevant preserved path and affected edge cases, including older data or callers where applicable. |
| Tests and build | The change affects executable behavior or build inputs | Run focused tests and applicable lint, types, or build checks. Broaden coverage when cross-component impact or project rules warrant it. |
| Review | A change was made or review was requested | Inspect the final scoped diff or requested revision for correctness, failure paths, compatibility, and unrelated edits. |
| Security | A change affects identity, sensitive data, trust boundaries, or permissions | Inspect enforcement and configuration. Exercise safe allow and deny control cases with scoped fixtures where feasible. |
| Performance | A budget or optimization claim is in scope | Compare comparable measurements with known conditions, sample counts, and correctness results. |
| Data integrity | Schemas, queries, permissions, or persisted data behavior change | Check representative records, roles, constraints, concurrency or locks where relevant, and interruption or recovery for migrations. |
| Deployment | A release or production readiness is in scope | Verify artifact and revision, required CI, config and recovery conditions, and health where authorized and executed. |
| Documentation | The deliverable is documentation or a documented workflow changes | Verify links, commands, examples, and current behavior. |

## Check status

- **PASSED** means a check ran or the required inspection was completed, and the evidence met the criterion.
- **FAILED** means a check ran or an inspection was completed and the criterion was not met. State the observed failure and its impact.
- **NOT RUN** means an applicable check was omitted despite being feasible. State why.
- **UNAVAILABLE** means an applicable check could not produce a result because a required tool, permission, environment, or fixture was missing. State the missing prerequisite and any narrower check that ran.
- **NOT APPLICABLE** means the gate does not apply to the task. Omit routine irrelevant gates from the user report.

When a check fails, use the error to distinguish a behavior defect from a setup issue. Fix in-scope defects and rerun impacted checks. If a required gate remains open, identify the incomplete acceptance criterion. Treat a pre-existing failure as such only when baseline evidence supports the attribution.
