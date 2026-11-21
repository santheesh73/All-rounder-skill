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
3. Choose browsers and viewports from the support matrix and affected layout modes. Check keyboard order, focus, labels, errors, and regressions along the primary journey. Capture relevant console and network failures with sensitive details removed.
4. Collect evidence only when it adds value. For failures, record build, browser, viewport, preconditions, steps, expected result, and observed result.

## Decision criteria

Prioritize the user path affected by the change and boundary states likely to break. Use at least one viewport per affected layout mode when feasible.

## Quality and safety rules

Use disposable accounts or fixtures for writes. Avoid real purchases, messages, or destructive submissions without applicable authorization. Redact artifacts before sharing.

## Failure handling

If a browser is unavailable, report the rendered journey as unavailable. Record separately any static or component results, plus the browser, viewport, inputs, and interactions still needed.

## Expected result

A browser check report with the actual journey, environment, observations, and useful evidence.

## Completion criteria

Each applicable journey has a result or explicit gap, and failures have enough detail to reproduce safely.
