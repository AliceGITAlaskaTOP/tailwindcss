# Transitions, Animations, Transforms

## Transitions

### Which properties
| Class | Properties |
|---|---|
| `transition` | bg-color, border-color, outline-color, color, fill, stroke, opacity, box-shadow, transform, translate, scale, rotate, filter, backdrop-filter, **display**, content-visibility, overlay, pointer-events (v4 default set) |
| `transition-all` | all properties |
| `transition-colors` | color-related only |
| `transition-opacity` | opacity |
| `transition-shadow` | box-shadow |
| `transition-transform` | transform/translate/scale/rotate |
| `transition-none` | disable |
| `transition-[<value>]` / `transition-(--my-list)` | custom |

### Behavior (v4 — for transitions on `display: none` and similar discrete properties)
`transition-discrete`, `transition-normal`. Lets `display`/`content-visibility` animate (e.g. for popovers).

### Duration
`duration-0`, `-75`, `-100`, `-150`, `-200`, `-300`, `-500`, `-700`, `-1000`. Arbitrary `duration-[450ms]`.

### Easing
`ease-linear`, `ease-in`, `ease-out`, `ease-in-out`, `ease-initial`. Custom via theme: `@theme { --ease-fluid: cubic-bezier(0.3,0,0,1); }` → `ease-fluid`. Arbitrary `ease-[cubic-bezier(.17,.67,.83,.67)]`.

### Delay
`delay-0/75/100/150/200/300/500/700/1000`. Arbitrary.

### Pattern
```html
<button class="bg-indigo-600 transition duration-200 ease-out
               hover:bg-indigo-500 hover:scale-105
               motion-reduce:transition-none motion-reduce:hover:scale-100">
  Hover me
</button>
```

## Animations

Built-in: `animate-none`, `animate-spin`, `animate-ping`, `animate-pulse`, `animate-bounce`.

### Custom animations via @theme
```css
@theme {
  --animate-wiggle: wiggle 0.6s ease-in-out infinite;
}
@keyframes wiggle {
  0%, 100% { transform: rotate(-3deg); }
  50%      { transform: rotate(3deg);  }
}
```
→ `animate-wiggle`.

Arbitrary: `animate-[shake_1s_ease-in-out_infinite]`.

---

## Transforms

The `transform` class is no longer required in v4 — transform utilities (translate/scale/rotate) work standalone.

### Scale
- `scale-0`, `-50`, `-75`, `-90`, `-95`, `-100`, `-105`, `-110`, `-125`, `-150`. Negative `-scale-100` (flip). Arbitrary `scale-[1.17]`.
- Axis-specific: `scale-x-*`, `scale-y-*`, `scale-z-*` (3D)
- `scale-3d`
- Shorthand for both: `scale-100` (no prefix sets all)

### Rotate
- `rotate-0`, `-1`, `-2`, `-3`, `-6`, `-12`, `-45`, `-90`, `-180`. Negative `-rotate-45`. Arbitrary `rotate-[17deg]`.
- 3D: `rotate-x-*`, `rotate-y-*`, `rotate-z-*`

### Translate
- `translate-x-*`, `translate-y-*` use spacing scale + fractions (`translate-x-1/2`), + `translate-x-full`, `translate-x-px`. Negative `-translate-y-4`.
- `translate-z-*` (3D)
- `translate-none`

### Skew
- `skew-x-0/1/2/3/6/12`, `skew-y-*`. Negative. Arbitrary `skew-x-[15deg]`.

### Transform origin
`origin-center` (default), `origin-top`, `origin-top-right`, `origin-right`, `origin-bottom-right`, `origin-bottom`, `origin-bottom-left`, `origin-left`, `origin-top-left`. Arbitrary `origin-[33%_75%]`.

### Transform style / backface / perspective (3D)
- `transform-3d`, `transform-flat`
- `backface-visible`, `backface-hidden`
- `perspective-dramatic`, `-near`, `-normal`, `-midrange`, `-distant`, `-none`. Arbitrary `perspective-[800px]`.
- `perspective-origin-*` (same set as transform-origin)

### Zoom (v4)
`zoom-0/50/75/90/95/100/105/110/125/150`. Visual scale that affects layout (unlike `scale-*`).

### Common patterns
```html
<!-- Lift on hover -->
<a class="transition hover:-translate-y-1 hover:shadow-lg">card</a>

<!-- Flip card -->
<div class="relative size-40 [perspective:600px]">
  <div class="absolute inset-0 transition-transform duration-500 transform-3d hover:rotate-y-180">
    <div class="absolute inset-0 backface-hidden">front</div>
    <div class="absolute inset-0 backface-hidden rotate-y-180">back</div>
  </div>
</div>

<!-- Spinner -->
<svg class="animate-spin size-5" .../>

<!-- Reduced motion respect -->
<div class="motion-safe:animate-bounce">...</div>
```
