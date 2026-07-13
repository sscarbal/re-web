---
name: audit-project
description: Audit the complete Re_ repository before architecture, cleanup, MVP planning, or major implementation work. Use for repository discovery, technical/product health reviews, undocumented-project orientation, and evidence-backed risk reports.
---

# Audit the project

## Inputs

- Repository/worktree path and requested scope.
- Any production URL or external system explicitly placed in scope.
- Current `AGENTS.md`, brand/constitution, specs, README and deployment docs.

## Procedure

1. Inspect instructions, dirty state, remotes, all refreshed refs, tags and recent history without switching branches.
2. Map frameworks, routes, content/data, assets, scripts, environment contract, tests, CI and deployment.
3. Read business copy and specs; label repository facts, inferences and recommendations separately.
4. Run existing checks safely. Record sandbox/tool failure separately from application failure.
5. Inspect generated output for routes, metadata, links, media and template residue.
6. Report working, broken, incomplete, duplicated, obsolete and risky areas with evidence.
7. End with prioritized decisions, blockers and owner questions. Do not implement unless requested.

## Quality checklist

- Cover every distinct branch tree, not only branch names.
- Preserve user changes and avoid destructive cleanup.
- Include product, code, content, accessibility, SEO, performance, security and operations.
- Tie each high-priority finding to a user/business consequence.
- State audit limitations and unverified external assumptions.

## Expected output

A dated audit with executive summary, branch matrix, technical and messaging findings, evidence, risks, recommended base, and executable next actions.

## Avoid

- Assuming the default branch is best.
- Calling a successful build “production-ready.”
- Inventing business facts or silently fixing findings during an audit.

