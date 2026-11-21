# Browser Testing

## Purpose

Verify the requested UI behavior in a real browser when available.

## Activation conditions

Use for critical UI journeys, responsive or interactive changes, and reported browser failures. Keep unloaded for tasks whose acceptance is entirely outside the browser.

## Required context

Approved URL or local preview command, representative roles and fixtures, critical journeys, supported browsers and viewports, and permitted side effects.

## Execution procedure

1. Identify the acceptance flows and relevant states. Confirm environment, account, and data before using controls that write or submit.
2. Use existing browser tooling. Exercise navigation, forms, validation, and failure or recovery flows through visible controls with representative data.
3. Check narrow and wide layouts, keyboard order, focus, labels, and other applicable accessibility behavior. Capture relevant console and network errors without secrets or private payloads.
4. Collect evidence only when it adds value. For failures, record build, browser, viewport, preconditions, steps, expected result, and observed result.

## Decision criteria

Prioritize the user path affected by the change and boundary states likely to break. Use at least one viewport per affected layout mode when feasible.

## Quality and safety rules

Use disposable accounts or fixtures for writes. Avoid real purchases, messages, or destructive submissions without applicable authorization. Redact artifacts before sharing.

## Failure handling

If a browser is unavailable, use relevant component or static checks and describe the manual flows, inputs, and viewports still required.

## Expected result

A browser check report with the actual journey, environment, observations, and useful evidence.

## Completion criteria

Each applicable journey has a result or explicit gap, and failures have enough detail to reproduce safely.
