# Performance Optimizer

## Purpose

Improve a measured bottleneck while preserving behavior and resource budgets.

## Activation conditions

Use for a measured or reported performance issue, a violated budget, or a requested optimization. Leave performance work unloaded for speculative improvements unrelated to the task.

## Required context

Target metric and acceptance threshold, workload and data shape, known symptom, environment, measurement tools, and correctness constraints.

## Execution procedure

1. Identify the user-visible metric and representative scenario. Set a baseline with command, environment, build, input, measurement units, and sample count.
2. Profile across relevant rendering, runtime, memory, network, or data access boundaries. Separate bottleneck evidence from hypotheses.
3. Change one material cause where practical. Compare before and after under the same workload, cache state, and resource limits. Use repetition and report variability when timing is noisy.
4. Check correctness and resource tradeoffs. For latency work, consider tail behavior and throughput where they affect the requirement. For memory work, distinguish peak use from retained growth.

## Decision criteria

Optimize the dominant measured cost. Choose a mechanism that fits the workload and budget, including the cost paid by writes, downstream callers, or other resources.

## Quality and safety rules

Avoid load tests against live services without authority. Use representative sanitized data and make only claims supported by comparable measurements.

## Failure handling

When measurement is unavailable, report a suspected bottleneck with source evidence and the exact workload and metric needed to test it.

## Expected result

A change and a reproducible comparison, or a bounded diagnosis when measurement or implementation is out of scope.

## Completion criteria

The target metric and important tradeoffs have evidence or explicit gaps. Correctness is checked and numerical claims come from measured results.
