# AI Supported — Project Guide

> This document provides the development rules and style guide for the **AI Supported Badge** project. All future work must adhere to these principles.

---

## 🎯 Core Philosophy

This project exists as a **single, lightweight, static HTML page** designed to be hosted on **Cloudflare Workers Pages**. The focus is on maximum simplicity, high SEO performance, and instant cacheability.

---

## 📜 Mandatory Rules

### 1. Single-Page Architecture
- **One HTML file only** (`index.html`). No multi-page or SPA routing.
- All styles, scripts, and content must be contained within, or directly referenced by, this single file.
- Assets (images, favicons) live in `/shared/` and should be referenced relatively or absolutely to the domain.

### 2. Static & Cacheable
- The page must be **fully static**. No server-side rendering, no build steps required.
- Avoid dynamic content that requires server interaction (e.g., no forms that POST to a backend, no API calls for page content).
- All content should be cacheable by Cloudflare's CDN edge nodes.

### 3. Minimal Libraries & External Calls
- **Zero or minimal external JavaScript/CSS libraries**.
- Currently, the project uses **TailwindCSS via CDN** for rapid styling. If refactoring, and you think it will improve the project performance, accessibility, or user experience, you may suggest:
  - Vanilla CSS with CSS Custom Properties (variables).
  - Pre-compiled Tailwind CSS (purged and minified) as a static file.
- **No runtime frameworks** (React, Vue, Angular, etc.).
- External resources should be limited to:
  - `shields.io` for badge generation.
  - W3C/WAI badges.
  - Google Fonts (if needed, prefer system fonts).

### 4. High SEO, Low Complexity
- Every page must have:
  - A unique, descriptive `<title>`.
  - A compelling `<meta name="description">`.
  - Relevant `<meta name="keywords">`.
  - Open Graph (`og:*`) and Twitter Card meta tags.
  - JSON-LD structured data (`application/ld+json`) for search engines and AI.
- Use only one `<h1>` per page.
- Maintain a logical heading hierarchy (`h1 > h2 > h3`).
- All links and images must have descriptive `alt` and `aria-label` attributes.

---

## ♿ Accessibility (WCAG 2.1 AA)

This project claims **WCAG 2.1 Level AA conformance**. All work must maintain this standard.

- Include a **"Skip to Main Content"** link.
- All interactive elements must be keyboard navigable.
- Use `focus-visible` for clear focus indicators.
- Provide `aria-label` or `aria-labelledby` for non-text elements.
- Ensure sufficient colour contrast.
- Test with screen readers and keyboard-only navigation.

---

## 🎨 Styling Guide

### Colours (Brand Palette)
| Name       | Value     | Usage                         |
|------------|-----------|-------------------------------|
| `teal-500` | `#14b8a6` | Primary accent, buttons, links |
| `teal-700` | `#0f766e` | Focus rings, strong emphasis  |
| `slate-50` | Light     | Body backgrounds              |
| `slate-900`| Dark      | Footer, code blocks           |

### Typography
- **Font Stack:** System fonts for performance.
  ```css
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  ```
- **Line Height:** `1.6` for readability.

### Layout Patterns
- **Max content width:** `max-w-4xl` (or `max-w-6xl` for footer).
- Use **Flexbox** for layout alignment.
- Use the **accordion pattern** (`<details>/<summary>`) for collapsible sections.

---

## 📁 Project Structure

```
ai-supported/
├── index.html        # The single, self-contained page
├── README.md         # GitHub repository documentation
├── AGENTS.md         # This file — project rules and style guide
└── shared/
    └── images/       # Static assets (logos, favicons)
```

---

## ✅ Commit Best Practices

- Commit messages should be clear and descriptive.
- One logical change per commit.
- Test locally before pushing.

---

## 🚀 Deployment Target

| Platform                  | Product          | Notes                                      |
|---------------------------|------------------|--------------------------------------------|
| **Cloudflare Workers**    | **Pages (Static)** | No Workers functions required for this page. |

- Ensure the `index.html` is at the root for Pages to serve it automatically.
- Use Cloudflare's cache rules to maximise edge caching.

---

## ⚠️ Avoid

- ❌ Multi-page sites or client-side routing.
- ❌ Heavy frameworks (React, Vue, Svelte, etc.).
- ❌ Server-side logic or APIs.
- ❌ Unnecessary external scripts or tracking.
- ❌ Complex build pipelines (Webpack, Vite, etc.) unless absolutely necessary.
- ❌ Bloated or non-essential npm dependencies.

---

## 📌 Summary

| Principle              | Requirement                                      |
|------------------------|--------------------------------------------------|
| **Architecture**       | Single static HTML page                          |
| **Hosting**            | Cloudflare Workers Pages (static)                |
| **Libraries**          | Minimal — prefer vanilla CSS/JS                  |
| **SEO**                | High priority — full meta, structured data       |
| **Accessibility**      | WCAG 2.1 AA compliant                            |
| **Complexity**         | Very low — keep it simple                        |

---

*This guide should be updated as the project evolves.*
