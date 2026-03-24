# Working Notes — Alex Hageman Personal Landing Page

> **Internal document — not intended for public audiences.**
> This file is for developer and AI assistant reference only. Update it at the end of every working session before closing the repository.

---

## 1. How to Use This File (For AI Assistants)

1. Read this entire file before suggesting any changes or writing any code.
2. Read `README.md` for the public-facing project description and feature list.
3. Do not change the folder structure or file naming conventions without discussing it first.
4. Follow all conventions listed in Section 8 exactly — do not introduce new patterns without flagging them.
5. Do not suggest any approach listed in Section 10 ("What Was Tried and Rejected").
6. Ask a clarifying question before making any large structural change (e.g., adding a framework, splitting into multiple pages, adding JavaScript logic).
7. This project was AI-assisted. The initial structure was generated with Claude and reviewed and modified by the author. Refactor conservatively — prefer targeted edits over wholesale rewrites.

---

## 2. Current State

**Last Updated:** 2026-03-24

This is a complete, functional first version of Alex Hageman's personal landing page. All required sections from the PRD are built and rendering correctly. The site is live on Replit and the repository is connected to GitHub at `github.com/Alex-Hageman/landing-page`. No JavaScript logic is in use. The page has not yet been tested in Safari or Firefox manually, though it uses standard CSS with no vendor-specific features.

### What Is Working

- [x] Sticky navigation bar with anchor links to all four sections
- [x] Hero section with circular headshot, name, tagline, and CTA buttons
- [x] About Me bio paragraph
- [x] Skills section with teal accent pill badges (Tools) and outlined pill badges (Techniques)
- [x] Projects section with three cards in a responsive CSS Grid
- [x] Dark navy contact footer with LinkedIn, GitHub, and email badge links
- [x] Fully responsive layout from 320px to desktop
- [x] WCAG 2.2 AA compliance: descriptive alt text, logical heading hierarchy, keyboard-navigable links, `focus-visible` outline styles
- [x] External links open in new tab with `rel="noopener noreferrer"`
- [x] `README.md` written and committed
- [x] Deployment configured as a static site on Replit

### What Is Partially Built

- [ ] `js/scripts.js` exists but is empty — reserved for future enhancements (smooth scroll polyfill, active nav highlighting, etc.)
- [ ] `LICENSE` file referenced in `README.md` but not yet created in the repository

### What Is Not Started

