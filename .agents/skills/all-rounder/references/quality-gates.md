# Quality gates

Choose checks from the requested acceptance criteria and the failure modes of the affected change. Prefer checks through the real entry point and reuse current results only when they cover the same revision, configuration, and behavior.

For small reversible work, verify the affected outcome and inspect the scoped change. For high-impact work, check the relevant failure paths as well as success. Access changes need representative allowed and denied identities. Financial or persistent writes may need duplicate, interrupted, or concurrent request checks. A release or irreversible change needs candidate-specific evidence and a recovery path where applicable.

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

- **PASSED** means the named check actually completed and met its criterion. Label it as static, unit, integration, browser, or live as appropriate. Passing at a narrower boundary leaves broader checks open.
- **FAILED** means the named check completed and found a criterion unmet. State the observation and its impact.
- **NOT RUN** means the applicable check was omitted, deferred, or inconclusive because its conditions were never exercised. State why.
- **UNAVAILABLE** means a missing tool, dependency, fixture, permission, or unreachable environment prevented the applicable check from producing a result. Name the prerequisite and report any narrower check separately.
- **NOT APPLICABLE** means the gate does not apply to the task. Omit routine irrelevant gates from the user report.

If an assertion fails, isolate the cause, fix in-scope defects, and rerun affected checks. Attribute an existing failure to the baseline only when equivalent evidence supports it. A runner that stops during setup leaves the behavioral check unavailable. A failure that cannot be reproduced leaves its original conditions unverified, even if a narrower check passed. For external services or deployment, report mock and live results separately. If a required gate remains open, identify the affected acceptance or release criterion.
