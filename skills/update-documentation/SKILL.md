---
name: update-documentation
description: Update Re_ product, technical, workflow, release, or onboarding documentation so it matches verified repository behavior. Use after implementation, architecture decisions, process changes, provider changes, or when template documentation is stale.
---

# Update documentation

## Inputs

- Changed behavior/diff, validation evidence, target audience and existing source of truth.

## Procedure

1. Identify the owning document; avoid creating a competing source of truth.
2. Verify commands, paths, configuration and screenshots against the current branch.
3. Separate approved facts, decisions, assumptions and future proposals.
4. Update only affected sections; link detailed evidence instead of duplicating it.
5. Include setup, environment, validation, operational and rollback implications when relevant.
6. Check links, examples, dates, locale terminology and consistency with brand/constitution.
7. Summarize documentation changed and unresolved owner inputs.

## Quality checklist

- A new contributor can execute documented commands.
- No secret, personal data or unapproved public claim is included.
- Template names/domains/examples are removed when obsolete.
- Status and last-verified context are clear.

## Expected output

A small documentation diff tied to the implementation, with verified examples and explicit open questions.

## Avoid

- Writing a changelog or extra README inside a skill.
- Copying the same business facts into many files.
- Documenting intended behavior as already implemented.

