# Agent workflow for Re\_

## Objective

Enable small, reviewable changes that improve launchability without losing user work, weakening the business message, or automating decisions that belong to the founder.

## 1. Inspect before editing

1. Read the nearest `AGENTS.md`.
2. Inspect `git status --short --branch`, branches relevant to the task, and recent commits.
3. Read `context/the_brand.md`, `context/constitution.md`, the applicable feature spec, and the files being changed.
4. Run or inspect the current validation baseline. Record environmental failures separately from product failures.
5. State facts, assumptions and the smallest intended change.

Do not switch branches in a dirty worktree. Use a separate worktree or wait for a human disposition if isolation is required.

## 2. Plan the change

- Define user/business outcome, scope, non-goals, likely files, risks and acceptance checks.
- Prefer one independently testable vertical slice.
- Surface missing founder input instead of inventing content, pricing, timing or claims.
- Request approval before provider choices, paid services, external writes, production actions, destructive cleanup, legal/privacy changes or significant scope expansion.

## 3. Branch and commit discipline

- Start from the human-approved integration branch.
- Use `codex/<task-id>-<short-slug>`.
- Keep unrelated user changes out of the branch.
- Use focused Conventional Commits: `type(scope): outcome`.
- Do not rewrite shared history or delete branches without explicit approval.

## 4. Implementation rules

- Preserve ES/EN parity and same-subject locale navigation.
- Keep business copy grounded in approved repository evidence.
- Prefer semantic static Astro and progressive enhancement.
- Treat every public page as a conversion path: no product/service dead end without a concierge CTA.
- Keep dependencies and abstractions proportional to the Concierge MVP.
- Never put secrets or customer data in source, URLs, fixtures, logs or screenshots.

## 5. Validation

Target command after the quality task is implemented:

```text
npm ci
npm run validate
```

Until then, document which of these were available and run the relevant subset:

- type/content schema check;
- lint/format check;
- production build;
- unit tests for helpers and form mapping;
- link and asset existence test;
- browser smoke tests for ES/EN navigation and all form intents;
- automated plus manual accessibility checks;
- performance budgets on representative mobile settings;
- form deliverability test only with explicit external-action approval.

Never report “tests pass” when only the build ran.

## 6. Documentation and handoff

Update the source of truth in the same change. A handoff or PR summary must include:

- outcome and business reason;
- branch/base and commits;
- files changed;
- validation commands and exact results;
- screenshots or preview URL for visual work;
- assumptions and decisions;
- known risks and follow-ups;
- explicit human approvals still required.

## 7. Risky decisions

Stop and request direction when the answer changes public facts, product scope, production data, external services, costs, privacy, legal terms, domains, inboxes, branch history or irreversible asset handling. Offer a concrete recommendation and reversible alternatives.

## 8. Pull request checklist

- Scope matches one backlog item or an explicitly linked group.
- Diff contains no unrelated user work, secrets, generated analyzer report or raw media.
- ES and EN behavior are equivalent.
- Business claims are sourced/approved.
- Acceptance criteria and validation evidence are present.
- Accessibility, SEO and performance impact is stated.
- Deployment/rollback impact is stated.
- Remaining approval gates are visible.

