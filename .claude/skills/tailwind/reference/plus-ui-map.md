# Tailwind Plus & UI Blocks — Catalog + Build-It-Yourself Patterns

**LICENSE NOTE.** Tailwind Plus / UI Blocks code is paid content under Tailwind Labs' EULA. The category names below are public marketing info, but the **HTML/JSX of each block is licensed only to paying customers**. Never copy Plus block source code into shared or public repositories. If the user is logged in and asks for a specific block in their private project, you may `WebFetch` it from `tailwindcss.com/plus/...` and use it there.

When a paid block isn't available, **build the equivalent** from utilities using the patterns at the bottom of this file.

---

## Full Catalog

### Application UI (`tailwindcss.com/plus/ui-blocks/application-ui`)

**Application Shells**
- Stacked Layouts
- Sidebar Layouts
- Multi-Column Layouts

**Headings**
- Page Headings
- Card Headings
- Section Headings

**Data Display**
- Description Lists
- Stats
- Calendars

**Lists**
- Stacked Lists
- Tables
- Grid Lists
- Feeds

**Forms**
- Form Layouts
- Input Groups
- Select Menus
- Sign-in & Registration
- Textareas
- Radio Groups
- Checkboxes
- Toggles
- Action Panels
- Comboboxes

**Feedback**
- Alerts
- Empty States

**Navigation**
- Navbars
- Pagination
- Tabs
- Vertical Navigation
- Sidebar Navigation
- Breadcrumbs
- Progress Bars
- Command Palettes

**Overlays**
- Modal Dialogs
- Drawers
- Notifications

**Elements**
- Avatars
- Badges
- Dropdowns
- Buttons
- Button Groups

**Layout**
- Containers
- Cards
- List Containers
- Media Objects
- Dividers

**Page Examples**
- Home Screens
- Detail Screens
- Settings Screens

### Marketing (`tailwindcss.com/plus/ui-blocks/marketing`)

**Page Sections** — Hero Sections · Feature Sections · CTA Sections · Bento Grids · Pricing Sections · Header Sections · Newsletter Sections · Stats · Testimonials · Blog Sections · Contact Sections · Team Sections · Content Sections · Logo Clouds · FAQs · Footers

**Elements** — Headers · Flyout Menus · Banners

**Feedback** — 404 Pages

**Page Examples** — Landing Pages · Pricing Pages · About Pages

### Ecommerce (`tailwindcss.com/plus/ui-blocks/ecommerce`)

**Components** — Product Overviews · Product Lists · Category Previews · Shopping Carts · Category Filters · Product Quickviews · Product Features · Store Navigation · Promo Sections · Checkout Forms · Reviews · Order Summaries · Order History · Incentives

**Page Examples** — Storefront · Product · Category · Shopping Cart · Checkout · Order Detail · Order History

### Templates (`tailwindcss.com/plus/templates`)
| Template | Purpose |
|---|---|
| **Catalyst** | React UI kit (components library) |
| **Spotlight** | Personal website |
| **Salient** | SaaS landing page |
| **Studio** | Agency site |
| **Protocol** | API reference docs |
| **Syntax** | Documentation site |
| **Commit** | Changelog |
| **Transmit** | Podcast site |
| **Pocket** | App marketing |
| **Keynote** | Conference site |
| **Primer** | Course/ebook info product |
| **Compass** | Course template |
| **Radiant** | SaaS marketing |
| **Oatmeal** | SaaS marketing kit (multi-theme) |

All built with React + Next.js (TypeScript).

### Headless UI library
For interactivity primitives (Dialog, Combobox, Tabs, Listbox, Disclosure, Popover, RadioGroup, Switch, Transition), use `@headlessui/react` or `@headlessui/vue`. **MIT-licensed, free** — pair with Tailwind utilities for styling.

---

## Build-it-yourself patterns

If you can't (or shouldn't) paste a Plus block, here are minimal, correct, accessible Tailwind v4 starting points.

### Button (primary)
```html
<button class="inline-flex items-center justify-center gap-2 rounded-md
               bg-indigo-600 px-4 py-2 text-sm font-medium text-white shadow-sm
               transition hover:bg-indigo-500
               focus:outline-none focus-visible:ring-2 focus-visible:ring-indigo-500 focus-visible:ring-offset-2
               disabled:cursor-not-allowed disabled:opacity-50">
  Save changes
</button>
```

