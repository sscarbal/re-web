Viewed 000-global-sprint-plan.md:50-77

Here is the **Technical Component Plan** for Sprint 1. It details the architectural decisions and patterns we will use to build the Foundation, the Multilingual Experience (Feature 007), and the Unified Concierge Desk (Feature 006) while strictly adhering to the Lean Operations and Zero-JS-by-default principles.

### 1. File Structure Updates (Astro i18n Routing)

To maintain a DRY (Don't Repeat Yourself) codebase and avoid duplicating every page manually, we will leverage Astro's dynamic routing (`[lang]`) combined with UI dictionaries. Since we are deploying on Vercel, the site will remain completely static.

**Proposed Directory Structure:**

```text
/src
  /i18n
    ui.ts                 # Translation dictionaries (ES and EN) for menus, buttons, form labels
    utils.ts              # Helper functions (e.g., useTranslations, getLangFromUrl)
  /content
    /products             # Markdown/MDX files for footwear and bags (with lang frontmatter)
    /services             # Markdown/MDX files for workshops and residencies
  /components
    /ConciergeDesk        # Feature 006 components
      ConciergeForm.astro
  /pages
    /[lang]/              # Dynamic route handler for languages
      index.astro         # Homepage (generates /es/ and /en/)
      contacto.astro      # Unified Concierge Desk (generates /es/contacto and /en/contacto)
      ...
```

_Note: We will set `es` as the default locale. We can configure Astro to automatically redirect the root `/` to `/es/` or serve `es` at the root, depending on your SEO preference._

### 2. The Form Handler: Recommendation

**Recommendation:** **Web3Forms**

**Why this fits Lean Operations:**

1. **Generous Free Tier:** Web3Forms offers 250 submissions per month for free, which is 5x more than Formspree's free tier (50/month). For a high-ticket, intentional friction model, 250 leads/month is a very healthy volume.
2. **Platform Agnostic:** Unlike Netlify Forms, which locks you into Netlify hosting, Web3Forms works perfectly on **Vercel** (our chosen deployment platform).
3. **No Backend Required:** It only requires a public Access Key embedded in the frontend HTML form and a simple POST request. No serverless functions or complex API configurations are needed.
4. **Spam Protection:** It includes basic bot protection (honeypot) by default without requiring invasive captchas that break the premium aesthetic.

### 3. Component Architecture for Feature 006 (Unified Concierge Desk)

The `ConciergeForm.astro` component must be "context-aware" but rendered statically. Since we generate a static HTML site, we cannot process URL parameters at build time; we must do it on the client side when the page loads.

**Structure (`ConciergeForm.astro`):**

1. **Server-Side Rendered (HTML/CSS):**
   - We will render the baseline form fields (Name, Email, Main Message Box) statically.
   - We will use Astro props to pass the current language dictionary down to the form so labels are rendered in the correct language instantly on page load.
   - Hidden input fields will be pre-rendered but empty (e.g., `<input type="hidden" id="intent" name="intent" value="" />`).
   - Dynamic UI blocks (like the "Portfolio Link" input for Residencies or the "Shoe Size" dropdown for Pre-orders) will be rendered in the HTML but hidden via CSS (`display: none` or a `.hidden` utility class).

2. **Client-Side Hydration (Vanilla JS logic):**
   - We will use a standard `<script>` tag at the bottom of the component.
   - On `DOMContentLoaded`, the script will read `new URLSearchParams(window.location.search)`.
   - Based on the `intent` parameter (e.g., `?intent=residency&model=none`), a `switch` statement will:
     1. Populate the hidden Web3Forms fields so the context is sent in the email.
     2. Update the UI: Unhide the specific fields required for that intent (e.g., `document.getElementById('portfolio-input').classList.remove('hidden')`).
     3. Dynamically update the main textarea placeholder to prompt the user contextually (e.g., "Tell us about your background..." vs. "Any doubts about the fit?").

### 4. State/Context Management

**Recommendation:** **Pure Vanilla JS inside Astro `<script>` tags + Astro Props.**

**Why:**

- **Nano Stores / Reactivity Libraries:** This is overkill. We do not have a complex global client-side state that changes across multiple components simultaneously. The context (URL parameters) is read exactly once when the `/contacto` page loads.
- **Astro Props:** Will handle all the static translation state (`es` vs `en`) server-side, ensuring zero layout shift and perfect SEO.
- **Vanilla JS:** A lightweight script (~50 lines of JS) attached strictly to the `ConciergeForm.astro` component will handle the URL parsing, DOM manipulation (hiding/showing fields), and the AJAX `fetch` request to Web3Forms to submit the payload without a page reload, presenting the elegant "White Glove" confirmation message. This keeps the bundle size incredibly small and performance lightning-fast.
