# Agent Task: Implement Liquid Glass navbar transitions

## Objective

Add CSS-driven Liquid Glass transition effects to the existing top navigation:

1. The active glass indicator should glide and resize between About, Research, Publications, and CV during same-origin page navigation.
2. Navbar links should have restrained hover and press feedback.
3. The light/dark/system theme icon should transition through opacity, rotation, and scale instead of switching abruptly.

Treat this as progressive enhancement. Navigation and theme switching must remain fully functional when animation or the View Transition API is unavailable.

## Repository context

- Framework: Jekyll multi-page site using pinned al-folio v1.x gems.
- Site-specific Sass entry point: `assets/css/main.scss`.
- Navbar markup and theme-switch JavaScript are supplied by the theme gems.
- Global search is disabled.
- Desktop theme-toggle alignment currently depends on `#light-toggle { transform: translateY(8px); }`.
- The static glass surface design is specified separately in `LIQUID_GLASS_PLAN.md`.

Read `AGENTS.md` and `LIQUID_GLASS_PLAN.md` before editing. Inspect the current worktree and preserve unrelated changes.

## Scope

Primary implementation file:

- `assets/css/main.scss`

Do not introduce a SPA router, animation library, WebGL, canvas, or third-party dependency. Do not edit page content.

Use the existing DOM if possible. Do not add `_layouts/`, `_includes/`, or JavaScript unless the current theme markup makes the icon transition impossible. If a template or JavaScript change appears necessary, first identify the exact DOM or state limitation and keep any change minimal.

## Required behavior

### 1. Cross-document View Transition opt-in

Enable same-origin multi-page transitions in CSS:

```scss
@view-transition {
  navigation: auto;
}
```

Requirements:

- Apply the same named view transition to the single active navbar link on every page.
- Confirm the rendered markup has exactly one active nav item before assigning the name.
- Use a unique name such as `active-nav-glass`.
- Do not assign the same `view-transition-name` to multiple elements on one page.
- Keep unsupported browsers on the existing immediate-navigation behavior.

Starting selector:

```scss
#navbar .nav-item.active > .nav-link {
  view-transition-name: active-nav-glass;
}
```

Inspect the built HTML and adjust the selector if the theme marks active items differently.

### 2. Active glass indicator

Style the active navbar link as the moving glass surface.

Requirements:

- Use a low-opacity glass background, translucent border, inset highlight, and soft shadow.
- Keep the existing text color and font weight unless contrast testing requires a small adjustment.
- Use a moderate radius of approximately `0.55rem` to `0.8rem`.
- Do not change the existing link padding or navbar height.
- Allow the indicator width to follow the label width so the View Transition can interpolate its size.
- Avoid animated rainbow gradients, continuous shimmer, or exaggerated glow.

The active surface must remain visually subordinate to the page content.

### 3. View Transition animation

Customize only the named active indicator rather than animating the entire page.

Suggested starting rules:

```scss
::view-transition-group(active-nav-glass) {
  animation-duration: 380ms;
  animation-timing-function: cubic-bezier(0.22, 1, 0.36, 1);
}

::view-transition-old(active-nav-glass),
::view-transition-new(active-nav-glass) {
  height: 100%;
  mix-blend-mode: normal;
}
```

Tune within these limits:

- Duration: `320ms`–`420ms`.
- Easing: a smooth deceleration curve; no elastic overshoot beyond a few pixels.
- Opacity: the old and new indicator may cross-fade slightly, but the text must not appear doubled for a noticeable period.
- Scale: if used, keep within approximately `0.98`–`1.02`.

Do not animate the root page unless a short root cross-fade is necessary to prevent flashing. If added, keep it under `160ms` and verify that it does not make navigation feel slower.

### 4. Navbar link hover and press states

Add local interaction feedback independently of cross-page navigation.

For inactive links:

- Hover: introduce a faint glass tint and a small inset highlight.
- Active/press: reduce brightness or scale to approximately `0.98`.
- Keep transitions between `160ms` and `220ms`.
- Do not move links vertically; movement would disturb navbar alignment.

For the active link:

- Hover may slightly strengthen the glass highlight.
- Press feedback must not overwrite its `view-transition-name` or active-state surface.

Keyboard focus must continue to use the site's existing `:focus-visible` outline.

### 5. Theme icon transition

The theme supplies these icon elements inside `#light-toggle`:

- `#light-toggle-system`
- `#light-toggle-dark`
- `#light-toggle-light`

The imported theme currently controls them with `display: none` and `display: inline-block`. A continuous transition requires all three icons to occupy the same button footprint while visibility is controlled with `opacity`, `visibility`, and `transform`.

Implementation requirements:

