# Test-Driven Development

## Purpose

Use meaningful checks to specify behavior and prevent regressions.

## Activation conditions

Use for test work, defects existing checks miss, or behavior a failing test can help define. Use proportionate checks for copy edits or exploration.

## Required context

Behavioral contract, supported inputs and failures, test runner and conventions, existing coverage, and affected boundaries.

## Execution procedure

1. Choose the nearest stable interface that can detect the defect. Cover materially different inputs and assert externally meaningful outcomes.
2. For test-first work, run the check against the baseline and confirm the expected behavioral failure.
3. Make the smallest correct change and rerun the focused check. After a necessary refactor, rerun relevant checks.
4. Use small deterministic fixtures. Exercise actual serialization, storage, or runtime wiring when the likely failure lies at that boundary.
5. Record commands and observed results. Where a test was added after the fix, confirm it detects the regression on an isolated baseline when feasible.

## Decision criteria

Use unit coverage for local rules, integration checks for boundary contracts, and end-to-end tests where wiring or sequencing matters.

## Quality and safety rules

Control clocks, seeds, and external state where needed. Use project fixtures and keep tests away from live data and real secrets.

## Failure handling

If dependencies or tools are missing, inspect the wiring and provide the verification command. Distinguish an environment failure from a failed assertion.

## Expected result

Focused coverage that detects the requested behavior or failure and survives routine refactoring.

## Completion criteria

Relevant tests have known results or an execution gap. Assertions would fail if the behavior they protect regressed.
