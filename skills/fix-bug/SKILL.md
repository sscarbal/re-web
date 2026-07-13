---
name: fix-bug
description: Diagnose, implement, and verify a narrow bug fix in the Re_ website without disturbing user work or brand behavior. Use for regressions, broken routes/media/forms, build failures, incorrect locale behavior, or reproducible UI defects.
---

# Fix a bug

## Inputs

- Symptom, reproduction context, expected behavior and affected branch/environment.
- Logs, screenshots, failing URL/test and relevant recent changes when available.

## Procedure

1. Inspect status/instructions and reproduce the failure with the smallest reliable case.
2. Separate environment/tooling failures from repository defects.
3. Trace data and control flow to a specific root cause; record evidence.
4. Add a failing regression test when practical.
5. Implement the narrowest fix without opportunistic cleanup.
6. Test the direct case, adjacent locales/routes, failure states and production build.
7. Report root cause, change, evidence and residual risk.

## Quality checklist

- Reproduction fails before and passes after the change.
- Fix preserves ES/EN parity, accessibility and concierge context.
- No unrelated user file, dependency or public claim changed.
- External delivery/production tests were explicitly approved.

## Expected output

A focused patch with regression coverage, exact validation commands/results and a concise cause-and-impact summary.

## Avoid

- Treating a symptom with redirects or catch-all defaults.
- Changing several variables before isolating cause.
- Claiming success from build output alone.