### Card
```html
<article class="rounded-2xl border border-gray-200 bg-white p-6 shadow-sm
                dark:border-gray-800 dark:bg-gray-900">
  <h3 class="text-lg font-semibold text-gray-900 dark:text-white">Title</h3>
  <p class="mt-2 text-sm text-gray-600 dark:text-gray-400">Body copy.</p>
</article>
```

### Hero section
```html
<section class="relative isolate overflow-hidden bg-white dark:bg-gray-950">
  <div class="mx-auto max-w-7xl px-6 py-24 sm:py-32 lg:px-8">
    <div class="mx-auto max-w-2xl text-center">
      <h1 class="text-4xl font-bold tracking-tight text-balance text-gray-900 sm:text-6xl dark:text-white">
        Headline that converts
      </h1>
      <p class="mt-6 text-lg text-pretty text-gray-600 dark:text-gray-400">
        One-sentence value prop.
      </p>
      <div class="mt-10 flex items-center justify-center gap-4">
        <a href="#" class="rounded-md bg-indigo-600 px-5 py-2.5 text-sm font-semibold text-white hover:bg-indigo-500">Get started</a>
        <a href="#" class="text-sm font-semibold text-gray-900 dark:text-white">Learn more →</a>
      </div>
    </div>
  </div>
</section>
```

### Responsive navbar (with mobile menu placeholder)
```html
<header class="bg-white shadow-sm dark:bg-gray-900">
  <nav class="mx-auto flex max-w-7xl items-center justify-between p-4 lg:px-8">
    <a href="#" class="font-bold text-xl">Logo</a>
    <div class="hidden lg:flex lg:gap-x-8">
      <a href="#" class="text-sm font-medium hover:text-indigo-600">Product</a>
      <a href="#" class="text-sm font-medium hover:text-indigo-600">Pricing</a>
      <a href="#" class="text-sm font-medium hover:text-indigo-600">About</a>
    </div>
    <button class="lg:hidden inline-flex items-center p-2 rounded hover:bg-gray-100">
      <span class="sr-only">Open menu</span>
      <!-- hamburger SVG -->
    </button>
  </nav>
</header>
```

### Card grid (auto-fit, no breakpoints)
```html
<div class="grid gap-6 grid-cols-[repeat(auto-fit,minmax(240px,1fr))]">
  <article class="rounded-xl bg-white p-6 shadow">…</article>
  <!-- repeat -->
</div>
```

### Pricing card
```html
<div class="rounded-3xl ring-1 ring-gray-200 p-8 dark:ring-gray-800">
  <h3 class="text-lg font-semibold">Pro</h3>
  <p class="mt-4 flex items-baseline gap-1">
    <span class="text-4xl font-bold">$29</span>
    <span class="text-sm text-gray-500">/ month</span>
  </p>
  <ul class="mt-6 space-y-3 text-sm">
    <li class="flex gap-2"><svg class="size-5 text-indigo-600">…</svg> Feature A</li>
    <li class="flex gap-2"><svg class="size-5 text-indigo-600">…</svg> Feature B</li>
  </ul>
  <button class="mt-8 w-full rounded-md bg-indigo-600 py-2 text-white">Buy</button>
</div>
```

### Form layout
```html
<form class="space-y-6 max-w-md">
  <div>
    <label for="email" class="block text-sm font-medium">Email</label>
    <input id="email" type="email" required
           class="mt-2 block w-full rounded-md border-0 bg-white px-3 py-2 ring-1 ring-inset ring-gray-300
                  focus:ring-2 focus:ring-indigo-600
                  dark:bg-gray-900 dark:ring-gray-700" />
  </div>
  <button type="submit" class="w-full rounded-md bg-indigo-600 px-4 py-2 text-white">Sign in</button>
</form>
```

### Modal (with Headless UI Dialog)
```jsx
import { Dialog } from '@headlessui/react'
<Dialog open={open} onClose={setOpen} className="relative z-50">
  <div className="fixed inset-0 bg-black/40 backdrop-blur-sm" />
  <div className="fixed inset-0 flex items-center justify-center p-4">
    <Dialog.Panel className="w-full max-w-md rounded-2xl bg-white p-6 shadow-xl dark:bg-gray-900">
      <Dialog.Title className="text-lg font-semibold">Title</Dialog.Title>
      <p className="mt-2 text-sm text-gray-600">Description</p>
      <div className="mt-6 flex justify-end gap-3">
        <button onClick={() => setOpen(false)} className="rounded-md px-3 py-2 text-sm">Cancel</button>
        <button className="rounded-md bg-indigo-600 px-3 py-2 text-sm text-white">Confirm</button>
      </div>
    </Dialog.Panel>
  </div>
</Dialog>
```

