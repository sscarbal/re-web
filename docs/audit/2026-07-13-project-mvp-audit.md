# Re\_ website: project audit and MVP execution plan

**Audit date:** 2026-07-13  
**Repository:** `sscarbal/re-web`  
**Audit mode:** Read-only discovery followed by new documentation and draft skills; no application code, branch, or existing content was changed.

## 1. Executive summary

The repository contains two valuable but disconnected bodies of work:

- `origin/my-photos` is the strongest implementation branch. It replaces most demo portfolios with Re\_ imagery, adds Saco, Sandal, Costura and Zurda content records, introduces Re\_ logos, and reduces the locale set to English and Spanish.
- `feat/context-and-specs` is the strongest product-knowledge branch. It defines the brand, Concierge MVP, seven active feature specifications, and five future product concepts, but contains no Re\_ website implementation.

No branch is production-ready. The best implementation still presents template copy, placeholder product descriptions, the wrong domain and inbox, no real contact form, no training/service pages, broken locale navigation, missing Zurda media, inaccessible client-only product images, invalid Windows filenames, and current dependency advisories. The current `master` is only the upstream portfolio template and should not be selected as the MVP base by default.

The fastest route to launch is to create an approved integration branch from `origin/my-photos`, bring in the product context without overwriting the dirty working tree, remove template-specific behavior, implement a static Spanish/English content model and a single context-aware inquiry form, then add automated build/link/accessibility gates and deploy a preview for human copy, media, legal, and deliverability approval.

### Evidence-based business understanding

**Fact:** Re\_ was founded by Bárbara León in 2019 and operates from a workshop in Sevilla. Its proprietary Método Re\_ deconstructs discarded footwear, classifies components, and reassembles them into new material through patchwork and circular-pattern techniques.

**Fact:** The documented business has three pillars: made-to-order consumer products, concept-store partnerships, and education/academic services.

**Inference:** The website's primary near-term job is not e-commerce. It is to make the value of the method and the pieces legible, establish trust, and generate qualified inquiries that Bárbara can handle personally.

**Primary risk:** The current implementation looks like a photography-template adaptation rather than the digital expression of the documented business. A successful build currently hides broken product journeys rather than proving launch readiness.

## 2. Discovery and branch audit

Remote references were refreshed with `git fetch --all --prune` before comparison. Six branch names resolve to five distinct trees; the two local feature branches are identical.

| Branch | Inferred purpose and important changes | State / evidence | Recommendation | Next action |
|---|---|---|---|---|
| `master` / `origin/master` | Upstream Astro design/photography portfolio template | Builds 54 pages; four demo locales; unrelated portfolios, domain, author, email and redirects | Preserve as historical upstream base; do not use directly for MVP | Keep until the integration branch is accepted |
| `origin/feat/context-and-specs` | Initial Re\_ brand, constitution, content workflow, 7 active specs and 5 future specs | 1 commit / 1,111 lines ahead of master; documentation only | Preserve and merge/cherry-pick product knowledge | Review facts with founder, then integrate docs |
| local `feat/context-and-specs` | Adds spec/constitution templates and planning prompts to the remote feature branch | 2 commits ahead of master and 1 ahead of remote; dirty working tree on top | Preserve; do not push or clean automatically | Reconcile the tracked deletion and untracked plans with owner |
| local `feat/sprint-1` | Intended implementation branch | Points to the same commit/tree as local `feat/context-and-specs`; no implementation | Rename or repurpose only after approval; otherwise archive later | Do not treat as Sprint 1 evidence |
| `origin/feature/en-es-i18n` | Re\_ assets plus English/Spanish reduction | 4 commits ahead of master; superseded by merge into `my-photos` | Preserve temporarily; archive after integration stabilizes | No independent merge needed |
| `origin/my-photos` | Re\_ media/catalog adaptation and merged bilingual work | 6 commits ahead of master; strongest app branch; isolated build succeeds after excluding invalid filenames | **Recommended implementation base** | Create reviewed integration branch from this ref |