- Keep `#light-toggle` as the containing block using `position: relative`.
- Place all three icons at the same center point with absolute positioning.
- Override the theme's `display` rules only as specifically as necessary.
- Hidden icons must use `opacity: 0`, `visibility: hidden`, and a small rotation/scale offset.
- The visible icon must use `opacity: 1`, `visibility: visible`, `rotate(0)`, and `scale(1)`.
- Preserve the theme's existing `data-theme-setting` state selectors.
- Use a duration of approximately `180ms`–`260ms`.
- Avoid a full 360-degree spin.
- Ensure hidden icons do not receive pointer events or appear to assistive technology as separate controls; the accessible control remains the parent button.

Suggested visual states:

- System icon: neutral scale with minimal rotation.
- Moon entering: rotate from approximately `-20deg`, scale from `0.82`.
- Sun entering: rotate from approximately `20deg`, scale from `0.82`.

Do not change the theme-switch order or JavaScript behavior.

### 6. Theme-toggle press feedback

Combine the theme icon transition with the existing glass-control surface from `LIQUID_GLASS_PLAN.md`.

Preserve the desktop vertical offset in every transform state:

```scss
@media (min-width: 576px) {
  #light-toggle {
    transform: translateY(8px);
  }

  #light-toggle:hover {
    transform: translateY(8px) scale(1.03);
  }

  #light-toggle:active {
    transform: translateY(8px) scale(0.97);
  }
}
```

On mobile, omit `translateY(8px)` and retain only the small scale feedback.

### 7. Reduced motion

Extend the existing `prefers-reduced-motion` block:

```scss
@media (prefers-reduced-motion: reduce) {
  @view-transition {
    navigation: none;
  }

  #navbar .nav-link,
  #light-toggle,
  #light-toggle i {
    transition: none !important;
  }
}
```

If nested `@view-transition` parsing is not supported by the Sass/CSS toolchain, keep `@view-transition { navigation: auto; }` globally and suppress the named transition animations through the View Transition pseudo-elements inside the reduced-motion query.

The final implementation must pass the actual Jekyll/Sass build; do not assume all at-rule nesting forms compile.

### 8. Browser fallback

- Browsers without cross-document View Transitions must still show the correct active glass indicator after normal navigation.
- Browsers without support for animating discrete properties should still switch theme icons correctly.
- Do not hide all theme icons if an advanced transition property is unsupported.
- The glass background fallback from `LIQUID_GLASS_PLAN.md` remains responsible for browsers without `backdrop-filter`.

## Implementation sequence

1. Inspect the rendered navbar HTML on Home, Research, Publications, and CV.
2. Inspect the imported theme rules for active navigation and all three theme-icon states.
3. Confirm there is exactly one active nav link on every target page.
4. Implement the static active glass surface.
5. Add the named cross-document View Transition.
6. Add inactive-link hover and press feedback.
7. Convert theme icons from abrupt `display` switching to overlapped opacity/transform states.
8. Add theme-toggle hover and press feedback while preserving the 8px desktop alignment.
9. Add reduced-motion behavior and compatibility fallbacks.
10. Build and visually verify every state before tuning durations or opacity.

## Validation commands

Run:

```bash
git diff --check
bundle exec jekyll build
```

Do not edit generated `_site/` files.

## Visual test matrix

Test at minimum:

| Viewport | Theme states | Navigation checks |
| --- | --- | --- |
| 1440 × 900 | light, dark, system | About → Research → Publications → CV → About |
| 1024 × 768 | light, dark | Forward navigation plus browser Back/Forward |
| 390 × 844 | light, dark | Expanded mobile menu and theme switching |
| 360 × 800 | light, dark | Narrow-menu wrapping and button hit areas |

For each supported browser, verify:

- The active glass indicator glides to the new link and resizes cleanly.
- Nav text does not duplicate, blur excessively, or jump vertically.
- The navbar does not resize during the transition.
- Browser Back and Forward navigation produces a coherent transition.
- Rapid navigation does not leave a stale active indicator.
- The theme icon rotates/fades without changing the button footprint.
- Switching light, dark, and system states does not flash multiple icons.
- Focus outlines remain visible during keyboard navigation.
- Reduced-motion mode removes movement.

Test at least one browser without cross-document View Transition support, or disable the feature in developer tools, and confirm normal navigation remains intact.

## Definition of done

- About, Research, Publications, and CV share one named active-nav transition.
- The active indicator moves and resizes in supporting browsers without converting the site to an SPA.
- Unsupported browsers retain correct static active states.
- Hover and press feedback is subtle and does not change layout.
- Theme icons transition smoothly inside a fixed button footprint.
- The theme-toggle button remains aligned with navbar labels, including its 8px desktop offset.
- Mobile navigation remains readable and operable.
- Reduced-motion users receive no new motion effects.
- No JavaScript library, routing layer, dependency, or broad theme override is added.
- `git diff --check` and `bundle exec jekyll build` pass.

## Handoff

Report:

- Exact selectors and View Transition names added.
- Any changes made outside `assets/css/main.scss` and the reason.
- Final animation durations and easing curves.
- Browsers, viewport sizes, and theme states checked.
- Behavior observed in unsupported browsers.
- Build result and any remaining compatibility limitation.
