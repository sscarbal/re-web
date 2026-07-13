# Re\_ Concierge MVP backlog

**Priority:** P0 blocker, P1 MVP, P2 soon after.  
**Complexity:** S (hours), M (roughly 1–2 focused days), L (multi-day/cross-functional).  
**Agent:** Yes means an agent can execute after dependencies are resolved; approval may still gate merge or release.

| Phase | ID | Pri | Task | Complexity | Dependencies | Likely files | Acceptance criteria | Agent | Human approval |
|---|---|---:|---|---|---|---|---|---|---|
| 0 | SAFE-01 | P0 | Preserve and classify current dirty worktree | S | None | Existing untracked/deleted files | Every change has an owner/disposition; nothing lost | Assisted | Yes: commit/stash/discard decision |
| 0 | SAFE-02 | P0 | Approve base and integration strategy | S | SAFE-01 | Git refs only | Decision records `origin/my-photos` base and context integration method | No | Yes |
| 0 | SAFE-03 | P0 | Create protected integration branch and preview policy | S | SAFE-02 | Git/GitHub settings, docs | Branch exists; production remains untouched; review rules documented | Assisted | Yes: branch/settings |
| 1 | REPO-01 | P0 | Remove `Zone.Identifier` blobs and prevent recurrence | S | SAFE-03 | Favicon/logo paths, `.gitignore` | Normal Windows checkout/archive succeeds; no ADS metadata tracked | Yes | Merge approval |
| 1 | REPO-02 | P0 | Integrate brand/spec context | S | SAFE-03 | `context/**` | Brand, constitution and specs present with history; no user work overwritten | Yes | Merge approval |
| 1 | REPO-03 | P0 | Replace template identity and obsolete integrations | M | REPO-02, real domain/inbox | `package*.json`, `src/site.config.ts`, layout/footer/about, robots, manifest, README, scripts | No HDUD/template/China/blog/tool identity in public build | Yes | Domain, inbox, deletion scope |
| 1 | QA-01 | P0 | Add reproducible validation and CI | M | REPO-01 | `package.json`, lockfile, lint/type configs, `.github/workflows/**` | Node 20 clean install, check, lint, build and tests run on PRs | Yes | CI/branch policy |
| 1 | SEC-01 | P0 | Upgrade and minimize dependencies | L | QA-01 | `package.json`, lockfile, imports | Direct imports declared; unused packages removed; audit risk accepted or resolved | Yes | Major upgrade/accepted advisories |
| 2 | I18N-01 | P0 | Fix locale URL model | M | REPO-03 | Astro config, menus, header, detail/grid links, locale pages | Same-page switch works; no `/en` dead routes; links retain locale | Yes | Default URL policy |
| 2 | MEDIA-01 | P0 | Reconcile image metadata and assets | M | SAFE-01 | `public/images`, `imageInfo.json`, content loader/scripts | No referenced asset is missing; Zurda launch decision explicit | Yes | Media selection/deletion |
| 2 | CONTENT-01 | P0 | Define typed bilingual content schema | M | REPO-02, I18N-01 | `src/content.config.ts`, content directories, dictionaries | Build rejects missing title, locale, alt, CTA context, publication state | Yes | Content model |
| 2 | UI-01 | P0 | Replace client-only image components with semantic responsive media | L | MEDIA-01, CONTENT-01 | Image/grid/detail components and styles | Product images exist in initial HTML, have dimensions/alt, lazy priority rules and no React dependency where unnecessary | Yes | Visual review |
| 2 | FORM-01 | P0 | Select and threat-model concierge form provider | S | Real inbox/privacy requirements | Architecture decision, env contract | Provider, fields, spam, retention and failure behavior approved | No | Yes |
| 2 | FORM-02 | P0 | Implement unified bilingual concierge form | L | FORM-01, CONTENT-01, I18N-01 | Contact routes/components, `.env.example`, tests | Context-aware fields, validation, consent, safe success/error states, locale/source metadata | Yes | Copy/privacy/provider |
| 2 | FORM-03 | P0 | Verify real delivery and operational response | M | FORM-02, preview | Provider/inbox settings, release checklist | Test messages arrive once, avoid spam, are legible, and receive agreed response handling | Assisted | Yes: external submission/inbox |
| 3 | COPY-01 | P0 | Approve positioning and claim inventory | M | REPO-02 | `docs/product/**`, `docs/brand/**` | Each claim is sourced, approved, translated or marked unavailable | Assisted | Founder approval |
| 3 | COPY-02 | P1 | Write home, method/founder and trust content | L | COPY-01 | Home/method content and components | Clear proposition, method, founder, proof and CTA in ES/EN | Assisted | Founder approval |
| 3 | COPY-03 | P1 | Complete four launch product records | L | COPY-01, MEDIA-01 | Product Markdown/MDX/content | No placeholders; materials, fit/specs, uniqueness, lead time and CTA approved in ES/EN | Assisted | Founder approval |
| 3 | COPY-04 | P1 | Complete combined learning page | L | COPY-01 | Learning content/routes | Workshops, residencies and institutions are distinguishable and route correct context | Assisted | Offering/availability approval |
| 3 | LEGAL-01 | P0 | Add reviewed privacy and required business disclosures | M | FORM-01, domain/company facts | Legal/privacy pages, form notice | Text matches actual data flow and production entity | No | Legal/owner approval |
| 4 | UX-01 | P1 | Establish minimal quiet-luxury design tokens and layouts | L | COPY-02–04 | Global styles, layouts, components | Mobile-first hierarchy, readable typography, consistent spacing/CTA/focus | Yes | Design approval |
| 4 | SEO-01 | P0 | Complete technical/on-page SEO | M | I18N-01, COPY tasks, domain | Layout/head, sitemap, robots, OG, structured data | Unique metadata, absolute canonicals/OG, `hreflang`, clean sitemap, valid robots | Yes | Domain/brand approval |
| 4 | A11Y-01 | P0 | Meet critical WCAG 2.1 AA journeys | L | UI-01, FORM-02, UX-01 | Components/styles/tests | Headings, landmarks, keyboard, focus, labels/errors, contrast, reduced motion pass | Yes | Manual sign-off |
| 4 | PERF-01 | P1 | Enforce mobile performance budgets | M | UI-01, MEDIA-01, SEC-01 | Build config, assets, CI tests | Agreed HTML/JS/image budgets and Core Web Vitals thresholds pass | Yes | Budget approval |
| 5 | DEPLOY-01 | P0 | Configure preview deployment and environments | M | QA-01, provider decision | Vercel/project config, env docs | PR preview builds from clean install; secrets separated; no prod mutation | Assisted | Hosting access/provider |
| 5 | DEPLOY-02 | P0 | Run release rehearsal and launch checklist | L | All P0 tasks | `docs/mvp/release-checklist.md` | Link/media/form/a11y/perf/SEO/domain/rollback tests recorded | Assisted | Production promotion |
| 6 | AGENT-01 | P1 | Adopt repository workflow and skills | S | Integration branch | `AGENTS.md`, `docs/agent-workflow/**`, `skills/**` | Agents consistently inspect, plan, test and hand off with approval gates | Yes | Governance approval |
| 6 | MCP-01 | P2 | Reassess MCPs after launch evidence | S | Stable recurring workflow | Decision record | Each proposed MCP has measured repetition, owner, permissions and simpler-alternative analysis | Yes | Any MCP build/integration |

