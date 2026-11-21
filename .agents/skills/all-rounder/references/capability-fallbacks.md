# Capability fallbacks

Check capabilities at the point they become necessary. Distinguish whether a tool is available, whether the target is reachable, and whether its use on that target is authorized. Respect host restrictions and prefer lower-impact ways to obtain the same evidence.

| Missing capability | Continue with | Evidence still needed |
| --- | --- | --- |
| Filesystem or repository search | Use supplied tree, manifests, diffs, or excerpts. Inspect caller and callee snippets. | Full path, revision, and surrounding behavior that could change the conclusion. |
| Terminal or test runner | Review tests and expected outputs. Run a narrower available check when possible. | The relevant check in the expected environment. |
| Git or remote access | Review supplied patches and local files and preserve current edits. | Index, history, upstream, or remote state that could not be observed. |
| Browser or running preview | Inspect component markup, styles, and existing tests. | Rendered flows, viewport behavior, accessibility interactions, or runtime errors. |
| Network or external docs | Use installed versions, repository docs, or supplied excerpts. | Current version, API, documentation, or service behavior where material. |
| Database or representative data | Review schema, queries, and migration order statically. | Actual plans, integrity and role checks, locking, and recovery where applicable. |
| CI, deployment integration, or production visibility | Inspect build and release config, run available local checks, and define smoke and recovery steps. | Observed CI, release, and health outcomes in the target environment. |

State the missing capability and which conclusion it limits. Include the exact command, input, environment, or observation needed to close the gap when known. Reuse this information through the completion report.
