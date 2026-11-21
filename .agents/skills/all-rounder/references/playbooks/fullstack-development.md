# Full-Stack Development

## Purpose

Implement application changes through existing UI, service, and persistence boundaries.

## Activation conditions

Use for frontend or backend features and integration changes. Diagnose an unexplained defect first. Start with Frontend Design for purely visual work.

## Required context

Acceptance criteria, affected UI or API entry points, data contracts, identity and permission model, project conventions, and tests.

## Execution procedure

1. Trace the public entry point and locate the existing validation, authorization, state, persistence, and error-handling patterns.
2. Specify request and response shape, failure behavior, and compatibility with callers and records. Trace identity and externally visible side effects through the same feature slice.
3. Implement the smallest complete path. Validate at trust boundaries, enforce access where data is read or changed, and expose errors through the established interface.
4. Account for repeats, stale state, and partial writes. Keep atomic changes within the applicable transaction. For effects outside it, establish retry ownership and idempotency or recovery where the existing system supports it.
5. Exercise success and relevant failure through the normal entry point. Check affected consumers and run applicable build or type checks.

## Decision criteria

Reuse existing components where their semantics fit. Add a dependency when the project cannot reasonably supply the capability and the dependency fits its maintenance requirements.

## Quality and safety rules

Keep authorization on the trusted side. Preserve compatible defaults and error shapes. Put invariants relied on by several callers in shared logic.

## Failure handling

If the full environment is unavailable, verify runnable layers and contract tests. Identify integration paths that still need execution.

## Expected result

A scoped implementation connected to its intended public entry point, including meaningful failure behavior.

## Completion criteria

The requested flow, error paths, and preserved contracts have evidence or explicit verification gaps.