- [ ] MIT `LICENSE` file (needs to be added via GitHub's license template tool)
- [ ] Project card images or screenshots (cards currently have no visual graphic)
- [ ] Favicon (`/images/favicon.ico` or `.png`)

---

## 3. Current Task

**What I was working on when I last stopped:**
The initial build is complete and the `README.md` and `WORKING_NOTES.md` documentation files have been generated. The last content edit was removing an em dash from the About Me paragraph and replacing it with a comma. The repository has been committed locally via Replit's automatic checkpoint system but has not yet been pushed to GitHub.

**The very next step is:**
Push the repository to GitHub (`git push origin main` in the Shell tab) and create a `LICENSE` file using GitHub's built-in MIT template.

---

## 4. Architecture and Tech Stack

| Technology | Version | Why It Was Chosen |
|---|---|---|
| HTML5 | Current standard | Required by STANDARDS.md; semantic elements improve accessibility and SEO |
| CSS3 | Current standard | Required by STANDARDS.md; no framework keeps the project lightweight and dependency-free |
| Inter (Google Fonts) | Variable | Clean, modern, highly legible sans-serif; freely available via CDN with no install needed |
| Python `http.server` | Built-in (Python 3) | Simplest possible dev server for serving static files; zero configuration on Replit |
| Replit | — | Free hosting and dev environment required by the course ($0 budget constraint from PRD) |
| GitHub | — | Version control and public repository for course submission and recruiter visibility |

---

## 5. Project Structure Notes

```
landing-page/                  ← Repository root
├── index.html                 ← Single-page entry point; all content lives here
├── css/
│   └── stylesheet.css         ← All styles; no inline styles or <style> tags permitted
├── js/
│   └── scripts.js             ← Empty placeholder; reserved for future JS (do not delete)
├── images/
│   └── headshot.jpeg          ← Profile photo; note .jpeg extension (not .jpg)
├── PRD.md                     ← Product Requirement Document; source of truth for content
├── STANDARDS.md               ← Technical and design standards; governs every file
├── README.md                  ← Public-facing project description for GitHub
├── WORKING_NOTES.md           ← This file; internal developer and AI reference
├── Alex_Hageman_Resume.pdf    ← Source resume; do NOT link to or embed this on the site
└── .github/
    └── workflows/             ← Legacy Azure Static Web Apps CI/CD files from original repo; not in use
```

**Non-obvious decisions:**
- `js/scripts.js` is intentionally empty. The STANDARDS.md specifies the `/js/` folder must exist. Do not remove it.
- The headshot file extension is `.jpeg`, not `.jpg`. The `src` attribute in `index.html` references `images/headshot.jpeg` — do not rename the file or change the reference without updating both.
- `Alex_Hageman_Resume.pdf` is in the repo root as a source document. STANDARDS.md explicitly says: **do not link to or embed the resume anywhere on the site.**
- `.github/workflows/` contains Azure deployment files from the original GitHub import. They are inactive and should not be modified.

**Files that must not be changed without discussion:**
- `STANDARDS.md` — defines constraints for the entire project
- `PRD.md` — source of truth for required content
- `images/headshot.jpeg` — filename must stay consistent with the HTML reference

---

## 6. Data / Database

This project has no persistent data layer. It is a fully static site with no database, no flat data files, and no server-side logic. All content is hard-coded directly in `index.html`.

---

## 7. Conventions

### Naming Conventions
- All filenames are lowercase with hyphens (e.g., `stylesheet.css`, not `StyleSheet.CSS`)
- The headshot is the one exception: `headshot.jpeg` (lowercase, `.jpeg` extension)
- HTML `id` attributes use kebab-case (e.g., `id="hero-name"`, `id="about-heading"`)
- CSS class names use BEM-inspired kebab-case (e.g., `.project-card`, `.tag--accent`, `.nav-links`)
- CSS custom properties use `--color-`, `--font-`, `--max-` prefixes for grouping

### Code Style Rules
- No inline `style=""` attributes — all styles go in `css/stylesheet.css`
- No `<style>` tags in any HTML file
- CSS properties are grouped logically: layout → typography → color → spacing → transitions
- All external links must include `target="_blank" rel="noopener noreferrer"`
- All `<img>` elements must have a descriptive `alt` attribute
- Heading hierarchy: `<h1>` (page name in hero) → `<h2>` (section headings) → `<h3>` (card/subsection titles)

### CSS Architecture
- CSS custom properties (variables) are defined in `:root` at the top of `stylesheet.css`
- Section styles are numbered and labeled with comments (e.g., `/* ── 6. Hero Section ──`)
- Responsive breakpoints: mobile-first base styles, `min-width: 640px` for tablet, `min-width: 900px` for desktop
- Max content width is `900px`, enforced with `.section-inner` wrapper divs

### Git Commit Message Style
- Imperative mood, present tense: "Add hero section" not "Added hero section"
- Specific and descriptive: "Replace em dash with comma in About Me paragraph"

---

## 8. Decisions and Tradeoffs

- **No CSS framework chosen:** STANDARDS.md left the framework choice open. Vanilla CSS was chosen to keep the project dependency-free, lightweight, and aligned with the course's emphasis on understanding the underlying technology. Do not suggest adding Bootstrap or Tailwind.
- **CSS custom properties over hardcoded values:** All colors, fonts, and spacing use `:root` variables so future redesigns require changing values in one place only.
- **Static site, no JavaScript:** The PRD scopes out "complex animations" and the STANDARDS.md specifies "no server-side code, no database, no back-end." JS is reserved for future non-breaking enhancements only.
- **Python `http.server` for dev:** No build step is needed for a static HTML/CSS project. Python's built-in server avoids adding Node or any package manager to the environment.
- **Dark navy footer for contrast:** The contact section uses `#1A2332` (dark navy) background to visually separate it from the white/grey body sections and to meet WCAG contrast ratios for white text on dark backgrounds.
- **`focus-visible` instead of `focus`:** Using `:focus-visible` ensures keyboard users see focus outlines while mouse users do not see them on click, providing a cleaner visual experience without sacrificing accessibility.

---

## 9. What Was Tried and Rejected

- **Em dash in About Me bio:** An em dash (`—`) was originally used in the sentence "digital product management — translating raw data…". It was replaced with a comma at the author's request. Do not reintroduce the em dash.
- **Linking to the resume PDF:** The resume file is in the repository. Embedding or linking it on the page was explicitly ruled out by STANDARDS.md. Do not add a "Download Resume" link.

---

## 10. Known Issues and Workarounds

- **`LICENSE` file missing:** `README.md` contains a markdown link to `[MIT License](LICENSE)` but the file does not yet exist in the repository. The link will 404 on GitHub until the file is created. **Workaround:** None in place. Next step is to create it via GitHub's license template tool.
- **Headshot file extension is `.jpeg` not `.jpg`:** The STANDARDS.md folder diagram shows `headshot.jpg` but the actual file is `headshot.jpeg`. The `index.html` reference matches the real file (`images/headshot.jpeg`). Do not rename the file or "correct" the extension — both are valid and the current setup works correctly.
- **`.github/workflows/` Azure files:** Two GitHub Actions workflow files from the original Azure Static Web Apps import remain in the repository. They are inactive (Azure deployment tokens are not configured) and do not affect the Replit deployment. They can be deleted in a future cleanup session but are harmless as-is.

---

## 11. Browser and Environment Compatibility

**Expected to work:** Chrome (primary development browser), Firefox, Safari, and mobile browsers (iOS Safari, Chrome for Android).

**Tested:** Chrome on desktop via Replit's preview pane.

**Not yet manually tested:** Safari, Firefox, or a physical mobile device.

**Known incompatibilities:** None identified. The CSS uses only widely-supported features (Flexbox, CSS Grid, custom properties, `clamp()`). All are supported in all modern browsers. Internet Explorer is not supported and is not a requirement.

**Environment:**
- Host: Replit (NixOS, stable-25_05 channel)
- Dev server: Python 3 `http.server`, port 5000, bound to `0.0.0.0`
- No build step, no package manager, no Node.js required

---

## 12. Open Questions

- Should project cards eventually include screenshot images or graphic placeholders? The PRD mentions "project image placeholders/local images" as in-scope but none were added in the initial build.
- Should a favicon be added? It is not mentioned in the PRD or STANDARDS but is standard practice and prevents a 404 in browser dev tools.
- Should the nav collapse into a hamburger menu on mobile, or stay hidden below 420px as it currently does?
- Is the GitHub URL `github.com/athageman` (from the author's prompt) or `github.com/Alex-Hageman` (from the PRD)? The contact footer currently uses `athageman`.

---

## 13. Session Log

### 2026-03-24
- Explored repository structure after GitHub import
- Read `PRD.md` and `STANDARDS.md`; confirmed understanding of goals, content requirements, and design direction with the author
- Built complete `index.html` and `css/stylesheet.css` from scratch with all five PRD sections
- Created empty `js/scripts.js` per STANDARDS folder structure requirement
- Replaced em dash in About Me paragraph with a comma per author request
- Generated `README.md` with description, features, contributing, license, author, contact, and acknowledgements sections
- Generated `WORKING_NOTES.md` (this file)
- Left incomplete: pushing to GitHub, creating MIT LICENSE file, project card images, favicon
- Next step when resuming: `git push origin main` in the Shell tab, then create `LICENSE` on GitHub

---

## 14. Useful References

- [PRD.md](PRD.md) — Project requirements and required content (source of truth for what must appear on the page)
- [STANDARDS.md](STANDARDS.md) — Technical and design constraints (governs every file in the project)
- [MDN HTML5 Semantic Elements](https://developer.mozilla.org/en-US/docs/Glossary/Semantics#semantic_elements) — Reference for correct semantic element usage
- [MDN CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout) — Used for the projects section responsive grid
- [Google Fonts — Inter](https://fonts.google.com/specimen/Inter) — Typography used across the site
- [WCAG 2.2 Quick Reference](https://www.w3.org/WAI/WCAG22/quickref/) — Accessibility standard followed throughout
- [CSS Tricks — A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) — Reference for nav and hero layout
- **AI assistance:** Initial code structure and documentation generated with Claude (Anthropic). All output reviewed and approved by the author. Refactor conservatively.
