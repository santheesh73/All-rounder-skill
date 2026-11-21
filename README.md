# All-rounder Skill

All-rounder gives coding agents a repeatable workflow for planning, building, debugging, reviewing, and releasing software. It helps the agent choose the right depth of investigation, keep changes in scope, and gather evidence for the result. [Agent Skills specification](https://agentskills.io/specification)

## Quick start with Codex

Clone this repository and open it as a Codex project. The skill is already in the project’s `.agents/skills/` directory. [Codex skill discovery docs](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills)

```sh
git clone https://github.com/santheesh73/All-rounder-skill.git
```

From a Codex session opened in the cloned repository, use this prompt:

```text
$all-rounder Review this repository and explain how the skill selects playbooks. Do not edit files.
```

## Install in another project

Copy the entire [`all-rounder` folder](.agents/skills/all-rounder/) so that `SKILL.md` is at the path shown below, relative to your **target project root**. Keep `SKILL.md` and `references/` together. Start a session in the target project and follow your agent’s guide to use `all-rounder`.

| Coding agent | Project path for `SKILL.md` | Setup guide |
| --- | --- | --- |
| Codex | `.agents/skills/all-rounder/SKILL.md` | [Codex](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills) |
| Claude Code | `.claude/skills/all-rounder/SKILL.md` | [Claude Code](https://code.claude.com/docs/en/skills#choose-where-skills-load) |
| Cursor | `.agents/skills/all-rounder/SKILL.md` | [Cursor](https://cursor.com/docs/skills#skill-directories) |
| Gemini CLI | `.agents/skills/all-rounder/SKILL.md` | [Gemini CLI](https://geminicli.com/docs/cli/skills/#discovery-tiers) |
| GitHub Copilot | `.agents/skills/all-rounder/SKILL.md` | [GitHub Copilot](https://docs.github.com/en/copilot/concepts/customizations/agent-skills#finding-and-storing-skills) |
| OpenCode | `.agents/skills/all-rounder/SKILL.md` | [OpenCode](https://opencode.ai/docs/skills/#discovery) |
| Google Antigravity | `.agents/skills/all-rounder/SKILL.md` | [Google Antigravity](https://antigravity.google/docs/skills) |

For another Agent Skills-compatible host, place the same folder in its documented skill directory. The package consists of Markdown instructions and references and uses the tools and permissions available in the host.

## What you can ask it to do

| Task | Example prompt after invoking the skill |
| --- | --- |
| Plan a feature | Plan a CSV import feature. Identify acceptance criteria, dependencies, and how failed rows should be reported. |
| Analyze a codebase | Trace invoice export from its endpoint to the queue and worker. Identify where retries are configured and what remains unknown. |
| Implement a feature | Add per-row errors to CSV imports. Preserve the existing response for successful imports and verify both paths. |
| Fix a bug | Investigate why blank rows crash CSV imports. Add a regression test and report which checks ran. |
| Review a change | Review the billing changes for defects and missing tests. Cite the relevant files and leave the code as-is. |
| Assess release readiness | Check whether the current billing release candidate is ready. Verify CI evidence, migration risks, and recovery steps. Keep the assessment read-only. |

## How it works

The [entrypoint](.agents/skills/all-rounder/SKILL.md) chooses an execution mode based on the task’s complexity and impact.

- **Lightweight** keeps small, reversible work focused.
- **Standard** traces dependencies and verifies changes at affected boundaries.
- **High Assurance** adds explicit permission checks, stronger verification, and recovery planning where appropriate.

The skill selects a primary playbook for the requested decision and loads supporting guidance when it adds a distinct check or procedure. Small, well-understood edits can use the Lightweight workflow directly. If a specialist already covers the task, All-rounder adds guidance only for a separate decision or verification gap. [Playbook routing](.agents/skills/all-rounder/references/routing.md)

Shared references define checks proportionate to the task, permission boundaries, alternatives for missing tools, and what counts as evidence. [Quality gates](.agents/skills/all-rounder/references/quality-gates.md) · [Permissions and risk](.agents/skills/all-rounder/references/risk-policy.md) · [Tool fallbacks](.agents/skills/all-rounder/references/capability-fallbacks.md) · [Evidence contract](.agents/skills/all-rounder/references/evidence-contract.md)

## Capabilities

| Area | Playbooks |
| --- | --- |
| Plan and understand | Project Planner orders work around acceptance criteria. Software Architect defines boundaries and tradeoffs. Codebase Analyzer traces existing behavior. Context Manager reconciles decisions and handoff evidence. |
| Build | Full-Stack Development implements feature slices. Frontend Design handles layout and interaction. Database Engineer protects data and migration invariants. Documentation Writer verifies technical instructions against their source. |
| Diagnose and verify | Systematic Debugging isolates causes. Test-Driven Development selects regression and contract checks. Browser Testing exercises rendered journeys. Performance Optimizer compares measurements under matched conditions. |
| Review and deliver | Code Review finds actionable defects. Security Auditor assesses defensive controls. Git Workflow scopes branch and commit operations. Deployment Engineer verifies release and recovery conditions. |

## Repository structure

```text
.
├── README.md
├── LICENSE
└── .agents/skills/all-rounder/
    ├── SKILL.md
    └── references/
        ├── playbooks/                # 16 engineering playbooks
        ├── routing.md
        ├── quality-gates.md
        ├── risk-policy.md
        ├── capability-fallbacks.md
        ├── evidence-contract.md
        └── validation-scenarios.md
```

This repository ships one portable, instruction-based Agent Skill. File access, test execution, browser and service checks, and permissions depend on the host and project.

## Compatibility and verification

The evaluation pairs skill-disabled and explicitly invoked sessions on disposable fixtures. Both use the same prompt, starting files, tools, and acceptance checks. Separate automatic runs record which references the host reads. [Validation protocol and results](.agents/skills/all-rounder/references/validation-scenarios.md)

- **Specification compatible.** The skill passed frontmatter, package structure, and internal link checks. [Agent Skills specification](https://agentskills.io/specification)
- **Codex.** Project discovery, explicit invocation, and automatic activation were observed in isolated app-server sessions. Five migration-sensitive release variants loaded both expected playbooks. The docs-only control skipped Database Engineer. The record retains an initial feature-slice and test-coverage misroute and the passing reruns.
- **OpenCode.** CLI discovery was verified in isolated projects. Two model requests timed out before activation could be verified.
- **Other listed agents.** The setup paths are documented by their vendors. Runtime discovery and activation remain untested.
- **Behavioral evaluation.** Independent evaluators reviewed 26 read-only cases. Both arms eventually passed all six coding fixtures, including SQLite and a headless Edge interaction. The CSV baseline initially timed out and passed on a fresh run. The sample shows no consistent correctness, token, or speed advantage.

If standalone Windows Codex cannot start its shell, run `codex doctor` to check sandbox provisioning. After host repair, confirm that Codex can read a plain project file before rerunning the skill tests. [Codex Windows sandbox troubleshooting](https://learn.chatgpt.com/docs/windows/windows-sandbox#troubleshooting-and-faq)

## License

[Apache License 2.0](LICENSE)
