# TrekMind Framework Adapters

## First Pass

Before editing, identify:

- Styling entrypoint: `src/style.css`, `src/assets/*.css`, `app/globals.css`, `pages/_app.*`, or plain HTML `<style>`.
- Tailwind presence: `tailwind.config.*`, `postcss.config.*`, or `@tailwind` directives.
- Font loading strategy: Google Fonts `<link>`, CSS `@import`, `next/font`, or existing local fonts.
- Existing component library or design system. Preserve useful structure; replace visual treatment.

## Plain HTML

- Copy or link `assets/trekmind-base.css`.
- Add Google Fonts links in `<head>` when there is no existing font pipeline.
- Structure pages with a constrained `.tm-container`, section dividers, serif headlines, and narrative body text.
- Use the preview HTML only as a rhythm reference. Do not assume every product page needs the same sections.

Minimal head snippet:

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=JetBrains+Mono:wght@400;500&family=Noto+Serif+SC:wght@400;500;600;700;900&display=swap" rel="stylesheet" />
<link rel="stylesheet" href="./trekmind-base.css" />
```

## Vue 3

- Put tokens and component classes in one global stylesheet, usually `src/style.css`, `src/assets/main.css`, or the stylesheet imported by `main.ts`.
- Keep Vue components focused on structure and state. Use semantic classes like `tm-btn-primary` and `tm-input` rather than repeating long inline style blocks.
- If the project already uses scoped styles, keep component-specific layout fixes scoped, but keep TrekMind tokens and base components global.
- For Vite apps, add Google Fonts links in `index.html` unless the project already uses a font package or local fonts.

Common mapping:

```vue
<section class="tm-section">
  <div class="tm-rule">
    <p class="tm-eyebrow">核心发现</p>
    <h2 class="tm-heading-2">标题内容</h2>
    <p class="tm-body">正文内容</p>
  </div>
</section>
```

## NextJS

- App Router: place tokens and component classes in `app/globals.css`.
- Pages Router: place them in the stylesheet imported by `pages/_app.tsx` or `pages/_app.jsx`.
- If the app uses `next/font`, configure `Noto Serif SC`, `Inter`, and `JetBrains Mono` there and expose CSS variables. Do not also load duplicate Google Font links.
- If the app does not use `next/font`, use the existing font-loading convention or add the HTML font links in `app/layout.tsx`.
- Keep page components idiomatic React: use semantic class names and reusable components, not pasted preview HTML.

Suggested `next/font` shape when the project already uses it:

```tsx
import { Inter, JetBrains_Mono, Noto_Serif_SC } from "next/font/google";

const serif = Noto_Serif_SC({ subsets: ["latin"], weight: ["400", "500", "600", "700", "900"], variable: "--font-tm-serif" });
const sans = Inter({ subsets: ["latin"], weight: ["400", "500", "600"], variable: "--font-tm-sans" });
const mono = JetBrains_Mono({ subsets: ["latin"], weight: ["400", "500"], variable: "--font-tm-mono" });
```

Then map CSS:

```css
:root {
  --tm-font-serif: var(--font-tm-serif), Georgia, serif;
  --tm-font-sans: var(--font-tm-sans), "PingFang SC", system-ui, sans-serif;
  --tm-font-mono: var(--font-tm-mono), ui-monospace, monospace;
}
```

## Tailwind

Extend the existing config instead of replacing it. Keep semantic TrekMind component classes in CSS even when utilities are available; this prevents the design language from becoming scattered utility soup.

Recommended theme extension:

```js
theme: {
  extend: {
    colors: {
      paper: { 50: "#fbf8f2", 100: "#f6f1e6", 200: "#ece4d2", 300: "#d8ccaf" },
      ink: { 950: "#0d0d0c", 900: "#1a1a17", 700: "#3a3833", 500: "#6b675f", 400: "#8a857a", 300: "#a8a397" },
      rust: { 700: "#7a2418", 600: "#993322", 500: "#b5432e", 400: "#cc6a55" }
    },
    fontFamily: {
      serif: ["Noto Serif SC", "Georgia", "serif"],
      sans: ["Inter", "PingFang SC", "system-ui", "sans-serif"],
      mono: ["JetBrains Mono", "ui-monospace", "monospace"]
    },
    borderRadius: {
      DEFAULT: "2px"
    }
  }
}
```

When using `@layer components`, add `.tm-*` classes there. Avoid relying only on one-off utility chains in every component.

## Existing UI Restyle

- Preserve routes, data flow, API calls, form behavior, and component responsibilities.
- Replace visual primitives first: background, typography, buttons, inputs, tags, dividers, spacing.
- Reduce cards when the current UI is card-heavy. Convert repeated cards into rule-separated rows or quiet paper panels.
- Keep admin-heavy screens more utilitarian, but still use TrekMind tokens, small radius, clean typography, and no shadows.
- After editing, scan for old palette classes, large radius classes, shadows, gradient decorations, and inline styles that fight the new system.
