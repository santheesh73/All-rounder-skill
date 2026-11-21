# Evidence contract

Report the requested outcome and what was achieved. Describe changes with paths or symbols where they help the user verify the work. For reviews, lead with supported findings ordered by impact. For analysis, distinguish observations from inferences and name assumptions that change the result.

Name the check or inspection, relevant environment or revision, and observed result. Use the quality-gate statuses for material gaps. Attribute behavior claims to the inputs and boundary actually checked. For example, explicitly supplying a null value leaves argument omission unverified.

| Outcome | Evidence to include when material |
| --- | --- |
| Implementation | Changed behavior and paths, checks that ran, open failures or unavailable checks, and any remaining risk. |
| Review | Severity, location, triggering condition, consequence, and suggested correction. Mark conditional observations and identify the evidence they need. |
| Analysis or handoff | Observed state, supported conclusions, assumptions, and uncertainty tied to the current revision. |
| Performance | Baseline, changed condition, comparable measurements, variability, and correctness results. |
| Release readiness | Candidate and target, matching check evidence, unmet release conditions, and recovery concerns. Record live outcomes only for actual authorized execution. |

Describe limitations and remaining risks that affect acceptance or a release decision. Give a next action only when it resolves a real ambiguity, verification gap, or blocker. For a small task, keep this to the outcome, evidence, and any material gap.

Support claims at the level of detail they imply. A subset of checks establishes that subset's result. Quantified performance changes require comparable measurements. Deployment claims require the observed target and health result. Security and readiness conclusions need a stated scope and supporting checks. Exclude secrets and private payloads from examples and evidence.
