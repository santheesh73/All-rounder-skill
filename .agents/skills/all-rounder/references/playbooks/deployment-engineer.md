# Deployment Engineer

## Purpose

Assess or execute a release with explicit checks and recovery conditions.

## Activation conditions

Use for release readiness, deployment changes, or an authorized rollout. Apply normal build and test checks to local changes without release implications.

## Required context

Release scope and revision, build and environments, CI or release workflow, config requirements, dependencies, rollout process, and operator permissions.

## Execution procedure

1. Identify the candidate revision, artifact or build identifier, and target. Match CI and build evidence to that exact candidate. Check required configuration keys, secret references, and version compatibility.
2. Review changes that affect startup, data migrations, traffic, and operations. Define preconditions and failure criteria for proceeding or stopping.
3. Specify rollout order and smoke checks. Identify monitoring signals, their observation window, and the owner or mechanism that can halt or recover the release.
4. Validate recovery against the actual state changes. If a migration affects compatibility between builds, data integrity, or recovery, read [Database Engineer](database-engineer.md) before assessing those gates. Apply its migration and recovery checks to the candidate. For irreversible data changes, identify the conditions for forward repair or restore.
5. Execute only with authority for the named target. Observe agreed smoke and health checks against the deployed artifact. Stop or apply the approved recovery procedure if a defined halt condition is met.

## Decision criteria

Choose staged rollout when blast radius and observability justify it. Pause on unmet mandatory checks, ambiguous targets, or undefined recovery for an irreversible operation.

## Quality and safety rules

Treat readiness review as a scope distinct from deployment. Protect environment values and confirm authority before live changes or credential operations.

## Failure handling

If CI or deployment access is missing, report what the configuration establishes and which build, smoke, or recovery checks require an operator. If migration guidance or database evidence is unavailable, mark the affected gate open and continue with the evidence that can be inspected.

## Expected result

A release assessment or an evidenced deployment outcome with operational checks and recovery steps.

## Completion criteria

The release artifact and target are identified. Required gates, health evidence, recovery prerequisites, and any unmet conditions are explicit.
