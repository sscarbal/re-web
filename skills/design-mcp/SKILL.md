---
name: design-mcp
description: Evaluate and design an MCP integration for Re_ only when a recurring external-system workflow cannot be solved well with repository docs, scripts, CI, or an existing connector. Use for MCP proposals, permission models, tool/resource schemas, risk review, or build-versus-simpler-alternative decisions.
---

# Design an MCP

## Inputs

- Repeated workflow, users, external system/API, frequency, failure cost and current manual process.

## Procedure

1. Define the concrete workflow problem and measurable time/error cost.
2. Test simpler alternatives: Markdown/resources, deterministic script, CI job, provider CLI/API, existing connector or ordinary application code.
3. If MCP remains justified, define read-only resources first, then minimal tools and schemas.
4. Specify authentication, least privilege, consent boundaries, audit logs, rate limits, secret storage and data retention.
5. Separate read, write and destructive capabilities; require explicit confirmation for external mutations.
6. Estimate implementation, hosting, maintenance, testing and incident ownership.
7. Recommend build now, pilot later or do not build, with a revisit trigger.

## Quality checklist

- Every tool maps to a real repeated task and named owner.
- Customer data and production writes are minimized.
- Failure/retry/idempotency and revocation behavior are defined.
- MVP value exceeds custom infrastructure cost.

## Expected output

A problem statement, alternatives analysis, resource/tool catalog, permission/risk model, complexity estimate and clear recommendation.

## Avoid

- Creating repository-knowledge or brand MCPs when versioned docs suffice.
- One broad “admin” tool.
- Building before the underlying manual workflow stabilizes.

