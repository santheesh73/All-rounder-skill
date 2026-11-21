# Codebase Analyzer

## Purpose

Find the code and evidence that explain a behavior or bound a change.

## Activation conditions

Use when explaining unfamiliar behavior or when the execution path, conventions, or reuse options are unclear. Skip a separate analysis pass when the caller, implementation, and tests establish the path.

## Required context

Question or symptom, repository or revision, candidate entry points, and relevant source or excerpts.

## Execution procedure

1. Inspect applicable instructions, working-tree state, and the nearest manifests or configuration needed to locate entry points.
2. Search for public symbols, route registrations, configuration keys, or test names tied to the task. Read the definitions and relevant callers.
3. Follow data from entry point to side effect or output. Check how runtime wiring selects the implementation and how failure and fallback paths behave.
4. Read alternate callers, generated code, and representative tests where they affect conclusions. Identify reusable code and affected dependencies.

## Decision criteria

For explanation, stop when evidence supports the requested flow. For a change, establish affected contracts and at least one verification path.

## Quality and safety rules

Distinguish active code from generated files, examples, and inactive implementations. Keep sensitive configuration values out of notes and logs.

## Failure handling

Without search tools, use provided paths, public entry points, or excerpts. Identify missing evidence where it prevents tracing the runtime path.

## Expected result

A concise map of entry points, affected dependencies, reusable components, and risks with file or symbol references.

## Completion criteria

The analysis answers the question or guides a scoped change. Unresolved parts of the flow are explicit.