### Branch-specific findings

- `origin/my-photos` and `origin/feature/en-es-i18n` differ only by a merge commit and a header home-link fix. The latter is fully contained in the former.
- Product context and implementation diverged directly from `master`; neither line contains the other's work. Their changes are largely non-overlapping and should integrate cleanly, but the existing dirty worktree makes an in-place merge unsafe.
- `origin/my-photos` tracks 10 `:Zone.Identifier` files. These paths prevent a normal archive/checkout on Windows. Remove them in a dedicated reviewed commit and add an ignore rule.
- Repository tree sizes: master 320 files / 14.82 MB; product-context remote 336 / 14.91 MB; local context 340 / 14.93 MB; Re\_ implementation 298 / 24.45 MB.
- Existing user work was preserved: deleted `context/specs_def_prompt.md`; untracked implementation plans/prompts; untracked Saco media.

## 3. Technical audit

### Architecture and frameworks

- Astro 5 static-site generation with strict TypeScript configuration.
- React 19 islands for all image rendering and the home gallery; Alpine.js and shared `@hdud/common` components for navigation, theme and utility behavior.
- Tailwind CSS 4, DaisyUI, HeroUI, Iconify, Astro sitemap, webmanifest, Open Graph image generation, Markdown content collections and i18next.
- No backend, database, CMS, payment, form handler, analytics implementation, test suite, CI workflow, or Vercel project configuration is present.
- The application delegates foundational layout, header/footer utilities, robots generation and several interactive behaviors to `@hdud/common`, increasing coupling to an upstream template package.

### What works

- The checked-out template branch builds successfully with telemetry disabled when Vite can read dependencies.
- A Windows-safe temporary copy of `origin/my-photos` builds 16 application pages and four redirect stubs.
- Static route generation, content collections, two locale directories, sitemap generation, PWA manifest generation, and dynamic OG image generation execute.
- Re\_ logo assets and product imagery for Costura, Saco and Sandal exist on `origin/my-photos`.

### Broken or incomplete behavior

1. All four product Markdown files use placeholder copy; Sandal is incorrectly titled “Saco Project.”
2. Zurda routes are generated from `imageInfo.json`, but all 14 expected AVIF/WebP assets are absent from the branch.
3. Spanish catalog/product links use unprefixed URLs, switching users into English.
4. The shared language selector links English pages to nonexistent `/en/...` URLs even though English is served at `/`.
5. Header marketing copy is hard-coded in English on Spanish pages.
6. The header produces nested anchors through the shared component, which is invalid HTML.
7. Product previous/next links ignore locale.
8. No page contains the concierge form; contact is a template `mailto:` link to the wrong inbox.
9. Generated `robots.txt` includes `{"message":"This access token is invalid."}` from an unauthenticated build-time DarkVisitors request.
10. Unrelated `/blog` redirects generate dead destinations; `/tools/screen` is publicly built.
11. Site metadata remains “Designer,” `howduudu.tech`, a template email, and a China ICP footer.
12. The About pages still describe and link to the upstream template.
13. The manifest keeps `HDUD` and template description; its icon configuration creates a duplicate `/public/favicon` tree.
14. `astro.config.mjs` references `fs` without importing it. It is a latent failure if the raw-font transform executes.
15. The legacy deployment script deletes a directory, clones and pushes to a different repository/branch, and must not be used for Re\_.
16. The bundle visualizer emits an approximately 845 KB `package_alalyze.html` report into the production output instead of keeping analysis opt-in.

### Code quality and maintainability

