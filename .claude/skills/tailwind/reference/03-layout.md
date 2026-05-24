# Layout

## Display
| Class | CSS |
|---|---|
| `block` `inline` `inline-block` `flow-root` | `display: ...` |
| `flex` `inline-flex` `grid` `inline-grid` | `display: ...` |
| `contents` | renders children as if parent didn't exist |
| `table` `inline-table` `table-caption` `table-cell` `table-column` `table-column-group` `table-footer-group` `table-header-group` `table-row-group` `table-row` | `display: table-*` |
| `list-item` | `display: list-item` |
| `hidden` | `display: none` |
| `sr-only` | visually hidden but readable to screen readers |
| `not-sr-only` | reverse of `sr-only` |

## Position
| Class | CSS |
|---|---|
| `static` | normal flow, offsets ignored |
| `relative` | offset from normal spot; ancestor for `absolute` children |
| `absolute` | removed from flow, offset from nearest non-static ancestor |
| `fixed` | offset from viewport |
| `sticky` | `relative` until scroll threshold, then `fixed` |

## Offsets — top / right / bottom / left
- `top-*`, `right-*`, `bottom-*`, `left-*` — spacing scale (0, 0.5, 1, …, 96)
- `inset-*` (all four), `inset-x-*` (left+right), `inset-y-*` (top+bottom)
- `start-*` / `end-*` — logical (RTL-aware)
- Negative: `-top-4`, `-inset-2`
- Special: `top-auto`, `top-px`, `top-full`, `top-1/2`, `top-1/3`, `top-2/3`, `top-1/4` etc.
- Arbitrary: `top-[117px]`, `inset-(--my-offset)`

## Z-index
`z-0`, `z-10`, `z-20`, `z-30`, `z-40`, `z-50`, `z-auto`. Arbitrary `z-[60]`. Negative `-z-10`.

## Visibility
`visible`, `invisible`, `collapse`. (`invisible` keeps space; `hidden` removes it.)

## Overflow
| Class | CSS |
|---|---|
| `overflow-auto` `overflow-hidden` `overflow-clip` `overflow-visible` `overflow-scroll` | both axes |
| `overflow-x-*` `overflow-y-*` | per axis |

## Overscroll behavior
`overscroll-auto`, `overscroll-contain`, `overscroll-none`, plus `overscroll-x-*` / `overscroll-y-*`.

## Aspect ratio
`aspect-auto`, `aspect-square` (1/1), `aspect-video` (16/9). Arbitrary `aspect-[4/3]`, `aspect-[2.35]`. Custom via `@theme { --aspect-portrait: 3/4; }` → `aspect-portrait`.

## Object fit & position
**Fit**: `object-contain`, `object-cover`, `object-fill`, `object-none`, `object-scale-down`.
**Position**: `object-top`, `object-top-right`, `object-right`, `object-bottom-right`, `object-bottom`, `object-bottom-left`, `object-left`, `object-top-left`, `object-center`. Arbitrary `object-[25%_75%]`.

## Box sizing
`box-border` (default — includes padding+border), `box-content`.

## Float / clear
`float-start`, `float-end`, `float-right`, `float-left`, `float-none`.
`clear-start`, `clear-end`, `clear-left`, `clear-right`, `clear-both`, `clear-none`.

## Columns
`columns-1` … `columns-12`, `columns-auto`, `columns-3xs`/`2xs`/`xs`/`sm`/`md`/`lg`/`xl`/`2xl`/.../`7xl`. Arbitrary `columns-[16rem]`.

## Break (column/page breaks)
- `break-before-*` and `break-after-*`: `auto`, `avoid`, `all`, `avoid-page`, `page`, `left`, `right`, `column`
- `break-inside-*`: `auto`, `avoid`, `avoid-page`, `avoid-column`

## Box decoration break
`box-decoration-slice` (default), `box-decoration-clone`. Useful for multi-line inline elements (highlighted text wrapping).

## Isolation
`isolate` (creates new stacking context), `isolation-auto`.
