**Role:** Act as an expert Web Developer and Hugo Specialist.

**Objective:** Build a custom, high-performance Hugo website from scratch. **Strict Requirement:** Do not use any third-party themes. Create a bespoke internal layout and architecture.

**Site Purpose:**
*   A personal portfolio and technical blog.
*   A landing page for "Findings and Updates."
*   A dedicated section for a downloadable Resume (PDF link).

**Design Aesthetic (Modern Minimalist / Developer-Centric):**
*   **Palette:** Clean white background with high-contrast text.
*   **Typography:** Use "Terminal" or "Monospace" code fonts (e.g., JetBrains Mono, Fira Code, or Roboto Mono) for the entire UI to appeal to a developer audience.
*   **Layout:** Ultra-minimalist, focused on whitespace and readability.

**Technical Requirements:**
1.  **Architecture:** Create a standard Hugo directory structure (`/content`, `/layouts`, `/static`, `/assets`).
2.  **Templating:** Create a base `list.html` and `single.html` in `/layouts/_default`.
3.  **Config:** Provide a comprehensive `hugo.toml` (or `config.toml`) with placeholders for:
    *   Social media links (GitHub, LinkedIn).
    *   SEO metadata and Author details.
    *   Google Analytics and Commenting system IDs.
4.  **Styling:** Use Tailwind CSS or vanilla CSS (centered in `/assets`)—keep it lightweight.
5.  **Resume:** Include a logic-based "Download Resume" button in the navigation or header.

**Deliverables:**
*   Step 1: The `hugo.toml` with all necessary placeholders.
*   Step 2: The base layout files (`baseof.html`, `header.html`, `footer.html`).
*   Step 3: A sample blog post (`.md`) and a sample resume page.

---

### Pro-Tips for the Agent:
*   **Ask for Asset Setup:** Since you are on a Mac, you can tell Claude: *"Assume I have Hugo installed via Homebrew. Initialize the folder structure first."*
*   **Mention Your Specific Stack:** If you prefer **Tailwind CSS** for that "modern" look, mention it explicitly so the agent configures the PostCSS pipeline for you.
*   **Terminal Fonts:** If you want a specific "hacker" vibe, ask it to import a font from Google Fonts (like *Source Code Pro*) in the HTML head.

**Do you want me to add a specific section for your DevOps projects or a "Tech Stack" grid to the resume part?**