- There are no `lint`, `format`, `check`, `test`, `test:e2e`, or `validate` scripts.
- `@astrojs/check` and `typescript` are not declared project dependencies, so strict checking is not reproducible.
- `lodash/debounce`, `sharp`, and `p-limit` are imported directly but are available only transitively; the build can break when parent dependencies change.
- Content schemas validate only `base` for works; titles, descriptions, locale, product type, material story, lead time, dimensions, alt text and publication state are unchecked.
- The active footwear spec and `future-specs/001-footwear-preorder.md` substantially duplicate the same journey; consolidate them so agents do not implement conflicting versions.
- i18next is globally initialized and language-mutated on each call; a simpler typed dictionary or isolated instance would be safer for static concurrent builds.
- Dead or suspect code includes an Astro component importing nonexistent `Image.astro`, unused packages, template comment integration, blog redirects and the external robots generator.
- Content and image metadata are coupled manually; the build does not assert that every referenced image exists.

### Security and privacy

- `npm audit --omit=dev` on the strongest branch reported 31 current advisories: 1 critical, 18 high, 10 moderate and 2 low. Some concern build/dev tooling rather than the static output, but the dependency chain must be upgraded and re-audited before launch.
- The robots route performs an external build-time request with an undeclared token and publishes the error response.
- A future contact form will process personal data. Provider choice, data minimization, spam protection, retention, privacy disclosure and recipient verification need human approval.
- No secrets are committed in the inspected refs, but no `.env.example` or documented environment contract exists.
- Third-party scripts currently include Google Fonts, jsDelivr, Giscus and the shared template behaviors. Each should be justified or removed to reduce privacy, availability and supply-chain surface.

### Performance

- The `my-photos` build output is 26.46 MB. Costura alone contains 16.22 MB across 118 image files; one WebP is 1.04 MB.
- Home HTML is about 156 KB and the Costura detail HTML about 121 KB because full image metadata is serialized into React islands.
- Client chunks include about 176 KB, 109 KB, 57 KB and 44 KB uncompressed bundles, despite the documented zero-JS-first goal.
- Product images render only after React mounts. Without JavaScript, visitors and crawlers see skeletons instead of product imagery.
- Both AVIF and WebP versions are committed, contradicting the documented future Cloudinary-only workflow. For MVP, choose one coherent media strategy rather than operating both accidentally.

### Accessibility

- Every audited public page has zero `h1` elements.
- The four header logo images on each page have no `alt`; product images also lack descriptive alternatives.
- Product imagery is client-only and therefore absent from initial semantic content.
- Labels such as `left`, `right`, `refush`, and icon-only controls are not meaningful enough; touch handlers suppress default behavior.
- Invalid nested anchors, JavaScript pseudo-links (`javascript:null` and misspelled `javascrpt:null`), and hover-dependent labels create keyboard and assistive-technology risks.
- Motion, custom cursor, transitions and animation need `prefers-reduced-motion` verification.
- A browser-based WCAG run could not be completed because the in-app browser runtime was sandbox-blocked; this remains a release-gate test.

### SEO

- Canonicals are generated, but for the wrong domain.
- No `hreflang` alternates were present on audited pages.
- Pages lack useful headings and product-specific descriptions; product titles use slugs and generic “Portfolio.”
- Open Graph images and metadata remain template-branded; image URLs include a suspicious trailing slash.
- Sitemap includes tool routes, placeholder pages and unrelated redirects.
- No structured data is present for Organization, Person, Product/CreativeWork, or Event/Service.
- The missing server-rendered product images and alt text weaken image discovery and content comprehension.

### Deployment and documentation

- Vercel and Cloudinary are described as intentions only; no deploy configuration, preview policy or environment contract is committed.
- The only deployment script targets `rnetao/howduudu.tech` and forcefully replaces a local `website` directory before pushing. Treat it as obsolete and dangerous for this project.
- README and bilingual docs describe the upstream template, not Re\_, onboarding, environment variables, content publishing or release operations.
- No CI, branch protection evidence, rollback instructions, form deliverability check, domain/DNS checklist or production monitoring exists.

## 4. Product and messaging audit

### Current message in code

The strongest branch says “Sneakers made from sneakers” and “Unique, handcrafted footwear, made just when you need it.” This is a useful hook, but the rest of the site immediately reverts to generic portfolio language. It does not explain the Método Re\_, founder, material transformation, traceability, made-to-order expectations, workshops or institutional services.

