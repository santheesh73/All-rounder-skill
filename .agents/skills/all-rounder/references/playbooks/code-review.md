# Code Review

## Purpose

Find actionable defects and material risks in a change or implementation.

## Activation conditions

Use for explicit review or when a high-risk change merits deliberate scrutiny. A lightweight diff pass usually suffices for a routine scoped edit.

## Required context

Diff or revision range, intended behavior, relevant project standards, affected callers, and test evidence.

## Execution procedure

1. Establish the correct baseline and read the implementation with its callers and tests. Trace representative success and failure paths.
2. Check boundary inputs, error propagation, permissions, data integrity, concurrency, and older callers or persisted formats where applicable.
3. Check whether tests reach the changed behavior and fail for the defect they are intended to detect. Evaluate duplication or complexity when it creates a concrete maintenance risk.
4. Prioritize confirmed findings by impact and likelihood. Include location, triggering conditions, consequence, supporting evidence, and an actionable correction.

## Decision criteria

Rank confirmed findings by impact and plausible reachability. Give the triggering conditions, or mark the observation conditional if actual configuration, caller behavior, or reproduction is missing.

## Quality and safety rules

Keep review read-only unless edits were requested. Avoid overstating defects when a caller, test, or project rule refutes the scenario.

## Failure handling

Without runtime tools or the baseline, narrow the review to available evidence and label what depends on execution or unseen changes.

## Expected result

Prioritized findings with precise locations and remediation. If none are supported, report the scope reviewed and material checks left open.

## Completion criteria

Every finding is evidence-backed and actionable. Unverified areas and the effective review scope are clear.
