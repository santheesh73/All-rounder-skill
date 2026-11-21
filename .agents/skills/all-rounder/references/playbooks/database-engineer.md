# Database Engineer

## Purpose

Change data structures and access paths while preserving integrity, availability, and access boundaries.

## Activation conditions

Use for data modeling, migrations, permissions, concurrency, or query work. For a read-only code explanation, use analysis alone when no database-specific decisions are needed.

## Required context

Engine and version, schema and migrations, data shape and scale, read and write paths, roles, and environments.

## Execution procedure

1. State data invariants. Review keys, nullability, uniqueness, referential integrity, and role permissions.
2. Check existing data against new constraints. Plan how to handle duplicates, orphans, or invalid values before enforcement.
3. For mixed-version deployments, check which reads and writes work in each rollout phase, including rollback to the previous build. Use a compatible sequence such as expand, backfill, verify, then contract. Determine lock acquisition, transaction support for DDL, and retry behavior in the actual engine.
4. For query tuning, compare plans across representative parameters in a suitable environment. Evaluate index maintenance cost and preserve results, ordering, and visibility.
5. Verify invariants under application roles and representative sanitized records. For a backfill, define how progress is detected and how a retry avoids duplicating or skipping concurrent writes.

## Decision criteria

Use database constraints for invariants shared by writers when feasible. Batch writes when a single transaction exceeds lock, log, or latency budgets. Use forward repair or restore when a down migration cannot recover lost data.

## Quality and safety rules

Confirm environment and role, use least privilege, and keep real records out of fixtures. Destructive production changes need explicit authority and a recovery path.

## Failure handling

Without database access, review SQL and migration order statically. List integrity, locking, role, and recovery checks that require a database.

## Expected result

A justified data-layer change with checks for relevant invariants and recovery conditions.

## Completion criteria

Integrity, compatibility, and role checks have results or documented gaps. Deployment and recovery prerequisites are explicit.