### Proposed message

**Assumption-marked draft:**

> Re\_ transforms discarded footwear into contemporary made-to-order pieces through the Método Re\_: a proprietary process of deconstruction, classification and patchwork assembly developed by designer and material researcher Bárbara León in Sevilla.

Supporting message:

> Explore footwear, bags and learning experiences shaped by real circular practice. Every inquiry begins a direct conversation with the workshop, so materials, fit, timing and purpose can be handled with care.

This draft uses only repository evidence. Claims about environmental impact, exact lead times, availability, prices, clients, awards and material provenance must be supplied and approved by the founder.

### Target audiences and value

| Audience | Need | Re\_ value | MVP conversion |
|---|---|---|---|
| Conscious premium consumer | Distinctive piece, trust, fit and provenance | Made-to-order craft, unique material language, human guidance | Product inquiry with model and size context |
| Sevilla creative audience | High-quality hands-on experience | Direct access to the workshop and Método Re\_ | Workshop date/interest inquiry |
| Design professional or student | Advanced applied circular-design learning | Personalized technical residency | Profile, objectives and date inquiry |
| University/design school | Credible specialist teaching | Masterclasses, workshops and curricular collaboration | Institutional proposal inquiry |
| Concept store buyer | Differentiated product and lower stock risk | Discovery/fit-kit model | Post-MVP partner inquiry unless approved now |

### Missing or weak content

- Founder biography, authority and portrait.
- A concise, evidence-led explanation of the Método Re\_ and its stages.
- Final names, descriptions, materials, fit notes, available sizes, care, uniqueness disclaimer and realistic lead time for each launch product.
- Approved photography selection, descriptive alt text and provenance for Zurda assets.
- Clear workshop/residency/institutional formats, inclusions, audience, location, availability and response expectations.
- Trust evidence: exhibitions, collaborations, press, teaching experience or testimonials, if verifiable.
- Production capacity and response-time expectation for the concierge promise.
- Privacy/legal information and a clear data-use note at the form.

### Recommended MVP information architecture

1. `/` and `/en/`: Home — proposition, Método Re\_, featured pieces, learning pathways, founder/trust and primary inquiry CTA.
2. `/piezas/` and `/en/pieces/`: Catalog for launch-ready models.
3. One bilingual detail page per approved model: Saco, Sandal, Costura and Zurda. Add Manuela only when content/media are ready.
4. `/metodo/` and `/en/method/`: Method, material traceability, founder and workshop.
5. `/formacion/` and `/en/learning/`: One MVP page with workshops, professional residencies and institutional training.
6. `/contacto/` and `/en/contact/`: Unified context-aware concierge form.
7. Bilingual privacy/legal pages and a useful 404.

## 5. Exact MVP definition

### Must have for launch

- Spanish-first or English-first routing decision, applied consistently with same-page locale switching and `hreflang`.
- Approved home, method/about, catalog, four launch product pages, combined learning page, contact, privacy/legal and 404 pages in Spanish and English.
- One unified form with product/service context, name, email, consent, message and conditional fields for size, dates, portfolio URL or institution.
- Form validation, honeypot/rate protection, success/error states, language metadata and verified delivery to the real inbox.
- Real domain, inbox, titles, descriptions, canonical URLs, OG assets, sitemap and robots file.
- Semantic server-rendered images, responsive sizes, useful alt text, no broken media, and a media budget.
- Keyboard navigation, focus visibility, labels/errors, reduced motion, contrast review and WCAG 2.1 AA test.
- Dependency upgrade/re-audit, reproducible Node 20 install, build/type/lint/link checks and CI.
- Preview deployment, custom-domain checklist, rollback path and post-deploy smoke test.

### Should have soon after MVP

