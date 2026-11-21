# Systematic Debugging

## Purpose

Explain a failure with evidence and correct the smallest responsible behavior.

## Activation conditions

Use for unexpected failures and regressions with an uncertain cause. Apply a direct fix when reliable evidence has already isolated the cause and affected behavior.

## Required context

Expected and actual behavior, safe inputs or sanitized incident evidence, environment, revision, and the last known good state when available.

## Execution procedure

1. Reproduce with the smallest safe input or record when an intermittent failure occurs. Capture the result and one meaningful control case.
2. Trace backward to the first incorrect state. Compare with a passing path or revision and form hypotheses that predict different observations.
3. Record the observation each hypothesis predicts and run the smallest safe check that distinguishes them. Change one factor at a time and remove temporary instrumentation.
4. Apply a targeted correction after evidence supports a cause. Add regression coverage when existing checks miss the failure.
5. Repeat the original path and check neighboring or previously passing behavior. For intermittent issues, report sample count and uncertainty.

## Decision criteria

Use controlled repetition for timing-dependent issues and a revision range when a regression is suspected. Separate a demonstrated cause from a suspected contributor.

## Quality and safety rules

Use reproduction for authorized, benign failures. Route suspected vulnerabilities to defensive review and safe control checks. Keep instrumentation from obscuring or changing the failure.

## Failure handling

If reproduction is unavailable, compare available failing and passing evidence. Stop speculative patching when hypotheses remain indistinguishable. Report the next observation that would justify a change.

## Expected result

A supported root-cause account and a verified correction when implementation is in scope.

## Completion criteria

Report the original symptom, evidence for the cause, and same-path and regression results or their limitations.
