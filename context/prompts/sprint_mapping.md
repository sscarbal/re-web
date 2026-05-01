**Role:** Senior Technical Lead and Solutions Architect.

**Context:**
We are building a digital ecosystem for "Re\_", a sustainable footwear and accessories brand. The project follows a strict `spec-kit` methodology. Our approach for this phase is a "Concierge MVP": a high-performance, minimalist static catalog that routes all user intentions (pre-orders, workshop bookings, B2B inquiries) to a single, unified contact form handled manually via email. We are NOT using complex databases, CMS, or payment gateways in this phase.

Our tech stack is based on an existing Astro template (`DesignPhotographyPortfolio`), deployed on Vercel, using Cloudinary for all media assets.

All product and technical guidelines are located in the `/context` directory of this workspace. Please read and analyze the following files:

- `/context/constitution.md` (Strict engineering, lean operations, and UX principles)
- `/context/the_brand.md` (Brand tone, mission, and the core "Método Re\_")
- `/context/content_workflow.md` (Asset management rules)
- All 7 active feature specifications inside `/context/specs/` (001 through 007).

_CRITICAL INSTRUCTION: Strictly ignore the `/context/specs/future-specs/` folder. Do not include any logic from those files in this phase._

**Your Task:**
Before we write any code or dive into individual feature implementation, I need you to act as an Architect and generate a **Global High-Level Implementation Plan (Sprint Roadmap)** based on the 7 active specs.

Please output a comprehensive Markdown document (which we will save as `/context/implementation/000-global-sprint-plan.md`) that includes:

1. **Architectural Overview:** A brief summary of how Astro, the i18n routing strategy (Feature 007), Cloudinary, and the form handler (e.g., Web3Forms/Formspree/Netlify Forms) will work together to satisfy the Concierge MVP without a backend.
2. **Sprint / Phase Breakdown:** Group the 7 features into logical sequential Sprints. (e.g., Phase 1: Base Template Setup & i18n routing, Phase 2: The Unified Concierge Desk, Phase 3: B2C Catalogs, etc.).
3. **Dependencies & Parallelization:** Clearly state which features must be built sequentially (e.g., the unified form must exist before the product pages can link to it passing URL parameters) and which can be done in parallel.
4. **Technical Milestones:** What constitutes "done" for each phase to ensure we respect the `constitution.md` guidelines.

**Constraints:**

- Do NOT write the actual application code (no Astro/React/HTML components yet).
- Output ONLY the high-level implementation plan in Markdown.
- Wait for my approval on this global plan before we start executing Sprint 1.
