**Status:** APPROVED.
The Global High-Level Implementation Plan is excellent. The logic of building the i18n routing and the Unified Concierge Desk first (Sprint 1) perfectly aligns with our Zero-Dead-Ends policy and the Concierge MVP architecture.

**Next Step: Execute Sprint 1 (Foundation & The Concierge Engine)**

We are now officially starting Sprint 1, which covers:

- Base Astro template setup (DesignPhotographyPortfolio) + Cloudinary logic.
- Feature 007: Multilingual Experience (i18n).
- Feature 006: Unified Concierge Desk.

Before generating the final source code, act as the Lead Developer and provide a specific **Technical Component Plan** for Sprint 1.

Please outline:

1. **File Structure Updates:** What specific directories and files will you create or modify in the Astro project for i18n routing? (e.g., how will `/es/` and `/en/` be structured?).
2. **The Form Handler:** Which specific free tier service do you recommend (Formspree, Web3Forms, Netlify Forms) based on our Lean Operations principle, and why?
3. **Component Architecture for Feature 006:** How will the `ConciergeForm.astro` (or similar) component be structured to read URL parameters (intent, model, lang) and dynamically adapt the UI (e.g., showing a portfolio input if intent=residency)?
4. **State/Context Management:** Will you use Nano Stores, standard Astro props, or pure Vanilla JS inside the Astro script tag to handle the form logic?

**Constraint:** Output only the Component Plan and architectural decisions. Wait for my final confirmation on these technical choices before writing the actual `.astro` or `.ts` code.
