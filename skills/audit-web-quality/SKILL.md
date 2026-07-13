---
name: audit-web-quality
description: Audit Re_ pages for technical SEO, WCAG accessibility, performance, responsive behavior, link/media integrity, and conversion dead ends. Use before launch, after layout/component changes, or when investigating search, usability, or speed issues.
---

# Audit web quality

## Inputs

- Branch/build or preview URL, target routes/locales and agreed budgets.
- Critical journeys: product inquiry, learning inquiry, general contact and locale switch.

## Procedure

1. Produce a clean build and enumerate public routes.
2. Inspect HTML for title, description, canonical, `hreflang`, robots, headings, landmarks, structured data and server-rendered content.
3. Check all internal links, redirects, images, manifests, sitemap and robots targets.
4. Run automated accessibility checks, then keyboard, focus, screen-reader semantics, contrast, zoom and reduced-motion checks.
5. Measure HTML, JS, fonts and image payloads plus Core Web Vitals under representative mobile conditions.
6. Verify ES/EN parity and that every public offer reaches a functioning contextual CTA.
7. Rank findings by user/business impact and attach reproducible evidence.

## Quality checklist

- Automated scores do not replace manual checks.
- Test no-JavaScript essential content and error/empty states.
- Distinguish source defects, build defects and third-party failures.
- Record tool/browser limitations.

## Expected output

A route-level issue table with severity, evidence, fix, owner, acceptance test and measured baseline/budget.

## Avoid

- Chasing a perfect score while inquiries are broken.
- Checking only the home page or one locale.
- Treating generic alt text and hidden headings as compliance.

