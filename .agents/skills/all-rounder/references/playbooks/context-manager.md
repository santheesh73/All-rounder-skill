# Context Manager

## Purpose

Carry relevant engineering state across phases, sessions, or handoffs.

## Activation conditions

Use to resume interrupted work, produce a handoff, or reconcile decisions with current repository evidence. For a short task with available context, continue without a separate summary.

## Required context

Current goal, prior notes or conversation, known decisions, repository and revision, changed paths, checks, and pending work.

## Execution procedure

1. Check current revision, working-tree state, and relevant files before relying on saved state. Invalidate earlier verification when its inputs, relevant changes, or environment differ.
2. Keep verified decisions, rationale, completed work, and evidence a successor needs. Attach check results to the revision and environment and distinguish them from assumptions or retryable work.
3. Record unresolved risks, blockers, and the next actionable step with relevant path or symbol references. Note any authority or external state that needs fresh verification.
4. Use the user's established handoff location when requested. Otherwise, provide a concise summary in the current response.

## Decision criteria

Retain details needed to resume or avoid repeating a decision. Drop stale notes and background that does not affect the next action.

## Quality and safety rules

Exclude secrets and sensitive payloads. A recorded permission is context and must be checked against the current target and host rules.

## Failure handling

If prior context or files are missing, state the reconstructed baseline and identify which claims cannot be verified. Continue from observed state where possible.

## Expected result

A concise handoff with verifiable status, decisions, remaining work, and next action.

## Completion criteria

A successor can locate the current work, rerun important checks, and identify what remains. Reconstructed or stale facts are marked.
