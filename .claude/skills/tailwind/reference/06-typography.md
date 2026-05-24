# Typography

## Font family
| Class | Default |
|---|---|
| `font-sans` | system UI sans stack |
| `font-serif` | system serif stack |
| `font-mono` | system mono stack |

Custom: `@theme { --font-display: "Satoshi", sans-serif; }` → `font-display`.

## Font size (also sets default line-height)
| Class | Size | Line height |
|---|---|---|
| `text-xs` | 12px | 16px |
| `text-sm` | 14px | 20px |
| `text-base` | 16px | 24px |
| `text-lg` | 18px | 28px |
| `text-xl` | 20px | 28px |
| `text-2xl` | 24px | 32px |
| `text-3xl` | 30px | 36px |
| `text-4xl` | 36px | 40px |
| `text-5xl` | 48px | 1 |
| `text-6xl` | 60px | 1 |
| `text-7xl` | 72px | 1 |
| `text-8xl` | 96px | 1 |
| `text-9xl` | 128px | 1 |

**Override line-height inline**: `text-lg/8` (= 32px line-height), `text-base/loose`.

Arbitrary: `text-[22px]`, `text-(length:--my-size)`.

## Font weight
`font-thin` (100), `font-extralight` (200), `font-light` (300), `font-normal` (400), `font-medium` (500), `font-semibold` (600), `font-bold` (700), `font-extrabold` (800), `font-black` (900). Arbitrary `font-[550]`.

## Font style
`italic`, `not-italic`.

## Font smoothing
`antialiased` (`-webkit-font-smoothing: antialiased`), `subpixel-antialiased`.

## Font stretch
`font-stretch-normal`, `-ultra-condensed`, `-extra-condensed`, `-condensed`, `-semi-condensed`, `-semi-expanded`, `-expanded`, `-extra-expanded`, `-ultra-expanded`. Percentage: `font-stretch-50%`–`font-stretch-200%`.

## Font variant numeric
`normal-nums`, `ordinal`, `slashed-zero`, `lining-nums`, `oldstyle-nums`, `proportional-nums`, `tabular-nums`, `diagonal-fractions`, `stacked-fractions`. Stackable: `tabular-nums slashed-zero`.

## Font feature settings
Arbitrary: `font-feature-settings-["ss01","cv11"]` or use a custom utility.

## Letter spacing (tracking)
`tracking-tighter` (-0.05em), `tracking-tight` (-0.025em), `tracking-normal` (0), `tracking-wide` (0.025em), `tracking-wider` (0.05em), `tracking-widest` (0.1em). Arbitrary `tracking-[0.18em]`.

## Line height (leading)
`leading-none` (1), `leading-tight` (1.25), `leading-snug` (1.375), `leading-normal` (1.5), `leading-relaxed` (1.625), `leading-loose` (2). Numeric: `leading-3` (12px) … `leading-10` (40px). Arbitrary `leading-[1.85]`.

## Line clamp (truncate to N lines)
`line-clamp-1` … `line-clamp-6`, `line-clamp-none`. Arbitrary `line-clamp-[10]`.

## List
- `list-disc`, `list-decimal`, `list-none` (style-type)
- `list-inside`, `list-outside` (position)
- Custom marker via `marker:` variant: `marker:text-blue-500`
- Image marker: `list-image-[url('/img/check.svg')]`, `list-image-none`

## Text align
`text-left`, `text-center`, `text-right`, `text-justify`, `text-start`, `text-end`.

## Color
`text-<color>-<shade>`, `text-black`, `text-white`, `text-transparent`, `text-current`, `text-inherit`. Opacity: `text-gray-900/60`. Arbitrary `text-[#fa0]`.

## Text decoration
- Line: `underline`, `overline`, `line-through`, `no-underline`
- Color: `decoration-<color>` (`decoration-pink-500/50`)
- Style: `decoration-solid`, `-double`, `-dotted`, `-dashed`, `-wavy`
- Thickness: `decoration-auto`, `-from-font`, `decoration-0`, `decoration-1`, `decoration-2`, `decoration-4`, `decoration-8`. Arbitrary `decoration-[3px]`.
- Underline offset: `underline-offset-auto`, `underline-offset-0/1/2/4/8`. Arbitrary.

## Text transform
`uppercase`, `lowercase`, `capitalize`, `normal-case`.

## Text overflow
`truncate` (= `overflow:hidden; text-overflow:ellipsis; white-space:nowrap` — single-line ellipsis), `text-ellipsis`, `text-clip`.

For multi-line ellipsis use `line-clamp-N`.

## Text wrap
`text-wrap` (default), `text-nowrap`, `text-balance` (`text-wrap: balance` — great for headings), `text-pretty` (`text-wrap: pretty` — better paragraph breaks).

## Text indent
`indent-*` (spacing scale), `-indent-*` (negative), arbitrary.

## Tab size
`tab-1`, `tab-2`, `tab-4`, `tab-8`. Arbitrary.

## Vertical align
`align-baseline`, `-top`, `-middle`, `-bottom`, `-text-top`, `-text-bottom`, `-sub`, `-super`. Arbitrary.

## White space
`whitespace-normal`, `-nowrap`, `-pre`, `-pre-line`, `-pre-wrap`, `-break-spaces`.

## Word break / overflow wrap / hyphens
- `break-normal`, `break-words` (= `overflow-wrap: break-word`), `break-all`, `break-keep`
- `wrap-normal`, `wrap-break-word`, `wrap-anywhere`
- `hyphens-none`, `hyphens-manual`, `hyphens-auto`

## Content (for `before:`/`after:` pseudo-elements)
- `content-none` removes
- Arbitrary string: `before:content-['*']`, `after:content-['→']`
- From attribute: `content-[attr(data-tooltip)]`
- From CSS var: `content-(--my-content)`

## Plugin: `@tailwindcss/typography` (prose)
Adds `prose`, `prose-sm`, `prose-lg`, `prose-xl`, `prose-2xl`, color variants like `prose-slate`, `prose-invert` (for dark backgrounds). Use on long-form markdown/CMS content:
```html
<article class="prose prose-lg dark:prose-invert max-w-none">{markdown HTML}</article>
```
Override individual elements via `prose-headings:`, `prose-p:`, `prose-a:`, `prose-img:`, etc.

## Plugin: `@tailwindcss/forms`
Resets form controls so utility styles actually apply. Install:
```css
@plugin "@tailwindcss/forms";
```

## Common heading recipe
```html
<h1 class="text-4xl sm:text-5xl font-bold tracking-tight text-balance">...</h1>
<p  class="mt-4 text-lg text-gray-600 dark:text-gray-400 text-pretty">...</p>
```
