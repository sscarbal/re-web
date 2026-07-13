# Re\_ repository agent instructions

These instructions apply to the whole repository.

## Read before changing code

1. Read `context/the_brand.md` and `context/constitution.md` when they are present on the working branch.
2. Read `docs/agent-workflow/README.md` and the relevant repository skill in `skills/`.
3. Inspect `git status --short --branch`, the active branch, and nearby files before editing.
4. Preserve user changes. Do not switch branches, delete files, rewrite history, or run deployment scripts without explicit approval.

## Product guardrails

- Build the Concierge MVP: a premium bilingual catalog that routes qualified product and education inquiries to one reliable contact flow.
- Keep Re\_'s evidence-backed concepts intact: Método Re\_, made-to-order production, contemporary craft, real traceability, quiet luxury, and the Sevilla workshop.
- Do not invent prices, lead times, material origins, credentials, availability, environmental claims, or customer proof.
- Prefer Spanish and English parity. A route or call to action is not complete until both locales work.
- Avoid checkout, accounts, databases, booking engines, digital passports, LMS features, and custom MCP servers unless a reviewed task explicitly adds them.

## Engineering guardrails

- Prefer semantic Astro rendered at build time. Add client JavaScript only for behavior that cannot be delivered with HTML/CSS.
- Every public page needs a unique title, description, canonical URL, language alternate links, one clear `h1`, keyboard-safe navigation, descriptive image alternatives, and a path to the concierge form.
- Use small branches named `codex/<task-id>-<slug>` after the base branch is approved.
- Use focused Conventional Commits such as `fix(i18n): preserve locale on product links`.
- Run the checks relevant to the change. The target MVP gate is `npm run validate`; until it exists, run at least a clean build and document missing checks.
- Report assumptions, files changed, validation evidence, residual risks, and any required human follow-up.

## Approval gates

Obtain human approval before changing the production domain or inbox, selecting a form/analytics/hosting provider, publishing brand copy as fact, adding paid services, moving or deleting branches, deleting media, changing privacy/legal text, deploying, or sending external messages.

