---
name: prepare-deployment
description: Assess and prepare a Re_ branch for preview or production deployment with reproducible checks, environment validation, form delivery evidence, and rollback planning. Use for release readiness, hosting configuration, domain changes, or launch rehearsals; never deploy unless explicitly authorized.
---

# Prepare deployment

## Inputs

- Approved release branch/commit, target environment and hosting/domain owners.
- Environment-variable contract, form provider, production inbox and release criteria.

## Procedure

1. Confirm clean scope, reviewed commits and no secrets/generated analyzer/raw media in the diff.
2. Reproduce the Node 20 clean install and full validation gate.
3. Validate environment separation, public/secret variables, domain/canonical URLs and provider quotas.
4. Create or inspect a preview deployment only when authorized.
5. Smoke test ES/EN routes, media, metadata, 404, form intents, success/error behavior and external delivery.
6. Check privacy/legal approval, monitoring, DNS, cache, security headers and rollback steps.
7. Produce a go/no-go report. Promote production only with explicit approval.

## Quality checklist

- Release commit is identifiable and reversible.
- Form deliverability is tested end to end, not inferred.
- Preview and production secrets/domains are not mixed.
- Known advisories and third-party risks have recorded disposition.

## Expected output

A signed-off checklist, validation evidence, preview reference, blockers, rollback plan and explicit production approval request.

## Avoid

- Running the legacy auto-deploy script.
- Editing DNS, secrets or production settings during a read-only review.
- Declaring go from a local build alone.

