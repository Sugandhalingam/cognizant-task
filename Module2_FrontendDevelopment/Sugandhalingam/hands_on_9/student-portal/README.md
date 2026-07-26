# Student Portal — Accessibility & Cross-Browser Edition

A plain HTML/CSS/JS Student Portal built to satisfy the WCAG 2.1 / cross-browser hands-on.
No build step — just open `index.html` directly, or serve the folder with any static server.

```bash
# either just open the file
open index.html      # macOS
start index.html      # Windows

# or serve it (recommended so the css-vars-ponyfill CDN script and relative
# asset paths behave exactly like a real deployment)
npx serve .
```

## What's already done in this file

- **Semantic structure & headings**: `h1` → `h2` (Courses, Profile) → `h3` (Basic details,
  Contact preference) with no skipped levels; `<nav>`, `<main>`, `<footer>` landmarks.
- **Alt text**: the header logo has descriptive alt text; the small title flourish next to
  the `h1` uses `alt=""` since it's purely decorative — both patterns are commented inline
  in `index.html`.
- **Labels**: every input (search box, name, email, semester, contact-preference radios)
  has a real `<label for="...">` (or is wrapped in a `<fieldset>`/`<legend>` for the radio
  group).
- **Keyboard-accessible cards**: each course `<li class="course-card">` has `tabindex="0"`
  and a `keydown` handler in `script.js` so Enter/Space on the focused card enrolls, in
  addition to the real `<button>` inside it.
- **ARIA**: `<nav aria-label="Main navigation">`, `aria-current="page"` on the active link,
  `role="status" aria-live="polite"` on the results-count text (updates as you type in
  search) and on the profile save confirmation, `aria-expanded` toggled on the mobile nav
  button in `script.js`.
- **Focus visibility**: `:focus-visible` outline defined in `style.css` — never removed.
- **Colour contrast**: documented before/after hex values and ratios in the comment at the
  top of `style.css`, checked against the 4.5:1 AA threshold.
- **Feature detection**: `@supports (gap: 1rem)` in `style.css` so the flex/grid layouts
  degrade to margin-based spacing on browsers without `gap` support, instead of relying on
  browser-sniffing.
- **Polyfill**: `css-vars-ponyfill` is loaded from a CDN at the bottom of `index.html` with
  `onlyLegacy: true`, so it only does work on browsers that actually lack CSS custom
  property support.

## What you still need to do yourself (these require your own browser)

The hands-on explicitly asks you to *run* these tools and record *your* results — that's
the point of the exercise, and it can't be done from here. Steps:

1. **Lighthouse score**: open `index.html` in Chrome → DevTools → Lighthouse →
   Accessibility → Generate report. Replace the two `[[ ... ]]` placeholders at the top of
   `index.html` with your real before/after scores. (This version's HTML is written to
   already avoid the common baseline failures — missing alt, missing labels, skipped
   headings, div-as-button — but Lighthouse will still flag anything it finds, so run it
   for real and record what it says.)
2. **axe DevTools**: install the axe DevTools Chrome extension, run it on the page, and
   note any violations it surfaces that Lighthouse didn't.
3. **Contrast spot-check**: pick a couple of colour pairs from `style.css` and re-verify
   them yourself at https://webaim.org/resources/contrastchecker/ to confirm the logged
   ratios.
4. **Cross-browser check**: open the same `index.html` in Firefox and Safari/Edge, tab
   through the page, and note any visual differences (the comment blocks in `style.css`
   are where you'd log findings from step 135/136 of the hands-on).
5. **caniuse.com**: the CSS-Grid/flex-`gap` findings are pre-filled in the comment at the
   top of `style.css` — double check them against https://caniuse.com/mdn-css_properties_gap
   yourself and adjust the note if anything's changed.
6. **DevTools emulation**: use Chrome DevTools' device toolbar / "More tools > Rendering"
   to simulate an older browser and confirm `css-vars-ponyfill` kicks in (check the
   Network tab for the script, and the Console for any ponyfill log output).