- Dedicated concept-store/B2B partner landing and inquiry path.
- Lightweight, consent-aware analytics with lead-event measurement after a privacy decision.
- More product models and editorial case studies as approved content arrives.
- Content/image validation scripts and a more comfortable editor workflow.
- Structured data beyond the basic Organization/Person layer.

### Nice to have later

- Digital product passports and repair flows.
- Workshop inventory, booking, payments and waitlists.
- Authenticated B2B portal and Fit Kit workflow.
- E-learning accounts, payments, progress and media protection.
- CMS if non-developers are publishing often enough to justify it.

### Not needed now / remove or archive after approval

- Checkout, customer accounts, database, CRM synchronization and automated pricing.
- Giscus comments, developer screen route, blog redirects, China ICP footer, demo portfolios, template About/README, PWA install experience, custom cursor and unrelated deployment script.
- A custom MCP server for repository or brand knowledge.

### MVP acceptance criteria

1. Every public route has equivalent approved ES/EN content and switches language without changing subject.
2. Every product/service CTA reaches the concierge form with correct, tamper-tolerant context.
3. Valid submissions arrive once in the verified inbox with locale and source; failure is recoverable and no sensitive value appears in URLs/logs.
4. There are no broken internal links, missing media, placeholder strings, template identities or dead ends.
5. Clean install, typecheck, lint, build, link test and smoke tests pass in CI on Node 20.
6. WCAG 2.1 AA manual/automated checks pass for critical journeys; keyboard-only use is complete.
7. Agreed page-weight and Core Web Vitals budgets pass on representative mobile conditions.
8. Search metadata, sitemap, robots, canonical and language alternates reference the production domain.
9. Founder approves Spanish copy, English translation, media selection, business facts, form expectations and legal text.
10. A preview-to-production release and rollback rehearsal is documented.

## 6. Prioritized work plan

The executable backlog with complexity, dependencies, files, acceptance criteria, agent autonomy and approval gates is maintained in [`docs/mvp/backlog.md`](../mvp/backlog.md).

Recommended phase order:

- **Phase 0:** Preserve the dirty tree, agree base branch, capture remote refs and approve integration strategy.
- **Phase 1:** Integrate `origin/my-photos` with product context; remove invalid filenames and template identity; establish checks.
- **Phase 2:** Repair routing/media/content schema and build the concierge engine.
- **Phase 3:** Write, translate and approve launch content.
- **Phase 4:** Refine quiet-luxury UI; complete SEO, accessibility and performance gates.
- **Phase 5:** Verify form delivery, preview deployment, domain/legal details and production smoke tests.
- **Phase 6:** Operationalize agent instructions/skills; defer MCPs until recurring integrations justify them.

## 7. Skills plan

Repository-local draft skills were created under `skills/` because `.agents/` is workspace-reserved read-only. Each contains a validated `SKILL.md` plus interface metadata.

| Need considered | Repository skill | Path | Status |
|---|---|---|---|
| Project Audit | `audit-project` | `skills/audit-project/SKILL.md` | Create now |
| Branch Comparison | `compare-branches` | `skills/compare-branches/SKILL.md` | Create now |
| MVP Planning | `plan-mvp` | `skills/plan-mvp/SKILL.md` | Create now |
| Business Messaging Review | `review-business-message` | `skills/review-business-message/SKILL.md` | Create now; claims still need founder input |
| Landing Page Improvement | `improve-landing-page` | `skills/improve-landing-page/SKILL.md` | Create now |
| Frontend Component Refactor | `change-frontend-component` | `skills/change-frontend-component/SKILL.md` | Create now |
| Bug Fix | `fix-bug` | `skills/fix-bug/SKILL.md` | Create now |
| SEO + Accessibility + Performance | `audit-web-quality` | `skills/audit-web-quality/SKILL.md` | Consolidated now to reduce duplication |
| Deployment Readiness | `prepare-deployment` | `skills/prepare-deployment/SKILL.md` | Create now; provider details need input |
| Documentation Update | `update-documentation` | `skills/update-documentation/SKILL.md` | Create now |
| Agent Handoff | `handoff-agent-work` | `skills/handoff-agent-work/SKILL.md` | Create now |
| MCP Design | `design-mcp` | `skills/design-mcp/SKILL.md` | Create now as an evaluation guardrail |

