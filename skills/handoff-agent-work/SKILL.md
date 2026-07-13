---
name: handoff-agent-work
description: Create a precise handoff for ongoing Re_ repository work. Use when another agent or human will continue a task, when a change is partially complete, at a pull request boundary, or before stopping with unresolved risks.
---

# Hand off agent work

## Inputs

- Objective, branch/base, current status, diff/commits, validation output and unresolved decisions.

## Procedure

1. State the achieved outcome before process detail.
2. Record branch, base commit, relevant commits and dirty/untracked state.
3. List files changed and why; identify user changes that were deliberately untouched.
4. Include exact commands/tests and their pass, fail or not-run status.
5. Record facts, assumptions, decisions, residual risks and approval gates.
6. Give the next agent one ordered starting point and concrete completion criteria.
7. Link the controlling issue/spec/docs and preview or screenshots when applicable.

## Quality checklist

- The receiver does not need hidden chat context.
- No claim says complete while required work remains.
- Failures include enough evidence to reproduce.
- External actions and approvals are explicit.

## Expected output

A compact standalone handoff with outcome, state, evidence, remaining work and next action.

## Avoid

- Narrative diary entries.
- Omitting dirty files, failed tests or unapproved assumptions.
- Sending the receiver back to rediscover branch topology.

