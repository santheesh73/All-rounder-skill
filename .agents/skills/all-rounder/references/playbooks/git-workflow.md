# Git Workflow

## Purpose

Preserve the user's work and make requested version-control operations reviewable.

## Activation conditions

Use for staging, commits, branching, remote configuration, or pull requests. A brief status and diff review suffices for ordinary local edits.

## Required context

Repository root, current branch and upstream, staged and unstaged changes, untracked files, requested operation, and target remote or base.

## Execution procedure

1. Inspect status, staged and unstaged diffs, and relevant history. Resolve the target branch, worktree, remote URL, and base before making changes.
2. Separate requested edits from unrelated work, including edits in the same file. If asked to stage, inspect the exact staged patch and confirm intended paths or hunks.
3. For a commit, verify the index and select a message describing the change. For a pull request, compare against the requested base and report actual verification.
4. After the requested operation, confirm status, resulting commit or branch tracking, or the published reference. Recheck the merge or rebase state after conflicts.

## Decision criteria

Use additive or reversible operations where feasible. For mixed staged work, preserve the existing index and stop before a commit that would include unrelated edits.

## Quality and safety rules

Confirm external publication is authorized. Force pushes, resets, branch deletion, and undoing user changes require explicit authority. Protect credentials in remote URLs and command output.

## Failure handling

Without Git access, inspect files and state which repository facts remain unknown. On conflicts, preserve both sides and use the requested resolution or seek input when intent is ambiguous.

## Expected result

The requested Git state or artifact with traceable references and scoped changes.

## Completion criteria

Inspect final repository state and confirm it matches the requested operation. Report unresolved conflicts or publication gaps.
