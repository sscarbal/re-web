**Status:** APPROVED.
This Technical Component Plan is absolutely flawless. It perfectly respects our Lean Operations constitution, the Vercel deployment target, and the zero-JS-by-default performance requirements. Web3Forms and Vanilla JS are exactly the right tools for this phase.

**Next Step: Execute Code Generation for Sprint 1**

Please proceed to generate the actual code for Sprint 1. We will do this step-by-step to maintain a clean codebase.

Please provide the exact file paths and code blocks for:

1. **i18n Foundation:**
   - Provide the `src/i18n/ui.ts` file with a basic dictionary for ES (default) and EN (focusing on global navigation and contact form labels).
   - Provide the `src/i18n/utils.ts` helper functions.

2. **The Dynamic Routing Skeleton:**
   - Provide the core structure for `src/pages/[lang]/index.astro`. Show how it reads the language and renders a basic localized greeting.

3. **The Unified Concierge Desk (Feature 006):**
   - Provide the complete `src/components/ConciergeDesk/ConciergeForm.astro` file.
   - **Crucial:** Include the HTML structure, the hidden fields for Web3Forms, the dynamic fields (e.g., shoe size, portfolio link) hidden by default with CSS, and the Vanilla JS `<script>` tag at the bottom that parses the URL parameters (intent, model), updates the UI, and handles the `fetch` POST request to Web3Forms to display the "White Glove" success message without reloading the page.

_Note: You can use placeholder Tailwind classes or standard semantic HTML/CSS. I will adapt the final styling to the DesignPhotographyPortfolio theme later. Focus strictly on the logic and architecture you proposed._
