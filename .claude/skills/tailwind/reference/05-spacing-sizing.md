# Spacing & Sizing

## The spacing scale (v4)

v4 derives everything from a single `--spacing` variable (default `0.25rem` = 4px). Every integer step `n` resolves to `calc(0.25rem * n)`.

Common values:
| Class | Value |
|---|---|
| `*-0` | 0 |
| `*-px` | 1px |
| `*-0.5` | 2px |
| `*-1` | 4px |
| `*-1.5` | 6px |
| `*-2` | 8px |
| `*-2.5` | 10px |
| `*-3` | 12px |
| `*-3.5` | 14px |
| `*-4` | 16px |
| `*-5` | 20px |
| `*-6` | 24px |
| `*-7` | 28px |
| `*-8` | 32px |
| `*-9` | 36px |
| `*-10` | 40px |
| `*-11` | 44px |
| `*-12` | 48px |
| `*-14` | 56px |
| `*-16` | 64px |
| `*-20` | 80px |
| `*-24` | 96px |
| `*-28` | 112px |
| `*-32` | 128px |
| `*-36` | 144px |
| `*-40` | 160px |
| `*-44` | 176px |
| `*-48` | 192px |
| `*-52` | 208px |
| `*-56` | 224px |
| `*-60` | 240px |
| `*-64` | 256px |
| `*-72` | 288px |
| `*-80` | 320px |
| `*-96` | 384px |

Override the base: `@theme { --spacing: 1px; }` makes everything pixel-perfect (`p-16` = 16px).

## Padding
- `p-*` (all sides), `px-*` (inline), `py-*` (block)
- Individual: `pt-*`, `pr-*`, `pb-*`, `pl-*`
- Logical: `ps-*` (start), `pe-*` (end), `pbs-*` (block-start), `pbe-*` (block-end)
- Arbitrary: `p-[7px]`, `p-(--my-pad)`

## Margin
- Same pattern: `m-*`, `mx-*`, `my-*`, `mt/mr/mb/ml-*`, `ms/me-*`, `mbs/mbe-*`
- **Negative**: `-m-4`, `-mt-2`, `-mx-[7px]`
- `m-auto`, `mx-auto` (center block element with `width` set)

## Space between (sibling spacing)
- `space-x-*` adds `margin-left` to siblings (gap between row items)
- `space-y-*` adds `margin-top` to siblings
- Reverse: `space-x-reverse`, `space-y-reverse` (for `flex-row-reverse` etc.)
- Modern alternative: use `flex` / `grid` + `gap-*`. Prefer `gap` when possible.

## Width
| Pattern | Generates |
|---|---|
| `w-<n>` | from spacing scale (`w-64` = 256px) |
| `w-1/2`, `w-1/3`, `w-2/3`, `w-1/4`, `w-3/4`, `w-1/5`, … `w-11/12` | fractions of parent |
| `w-full` | 100% |
| `w-screen` | 100vw |
| `w-dvw` `w-svw` `w-lvw` | dynamic / small / large viewport width |
| `w-min` `w-max` `w-fit` | content-based |
| `w-auto` | `auto` |
| `w-px` | 1px |
| `w-xs` `w-sm` `w-md` `w-lg` `w-xl` `w-2xl` … `w-7xl` | container scale (16rem–80rem) |
| `w-[317px]` `w-(--my-w)` | arbitrary |

## Height
Same patterns: `h-<n>`, `h-full`, `h-screen`, `h-dvh` (dynamic viewport — recommended for mobile), `h-svh`, `h-lvh`, `h-min`, `h-max`, `h-fit`, `h-auto`, `h-px`.

## Min / max width & height
- `min-w-*`, `min-h-*`: same scale + `min-w-0` (critical for flex overflow fix), `min-w-full`, `min-w-min`, `min-w-max`, `min-w-fit`
- `max-w-*`: same + readability presets `max-w-prose` (~65ch), `max-w-screen-sm/md/lg/xl/2xl`
- `max-h-*`: same plus `max-h-screen`, `max-h-dvh`

## Size (sets both width and height)
- `size-<n>`, `size-full`, `size-px`, `size-1/2`, `size-auto`, `size-fit`, `size-min`, `size-max`
- Common for icons: `size-4`, `size-5`, `size-6`

## Logical sizes
- `inline-size-*`, `min-inline-size-*`, `max-inline-size-*`
- `block-size-*`, `min-block-size-*`, `max-block-size-*`
Useful for writing-mode-aware layouts.

## Common gotchas
- **Flex item overflowing parent?** Add `min-w-0` (and/or `min-h-0`) — flex items have `min-width: auto` by default which prevents shrinking below content size.
- **Truncate inside flex?** `flex-1 min-w-0` on the parent of the truncating text.
- **Full viewport height on mobile broken by URL bar?** Use `h-dvh` instead of `h-screen`.
- **`w-screen` causes horizontal scroll?** Includes scrollbar width. Use `w-full` inside a centered container instead.
