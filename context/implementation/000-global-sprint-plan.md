# Global High-Level Implementation Plan (Sprint Roadmap)

**Phase:** Concierge MVP  
**Methodology:** Spec-Driven Development  
**Brand:** Re\_

This document outlines the strategic implementation roadmap for the Re\_ digital ecosystem. It maps the 7 active feature specifications into a sequential and logical sprint plan, ensuring strict adherence to the brand's constitution (Lean Operations, Premium Aesthetics, Intentional Friction).

---

## 1. Architectural Overview

To achieve a "Concierge MVP" (a high-performance static catalog routing to a unified manual contact flow) without a backend, we will leverage the following architecture:

- **Astro (The Core):** The static site generator. It provides a highly optimized, zero-JS-by-default frontend, fulfilling the "Performance & Quiet Luxury" requirement. Content (products, workshops) will be managed via Markdown/MDX files.
- **Cloudinary (The Visual Engine):** As per the content workflow, no high-resolution media will be stored in the repository. Cloudinary will serve all images and videos with automatic format and quality optimization (`f_auto,q_auto`), ensuring fast load times and premium visual fidelity.
- **i18n Routing Strategy (Feature 007):** Astro's native directory-based internationalization (`/es/` and `/en/` or via configuration) will manage the language state. The user's language preference will persist and dictate the content served, as well as the context sent through the contact form.
- **Unified Form Handler (Feature 006):** A service like Web3Forms, Formspree, or Netlify Forms will capture the unified intent. By passing URL parameters (e.g., `?intent=preorder&model=manuela&lang=en`) to the form page, the static form can dynamically adjust its fields (using minimal client-side JS) and structure the lead data before emailing it directly to Bárbara's inbox, satisfying the "Zero-Dead-Ends" and "Trust & Bespoke UX" principles.

---

## 2. Sprint / Phase Breakdown

The 7 active features are grouped into three logical phases to minimize technical debt and establish strong foundations early.

### Sprint 1: Foundation & The Concierge Engine
*Establishing the skeleton, language routing, and the critical conversion funnel.*
- **Setup:** Base Astro template adaptation and Cloudinary integration.
- **Feature 007:** Multilingual Experience (i18n structure and UI toggle).
- **Feature 006:** Unified Concierge Desk (The central contact form capable of reading context via URL parameters and forwarding emails).

### Sprint 2: B2C Premium Catalog
*Implementing the core products with a focus on visual storytelling and traceability.*
- **Feature 001:** B2C Pre-order Flow (Calzado / Footwear).
- **Feature 002:** Zurda Bags Pre-order (Bolsos / Bags).

### Sprint 3: Academic & B2B Services
*Deploying the high-ticket value propositions and institutional offerings.*
- **Feature 003:** In-person Workshops Inquiry (Ocio Creativo / Local Workshops).
- **Feature 004:** Professional Residency Inquiry (Mentoring B2B/Académico).
- **Feature 005:** Institutional Training Inquiry (Alianzas Universitarias).

---

## 3. Dependencies & Parallelization

### Sequential Dependencies
- **Sprint 1 MUST be completed first.** The Unified Concierge Desk (Feature 006) and the Multilingual Experience (Feature 007) are absolute prerequisites. No product or service page can exist without a functional "Call to Action" route (Zero-Dead-Ends rule). Furthermore, adding i18n after building all pages requires massive refactoring; it must be there from day one.
- **Sprint 2 and Sprint 3 depend on Sprint 1**, but they **do not depend on each other**.

### Parallelization Opportunities
- Once Sprint 1 is complete, **Sprint 2 (B2C) and Sprint 3 (Services)** can be developed in parallel if resources allow.
- Within Sprint 2, Features 001 and 002 can be built concurrently.
- Within Sprint 3, Features 003, 004, and 005 can be built concurrently.

---

## 4. Technical Milestones & Definition of Done

To ensure we respect the `constitution.md` guidelines, each sprint will only be considered "done" when the following criteria are met:

### Milestone 1: The Engine is Alive (End of Sprint 1)
- The site deploys successfully to Vercel.
- The i18n routing works flawlessly (switching languages updates content without breaking URLs).
- Cloudinary integration is tested and verified (inspecting network tabs shows optimized assets).
- **Critical Form Audit:** A test submission through the Unified Concierge Desk successfully reaches the designated inbox (avoiding spam filters) with correct language and intent metadata attached.

### Milestone 2: The Catalog is Open (End of Sprint 2)
- Footwear and Bag model pages are live in both languages.
- Mobile-First design is validated (galleries and traceability stories look premium on mobile devices).
- "Intentional Friction" is verified: All "Initiate Order" buttons successfully route to the Sprint 1 Concierge Desk, automatically pre-filling the product context (e.g., "Interested in Sandal").

### Milestone 3: The Ecosystem is Complete (End of Sprint 3)
- All educational and B2B pages are live and translated.
- The Concierge Desk correctly adapts to complex requests (e.g., requesting a portfolio link for a Residency vs. just contact info for a Workshop).
- **Accessibility & Performance Audit:** Lighthouse scores pass the WCAG 2.1 AA requirements and demonstrate near-instant load times.
