# All-rounder Skill

All-rounder is a portable [Agent Skill](https://agentskills.io/specification) that gives coding agents a repeatable workflow for planning, building, debugging, reviewing, and releasing software. It helps the agent decide what to inspect, which changes are in scope, and what evidence to collect before calling the work complete.

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
| Fix a bug | Investigate why blank rows crash CSV imports. Add a regression test and report which checks ran. |
| Review a change | Review the billing changes for defects and missing tests. Cite the relevant files and leave the code as-is. |
| Assess release readiness | Check whether the current billing release candidate is ready. Verify CI evidence, migration risks, and recovery steps. Keep the assessment read-only. |

## How it works

The [entrypoint](.agents/skills/all-rounder/SKILL.md) chooses an execution mode based on the task’s complexity and impact.

- **Lightweight** keeps small, reversible work focused.
- **Standard** traces dependencies and verifies changes at affected boundaries.
- **High Assurance** adds explicit permission checks, stronger verification, and recovery planning where appropriate.

The skill uses [playbook routing](.agents/skills/all-rounder/references/routing.md) to select from 16 playbooks covering planning, architecture, codebase analysis, development, frontend design, databases, debugging, testing, code review, security, performance, browser testing, Git, deployment, documentation, and handoffs. It loads supporting playbooks when their guidance is needed.

Shared references cover [quality gates](.agents/skills/all-rounder/references/quality-gates.md), [permissions and risk](.agents/skills/all-rounder/references/risk-policy.md), [tool fallbacks](.agents/skills/all-rounder/references/capability-fallbacks.md), and [reporting evidence](.agents/skills/all-rounder/references/evidence-contract.md).

## Verification

- The skill passed frontmatter, package structure, and internal link checks.
- Codex discovered it as an enabled project skill. An independent evaluator manually loaded it for three read-only scenarios covering code explanation, authorization review, and release readiness.
- Automatic activation in Codex and discovery or activation in the other listed agents remain untested. The installation paths above come from each agent’s documentation.

## License

[Apache License 2.0](LICENSE)
