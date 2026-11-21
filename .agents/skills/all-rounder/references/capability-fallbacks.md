# Capability fallbacks

Check capabilities at the point they become necessary. Distinguish whether a tool is available, whether the target is reachable, and whether its use on that target is authorized. Respect host restrictions and prefer lower-impact ways to obtain the same evidence.

| Missing capability | Continue with | Evidence still needed |
| --- | --- | --- |
| Filesystem or repository search | Use supplied tree, manifests, diffs, or excerpts. Inspect caller and callee snippets. | Full path, revision, and surrounding behavior that could change the conclusion. |
| Terminal or test runner | Inspect test entry points and assertions. Use an available smaller check when it can answer a specific question. | The named test result in the intended runtime. |
| Git or remote access | Review supplied patches and local files and preserve current edits. | Index, history, upstream, or remote state that could not be observed. |
| Browser or running preview | Inspect component markup, styles, and existing tests. | Rendered flows, viewport behavior, accessibility interactions, or runtime errors. |
| Network or external docs | Use installed versions, repository docs, or supplied excerpts. | Current version, API, documentation, or service behavior where material. |
| Database or representative data | Review schema, queries, and migration order. Use supplied plans only when their provenance fits the question. | Execution plans, integrity and role checks, locking, and recovery where applicable. |
| CI, deployment integration, or production visibility | Inspect build and release config, run available local checks, and define smoke and recovery steps. | Observed CI, release, and health outcomes in the target environment. |

State the missing capability and which conclusion it limits. Report a static inspection separately from any runtime check it could not replace. If a safe substitute is possible, name the difference in boundary or environment. Include the smallest command, input, or observation needed to close the gap when known.
