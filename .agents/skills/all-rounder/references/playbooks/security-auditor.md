# Security Auditor

## Purpose

Assess application security controls and recommend defensible remediation.

## Activation conditions

Use for a defensive security review, material changes to trust boundaries, or diagnosis of suspected vulnerable code. Use ordinary Code Review when no material security boundary is implicated.

## Required context

Authorized scope, revision and environments, identities and roles, sensitive data, trust boundaries, and existing controls or tests.

## Execution procedure

1. Map entry points, trust boundaries, sensitive flows, and the expected permissions for each actor and resource. Separate authentication, object authorization, tenant isolation, and field-level access.
2. Trace where the server enforces controls on relevant reads and writes. Check object and tenant scope, validation and encoding, secret storage, and fail-closed defaults. Inspect relevant dependency versions and reachability when dependency exposure is in scope.
3. Consult the relevant requirements in [OWASP ASVS](https://asvs.owasp.org/) when authoritative guidance is needed. Limit the assessment to supported evidence and the authorized scope.
4. Verify remediations at the real enforcement boundary using ordinary, non-sensitive allow and deny fixtures. Confirm that denied requests produce no protected output or state change. Review fail-closed behavior when dependencies or policy checks fail.
5. Report affected controls, consequences, code locations, confidence, and prioritized fixes. Identify which controls require additional configuration or test evidence.

## Decision criteria

Consider whether the path is reachable, which identities can reach it, and what data or state is affected. Keep blockers and evidence gaps distinct from confirmed findings.

## Quality and safety rules

Limit work to defensive inspection, remediation, and safe control verification. Exclude exploit creation, vulnerability reproduction, intrusion, and autonomous offensive testing. Explain whether an affected dependency feature is reachable when evidence is available.

## Failure handling

If configuration or runtime controls are unavailable, describe findings as static or conditional and ask only for the minimum sanitized evidence needed.

## Expected result

A scoped assessment with evidence, remediation, and safe verification criteria.

## Completion criteria

Relevant trust boundaries and control checks are accounted for. Each finding has evidence and a fix or mitigation, with review limits identified.
