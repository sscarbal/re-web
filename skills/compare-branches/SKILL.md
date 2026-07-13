---
name: compare-branches
description: Compare all local and remote Git branches for Re_ and recommend how to preserve or integrate their work. Use when selecting a base branch, reconciling divergent product/code work, reviewing stale branches, or planning safe merges.
---

# Compare branches

## Inputs

- Repository path, candidate target and permission to refresh remote refs.
- Dirty-worktree constraints and production/default branch context.

## Procedure

1. Read `AGENTS.md` and inspect status before any fetch or checkout.
2. Refresh refs when authorized; never equate stale local refs with remote truth.
3. Record commit, parent, date, tree ID, divergence and merge base for each branch.
4. Group names that point to identical trees.
5. Compare commit intent, changed files, directory stats, deletions, assets and configuration.
6. Test distinct application trees in isolated temporary directories; do not switch a dirty worktree.
7. Identify contained, superseded, complementary and conflicting work.
8. Recommend keep, integrate, archive-later or ignore, with a reversible sequence.

## Quality checklist

- Include local and remote-only branches.
- Detect invalid filenames, large blobs and untracked work.
- Distinguish documentation value from implementation readiness.
- Do not delete, merge, rebase, push or rename without approval.

## Expected output

A branch table, topology summary, verified best-base recommendation, integration order, conflict/risk notes and approval gates.

## Avoid

- Ranking by recency alone.
- Building several branch names that share one tree.
- Hiding checkout/build exclusions used during testing.

