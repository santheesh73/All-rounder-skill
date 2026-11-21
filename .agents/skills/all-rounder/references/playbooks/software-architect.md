# Software Architect

## Purpose

Choose system boundaries that support the requested behavior and the way the system will be operated.

## Activation conditions

Use for new systems, substantial cross-module changes, shared contracts, or decisions costly to reverse. Follow the established architecture for local edits that fit its boundaries.

## Required context

Existing modules and deployment topology, external consumers, data ownership, failure expectations, workload targets, and operational constraints.

## Execution procedure

1. Trace one representative request through component boundaries, storage, and external effects. Trace what happens when a dependency fails.
2. Identify the owner of each invariant and source of truth. Specify boundary contracts, validation, authorization, and compatibility.
3. Compare the existing design and viable alternatives against coupling, operational burden, failure isolation, and measured capacity limits. Identify the load or change that would justify another boundary.
4. Define behavior under timeouts, retries, and partial failure. Identify the consistency guarantee, who owns recovery, and what old and new consumers can tolerate during migration.
5. Record the selected design, material tradeoffs, and evidence that would justify revisiting it.

## Decision criteria

Prefer an in-process boundary when independent deployment, scaling, or failure isolation is unnecessary. Use asynchronous work only when consumers can tolerate its consistency and failure model.

## Quality and safety rules

Give each invariant a clear owner. Keep interfaces narrow and make privacy and trust boundaries explicit.

## Failure handling

Without workload or reliability data, mark assumptions and specify what measurements would confirm them. Favor reversible decisions or investigate before committing to a costly boundary.

## Expected result

A design identifying responsibilities, interfaces, data flow, failure behavior, and tradeoffs.

## Completion criteria

Key use cases and failure paths are accounted for. Existing consumers have an implementable transition where needed.
