# Interactivity

## Cursor
`cursor-auto`, `cursor-default`, `cursor-pointer`, `cursor-wait`, `cursor-text`, `cursor-move`, `cursor-help`, `cursor-not-allowed`, `cursor-none`, `cursor-context-menu`, `cursor-progress`, `cursor-cell`, `cursor-crosshair`, `cursor-vertical-text`, `cursor-alias`, `cursor-copy`, `cursor-no-drop`, `cursor-grab`, `cursor-grabbing`, `cursor-all-scroll`, `cursor-col-resize`, `cursor-row-resize`, `cursor-n-resize`, `cursor-e-resize`, `cursor-s-resize`, `cursor-w-resize`, `cursor-ne-resize`, `cursor-nw-resize`, `cursor-se-resize`, `cursor-sw-resize`, `cursor-ew-resize`, `cursor-ns-resize`, `cursor-nesw-resize`, `cursor-nwse-resize`, `cursor-zoom-in`, `cursor-zoom-out`. Arbitrary `cursor-[url(hand.cur),_pointer]`.

## Pointer events
`pointer-events-none`, `pointer-events-auto`.

## User select
`select-none`, `select-text`, `select-all`, `select-auto`.

## Resize (textarea handle)
`resize-none`, `resize-y`, `resize-x`, `resize`.

## Appearance
`appearance-none` (strip native styles), `appearance-auto`.

## Caret color
`caret-<color>` (e.g., `caret-blue-500`).

## Accent color (checkboxes, radio, range)
`accent-<color>` (`accent-indigo-600`), `accent-auto`.

## Color scheme
`scheme-normal`, `scheme-dark`, `scheme-light`, `scheme-light-dark`, `scheme-only-dark`, `scheme-only-light`. Hints the browser for native UI (scrollbars, form controls).

## Field sizing
`field-sizing-content` (textarea grows with content), `field-sizing-fixed`.

## Scroll behavior
`scroll-auto`, `scroll-smooth`.

## Scroll margin / padding (for scroll snap & anchor offsets)
- `scroll-m-*`, `scroll-mx/y-*`, `scroll-mt/mr/mb/ml-*`, `scroll-ms/me-*` (logical), negative `-scroll-m-4`
- `scroll-p-*` and same axes/sides

## Scroll snap
- Container: `snap-x`, `snap-y`, `snap-both`, `snap-none`
- Strictness: `snap-mandatory`, `snap-proximity`
- Child alignment: `snap-start`, `snap-center`, `snap-end`, `snap-align-none`
- `snap-normal`, `snap-always` (stop strictness)
- `snap-stop-normal`, `snap-stop-always`

### Carousel recipe
```html
<div class="flex snap-x snap-mandatory overflow-x-auto scroll-smooth">
  <div class="snap-start shrink-0 w-full">Slide 1</div>
  <div class="snap-start shrink-0 w-full">Slide 2</div>
  <div class="snap-start shrink-0 w-full">Slide 3</div>
</div>
```

## Scrollbar
- Color: `scrollbar-thumb-<color>`, `scrollbar-track-<color>` (Firefox + Safari modern)
- Width: `scrollbar-thin`, `scrollbar-none`, `scrollbar-auto`
- Gutter: `scrollbar-gutter-auto`, `scrollbar-gutter-stable`, `scrollbar-gutter-stable-both-edges`

## Touch action
`touch-auto`, `touch-none`, `touch-pan-x`, `touch-pan-y`, `touch-pan-left`, `touch-pan-right`, `touch-pan-up`, `touch-pan-down`, `touch-pinch-zoom`, `touch-manipulation` (disables double-tap zoom — recommended for buttons).

## Will change
`will-change-auto`, `will-change-scroll`, `will-change-contents`, `will-change-transform`. Use sparingly — hints to browser to optimize, but overuse hurts.

## Common patterns
```html
<!-- Button (fully styled, accessible) -->
<button class="inline-flex items-center gap-2 rounded-md bg-indigo-600 px-4 py-2 text-sm font-medium text-white
               touch-manipulation transition
               hover:bg-indigo-500
               focus:outline-none focus-visible:ring-2 focus-visible:ring-indigo-500 focus-visible:ring-offset-2
               disabled:cursor-not-allowed disabled:opacity-50">
  Action
</button>

<!-- Custom checkbox accent -->
<input type="checkbox" class="size-4 accent-indigo-600">

<!-- Auto-growing textarea -->
<textarea class="field-sizing-content resize-none w-full p-2"></textarea>
```
