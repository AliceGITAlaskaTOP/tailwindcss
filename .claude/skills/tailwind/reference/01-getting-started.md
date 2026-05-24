# Getting Started

## Installation (v4)

### Vite (recommended for React/Vue/Svelte/Solid/Qwik)

```bash
npm install tailwindcss @tailwindcss/vite
```

```ts
// vite.config.ts
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'
export default defineConfig({ plugins: [tailwindcss()] })
```

```css
/* src/index.css (or app.css) */
@import "tailwindcss";
```

Then `import "./index.css"` from the app entry.

### PostCSS

```bash
npm install tailwindcss @tailwindcss/postcss postcss
```

```js
// postcss.config.mjs
export default { plugins: { "@tailwindcss/postcss": {} } }
```

```css
@import "tailwindcss";
```

### Tailwind CLI

```bash
npm install tailwindcss @tailwindcss/cli
npx @tailwindcss/cli -i ./src/input.css -o ./dist/output.css --watch
```

### Play CDN (prototyping only)

```html
<script src="https://cdn.tailwindcss.com"></script>
```

### Framework guides

Next.js / Nuxt / Remix / SvelteKit / Astro / Laravel / Phoenix / Rails — see `https://tailwindcss.com/docs/installation/framework-guides`. Each has minor wiring differences but the CSS is always:

```css
@import "tailwindcss";
```

## Editor setup

- **VS Code**: install `bradlc.vscode-tailwindcss`. Enable autocomplete in JSX/TSX/Vue/Svelte. Add `"tailwindCSS.experimental.classRegex"` for `cva`, `clsx`, `cn`.
- **Prettier**: install `prettier-plugin-tailwindcss` for automatic class sorting.
- **JetBrains**: Tailwind plugin is built-in (enable in settings).

## Browser compatibility (v4)

Requires Safari 16.4+, Chrome 111+, Firefox 128+. Uses `@property`, `color-mix()`, cascade layers natively. **If you need older browsers, stay on v3.**

## v3 → v4 Upgrade

Run the automated tool first:

```bash
npx @tailwindcss/upgrade
```

It rewrites most of:

### CSS file
- `@tailwind base; @tailwind components; @tailwind utilities;` → `@import "tailwindcss";`
- Moves `tailwind.config.js` theme into a `@theme { ... }` block (or keeps the JS config via `@config "./tailwind.config.js";`).

### Class renames (apply across HTML/JSX)
| v3 | v4 |
|---|---|
| `shadow-sm` | `shadow-xs` |
| `shadow` | `shadow-sm` |
| `drop-shadow-sm` | `drop-shadow-xs` |
| `blur-sm` | `blur-xs` |
| `blur` | `blur-sm` |
| `rounded-sm` | `rounded-xs` |
| `rounded` | `rounded-sm` |
| `ring` (3px) | `ring-3` |
| `outline-none` | `outline-hidden` |
| `flex-shrink-*` | `shrink-*` |
| `flex-grow-*` | `grow-*` |
| `decoration-clone` | `box-decoration-clone` |
| `decoration-slice` | `box-decoration-slice` |
| `overflow-ellipsis` | `text-ellipsis` |
| `bg-gradient-to-r` | `bg-linear-to-r` |

### Opacity utilities removed
- ❌ `bg-opacity-50`, `text-opacity-50`, `border-opacity-50`, `placeholder-opacity-50`, `ring-opacity-50`, `divide-opacity-50`
- ✅ Use color/opacity syntax: `bg-black/50`, `text-gray-900/60`, `border-red-500/20`, etc.

### Important modifier moved to end
- v3: `<div class="!font-bold">`
- v4: `<div class="font-bold!">`

### CSS variable arbitrary values
- v3: `bg-[--brand]`
- v4: `bg-(--brand)` — parentheses, not brackets

### Commas → underscores in arbitrary values
- v3: `grid-cols-[max-content,auto]`
- v4: `grid-cols-[max-content_auto]`

### Default border color
- v3: defaulted to `gray-200`
- v4: defaults to `currentColor`. Either set explicitly (`border-gray-200`) or define `@theme { --default-border-color: var(--color-gray-200); }`.

### Default ring
- v3: `ring` was 3px blue with 50% opacity
- v4: `ring` is 1px `currentColor`. Use `ring-3 ring-blue-500/50` for old behavior.

### Hover only on hover-capable devices
v4's `hover:` uses `@media (hover: hover)` so it doesn't stick on touch devices. If you need always-on hover, write a custom variant.

### `@apply` in scoped CSS
In Vue `<style scoped>`, Svelte `<style>`, CSS Modules — utilities aren't in scope. Add at the top of that style block:
```css
@reference "../app.css";
```
Then `@apply` works as expected.

### No Sass/Less
Tailwind v4 is itself a preprocessor (Lightning CSS under the hood). Don't pipe through Sass.
