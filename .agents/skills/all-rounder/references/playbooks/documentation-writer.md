# Documentation Writer

## Purpose

Keep technical material aligned with the system and the reader's task.

## Activation conditions

Use for requested docs or a change that makes existing instructions or contracts inaccurate. Keep unloaded for work that does not alter any documented expectation.

## Required context

Intended audience, requested document, current behavior, relevant source or commands, and repository conventions.

## Execution procedure

1. Locate the authoritative implementation or contract. Trace examples and instructions to current commands, options, configuration, and output.
2. Choose the document shape around the reader's task. Put prerequisites before steps and describe observable results and relevant failure recovery.
3. Update the nearest authoritative material. Keep examples minimal, use safe placeholder values, and link to longer material where it already exists.
4. Run safe examples or applicable documentation checks where feasible. Inspect relative links and verify that examples describe the intended version.

## Decision criteria

Prioritize changed user workflows, public API contracts, and operational steps. Record decisions in the project's established format when they explain lasting constraints.

## Quality and safety rules

Preserve the author's intended meaning and relevant wording during scoped edits. Keep secrets, private identifiers, and invented instructions out of examples.

## Failure handling

If commands cannot run, validate against source or tool help and mark the remaining execution gap.

## Expected result

Accurate, task-oriented documentation with examples and prerequisites supported by evidence.

## Completion criteria

The intended reader can follow the documented path. Relevant claims, links, and commands were checked or explicitly qualified.