### Tabs (Headless UI)
```jsx
import { Tab } from '@headlessui/react'
<Tab.Group>
  <Tab.List className="flex gap-1 rounded-xl bg-gray-100 p-1 dark:bg-gray-800">
    {['Tab 1','Tab 2','Tab 3'].map(t => (
      <Tab key={t} className={({selected}) =>
        `flex-1 rounded-lg px-3 py-1.5 text-sm font-medium
         ${selected ? 'bg-white shadow text-indigo-700 dark:bg-gray-900' : 'text-gray-600 hover:bg-white/50'}`
      }>{t}</Tab>
    ))}
  </Tab.List>
  <Tab.Panels className="mt-4">
    <Tab.Panel>Panel 1</Tab.Panel>
    <Tab.Panel>Panel 2</Tab.Panel>
    <Tab.Panel>Panel 3</Tab.Panel>
  </Tab.Panels>
</Tab.Group>
```

### Notification toast
```html
<div role="status" class="pointer-events-auto w-full max-w-sm overflow-hidden rounded-lg bg-white shadow-lg ring-1 ring-black/5 dark:bg-gray-900 dark:ring-white/10">
  <div class="p-4 flex gap-3">
    <svg class="size-6 text-green-500 shrink-0">…</svg>
    <div class="flex-1 min-w-0">
      <p class="text-sm font-medium">Saved successfully</p>
      <p class="mt-1 text-sm text-gray-500">Your changes are live.</p>
    </div>
    <button class="text-gray-400 hover:text-gray-500"><span class="sr-only">Close</span>×</button>
  </div>
</div>
```

### Stat card
```html
<div class="rounded-xl bg-white p-6 shadow ring-1 ring-gray-100">
  <p class="text-sm font-medium text-gray-500">Total revenue</p>
  <p class="mt-2 flex items-baseline gap-2">
    <span class="text-3xl font-bold">$405,091</span>
    <span class="text-sm font-medium text-green-600">+4.75%</span>
  </p>
</div>
```

### Sidebar layout (app shell)
```html
<div class="flex h-dvh">
  <aside class="hidden lg:flex lg:w-64 lg:flex-col lg:border-r lg:bg-white">
    <nav class="flex-1 space-y-1 p-4">
      <a class="block rounded px-3 py-2 text-sm font-medium bg-gray-100 text-gray-900">Dashboard</a>
      <a class="block rounded px-3 py-2 text-sm font-medium text-gray-600 hover:bg-gray-50">Team</a>
    </nav>
  </aside>
  <div class="flex-1 flex flex-col min-w-0">
    <header class="border-b bg-white p-4">Top bar</header>
    <main class="flex-1 overflow-auto p-6 bg-gray-50">Content</main>
  </div>
</div>
```

### Pricing bento (auto-spanning)
```html
<div class="grid grid-cols-1 sm:grid-cols-3 grid-rows-2 gap-4">
  <div class="sm:col-span-2 sm:row-span-2 rounded-2xl bg-indigo-600 p-8 text-white">Big feature</div>
  <div class="rounded-2xl bg-white p-6 shadow">Feature</div>
  <div class="rounded-2xl bg-white p-6 shadow">Feature</div>
</div>
```

### Footer
```html
<footer class="border-t bg-white dark:border-gray-800 dark:bg-gray-950">
  <div class="mx-auto max-w-7xl px-6 py-12 lg:px-8">
    <div class="grid grid-cols-2 gap-8 md:grid-cols-4">
      <!-- columns -->
    </div>
    <p class="mt-8 text-xs text-gray-500">© 2026 Acme.</p>
  </div>
</footer>
```

---

## When you need a Plus block specifically
1. Confirm the user has a Tailwind Plus subscription (don't assume).
2. Use `WebFetch` on `https://tailwindcss.com/plus/ui-blocks/<category>/<block-slug>` — the page may show a preview/demo HTML if accessible.
3. Use it only inside the user's private project. Do not commit to a public repo or share verbatim.
4. If unsure about license — default to building from the patterns above.
