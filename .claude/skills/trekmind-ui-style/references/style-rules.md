# TrekMind Style Rules

## Visual Intent

TrekMind should feel like a high-end business magazine turned into a working interface: editorial, restrained, warm, and precise. It is not a SaaS dashboard skin.

## Tokens

Use these names even if the target stack maps them into Tailwind, CSS variables, JS constants, or component theme objects.

| Token | Value | Use |
| --- | --- | --- |
| `paper-50` | `#fbf8f2` | Main page background |
| `paper-100` | `#f6f1e6` | Soft panels and grouped areas |
| `paper-200` | `#ece4d2` | Hover and secondary background |
| `paper-300` | `#d8ccaf` | Disabled states |
| `ink-950` | `#0d0d0c` | Headlines, primary text, dark buttons |
| `ink-900` | `#1a1a17` | Body text |
| `ink-700` | `#3a3833` | Secondary text |
| `ink-500` | `#6b675f` | Hints and metadata |
| `ink-400` | `#8a857a` | Placeholder and quiet labels |
| `ink-300` | `#a8a397` | Dividers and low-emphasis marks |
| `rust-700` | `#7a2418` | Primary accent, numbers, selected labels |
| `rust-600` | `#993322` | Accent hover |
| `rust-500` | `#b5432e` | Highlights and active state |
| `rust-400` | `#cc6a55` | Soft accent |

Use rust as the only default accent color. If the product needs success/warning/error colors, keep them rare and functional.

## Typography

- Primary serif: `Noto Serif SC`, fallback `Georgia`, `serif`.
- UI sans: `Inter`, `PingFang SC`, `system-ui`, `sans-serif`.
- Mono: `JetBrains Mono`, `ui-monospace`, `monospace`.
- Headings: serif, `600` or `700`, line-height around `1.15` to `1.25`, letter spacing `0`.
- Body: serif for narrative/content text, `15px` to `16px`, line-height around `1.75` to `1.9`.
- Controls and forms: sans-serif, `13px` to `15px`, medium weight when needed.
- Metadata and item numbers: mono, rust, usually two-digit labels like `01`, `02`, `F03`.

Font loading in plain HTML can use Google Fonts. In framework projects, follow the framework adapter and the app's existing font strategy.

## Layout

- Page background defaults to `paper-50`.
- Optional right-top warm radial wash may be used for static preview pages, but is not required in product UIs.
- Main content width: usually `1024px` or narrower. Narrative text should stay closer to `640px` to `760px`.
- Section padding: generous, often `48px` to `80px` vertically on desktop.
- Use divider-led structure: `.tm-rule` between sections, `.tm-rule-thin` between list rows, `.tm-rule-strong` for important starts.
- Prefer one or two clear columns. Use three columns only for compact repeated summaries.

## Components

Use these component semantics even when implemented with Tailwind utilities or framework components:

- `tm-eyebrow`: section marker. Small uppercase or spaced label, ink or rust.
- `tm-smallcap`: form label, table head, quiet category.
- `tm-rule`, `tm-rule-thin`, `tm-rule-strong`: divider hierarchy.
- `tm-tag`, `tm-tag-rust`, `tm-tag-ink`: compact labels.
- `tm-btn-primary`: ink background, paper text, `2px` radius.
- `tm-btn-ghost`: transparent button with ink border.
- `tm-input`: transparent input with bottom border only.
- `tm-drop-zone`: dashed file upload area with subtle hover.

## Prohibitions

- Do not use rounded SaaS cards as the dominant structure.
- Do not use shadows for hierarchy.
- Do not introduce purple, blue, neon, or multi-color gradients as the main palette.
- Do not turn every module into a floating card.
- Do not use large border radius. Default radius is `2px`.
- Do not cram dense admin-table layouts into this style without adjusting spacing and hierarchy.
- Do not copy the preview HTML wholesale into Vue or NextJS. Extract the style language and rebuild idiomatically.