## 8. MCP plan

### Required for MVP

None. Repository knowledge is small enough for versioned Markdown plus skills. Website QA should begin as package scripts and CI. Form, hosting and media providers already expose standard APIs/dashboards; a custom protocol layer would add maintenance before the workflow is stable.

### Useful after MVP, only if repetition proves the need

| Idea | Connects to / exposes | Permissions | Risk | Complexity | Trigger to build |
|---|---|---|---|---|---|
| Media inventory MCP | Cloudinary folders, asset metadata, transformations and broken-reference checks | Read/list by default; upload/tag only with explicit approval | Accidental publication/deletion; asset cost | Medium | Frequent agent-led media updates across many products |
| Release evidence MCP | Vercel previews/deployments, build logs, domain status and smoke-test results | Read deployment; production promotion separately gated | Production changes and log data | Medium | Multiple weekly releases with manual evidence gathering |
| Business operations connector | Approved task system or CRM for inquiry follow-up | Minimum scoped read/write per project | Customer personal data and unintended messages | High | A real CRM/task workflow exists and manual duplication is measurable |

### Not recommended now

- Repository-knowledge MCP: use `AGENTS.md`, `context/`, `docs/` and repository search.
- Brand-guideline MCP: use versioned brand docs and `review-business-message`.
- Website-QA MCP: use deterministic local scripts, Playwright/axe and CI.
- CMS MCP: there is no selected CMS.
- Custom customer-context MCP: no approved data source or privacy model exists.

## 9. Suggested project structure

```text
AGENTS.md
context/                       # Existing source business/spec evidence; preserve history
docs/
  audit/                       # Dated audits and decision records
  product/                     # Approved positioning, audiences and content inventory
  brand/                       # Publishable tone/claims/asset guidance derived from context
  mvp/                         # Scope, backlog, acceptance and release checklist
  technical/                   # Architecture and deployment decisions
  agent-workflow/              # Agent operating protocol and handoff template
skills/                        # Repository-local reusable agent skills
tasks/                         # Add only if GitHub Issues is not chosen as the source of truth
```

Do not duplicate facts between `context/`, `docs/brand` and skills. Treat `context/` as source evidence, `docs/brand` as approved publishable guidance, and skills as concise procedures that link to those sources.

## 10. First 10 immediate actions

1. Preserve the current dirty worktree in a human-approved commit or stash; decide whether the deleted prompt and untracked Saco assets belong.
2. Approve `origin/my-photos` as the implementation base and create a non-production integration branch from it.
3. Remove tracked `Zone.Identifier` paths and add an ignore rule so Windows checkouts work.
4. Bring the product-context commits into the integration branch without overwriting user work.
5. Replace template identity: package metadata, site config, footer, About, README, robots, manifest, redirects, Giscus and legacy deploy script.
6. Decide the real domain, inbox, default-locale URL policy, form provider and launch product/service inventory.
7. Fix ES/EN links, same-page switching, locale-aware product navigation, `hreflang`, canonical and sitemap behavior.
8. Restore/approve Zurda media, enforce media existence in the build, and render all product images semantically with alt text.
9. Implement the bilingual content schema, approved pages and unified concierge form; test real inbox delivery and spam handling.
10. Add reproducible Node 20 validation/CI, resolve dependency advisories, run accessibility/performance/link tests, and deploy an approval preview.

## Audit limitations

- Visual browser and automated rendered accessibility inspection were blocked by the in-app browser runtime's sandbox permissions. Source and generated HTML were inspected instead; browser QA remains mandatory.
- No production account, domain, inbox, Cloudinary library, analytics, form-provider dashboard or hosting project was accessed.
- Dependency advisories reflect the npm registry on the audit date and should be rechecked during implementation.
