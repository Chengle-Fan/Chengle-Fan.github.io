# Agent Task: Implement a restrained Liquid Glass treatment

## Objective

Implement a CSS-only Liquid Glass treatment for the site's navigation and primary interactive controls. Preserve the current academic visual hierarchy, typography, content layout, light/dark theme behavior, and mobile navigation.

The result should suggest glass through translucency, backdrop blur, subtle gradients, edge highlights, and soft shadows. Do not attempt shader-based refraction or animated distortion.

## Repository context

- Framework: Jekyll with the pinned al-folio v1.x gem theme.
- Site-specific Sass entry point: `assets/css/main.scss`.
- Theme partials are imported before the site's custom rules in that file.
- The navbar HTML and theme-switch behavior are owned by the pinned theme gems.
- The desktop theme toggle currently uses `#light-toggle { transform: translateY(8px); }` for visual alignment. Preserve that final vertical position.
- The global search feature is disabled.
- Required validation command: `bundle exec jekyll build`.

Read `AGENTS.md` before editing. Inspect the current worktree and preserve unrelated user changes.

## Scope

Modify only:

- `assets/css/main.scss`

Do not add or modify `_layouts/`, `_includes/`, JavaScript, dependencies, page content, or configuration unless the existing DOM makes the CSS-only implementation impossible. If a template override becomes unavoidable, stop and report the exact blocker instead of creating the override.

## Required behavior

### 1. Theme tokens

Add dedicated glass tokens to the existing light and dark theme variable blocks. Start with the following values and tune only when visual QA shows a concrete contrast or layering issue:

```scss
:root {
  --glass-bg: rgba(248, 252, 255, 0.72);
  --glass-bg-strong: rgba(248, 252, 255, 0.88);
  --glass-border: rgba(255, 255, 255, 0.72);
  --glass-highlight: rgba(255, 255, 255, 0.82);
  --glass-shadow: rgba(31, 60, 86, 0.14);
  --glass-control-bg: rgba(255, 255, 255, 0.32);
  --glass-blur: 18px;
}

html[data-theme="dark"] {
  --glass-bg: rgba(23, 35, 49, 0.72);
  --glass-bg-strong: rgba(23, 35, 49, 0.9);
  --glass-border: rgba(180, 211, 235, 0.2);
  --glass-highlight: rgba(220, 239, 255, 0.16);
  --glass-shadow: rgba(0, 0, 0, 0.34);
  --glass-control-bg: rgba(151, 202, 236, 0.1);
}
```

Do not replace the site's existing global color tokens. The new tokens must layer on top of them.

### 2. Navbar

Apply the primary glass treatment to `#navbar`.

Requirements:

- Use a translucent background with a subtle vertical or diagonal gradient.
- Apply both `backdrop-filter` and `-webkit-backdrop-filter`.
- Use blur plus moderate saturation; avoid extreme color amplification.
- Replace the current hard divider with a translucent border.
- Add one soft outer shadow and one subtle inset top highlight.
- Keep navbar dimensions and content positions stable.
- Do not introduce a full-width colorful background solely to make the blur visible.
- Keep nav labels readable over both light and dark page content.
- Preserve the current fixed-navbar behavior.

Suggested starting point:

```scss
#navbar {
  background:
    linear-gradient(135deg, var(--glass-highlight), transparent 42%),
    var(--glass-bg);
  border-bottom: 1px solid var(--glass-border);
  box-shadow:
    inset 0 1px 0 var(--glass-highlight),
    0 8px 28px var(--glass-shadow);
  backdrop-filter: blur(var(--glass-blur)) saturate(145%);
  -webkit-backdrop-filter: blur(var(--glass-blur)) saturate(145%);
}
```

Adjust the gradient opacity if it reduces nav-label contrast. Do not add animated sheen.

### 3. Current navigation item

Give the active nav item a quiet glass selection state.

- Target the theme's actual active-nav selector after inspecting the rendered markup.
- Use a low-opacity background, a thin translucent border, and a small radius.
- Do not change the text label, font weight, nav order, or link padding.
- Avoid a large pill that visually competes with the page content.

### 4. Theme toggle

Apply a compact glass-control treatment to `#light-toggle`.

- Keep its existing fixed width and height.
- Add a translucent circular background, a thin border, an inset highlight, and a small shadow.
- Retain the current icon colors and theme-switch logic.
- Preserve the final desktop `translateY(8px)` alignment.
- Hover may slightly brighten the background and increase scale to at most `1.03`.
- Active may reduce the shadow and scale to approximately `0.97`.
- Use short transitions, approximately 160–220 ms.
- Combine transforms carefully so hover/active rules do not overwrite the required vertical translation.

For example, the desktop hover transform must include both operations:

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

### 5. Primary and secondary action buttons

Apply a restrained glass treatment to the existing `.button-primary` and `.button-secondary` controls.

- Keep current dimensions, typography, and semantic color hierarchy.
- Primary buttons should retain the site's blue accent with a translucent blue gradient.
- Secondary buttons should use the neutral glass tokens.
- Add a thin border, inset highlight, and soft shadow.
- Keep text contrast sufficient in both themes.
- Hover and active feedback should match the theme-toggle timing.
- Do not apply these styles to ordinary text links, publication controls, project cards, CV entries, or news rows.

### 6. Mobile behavior

Inside the existing mobile breakpoints:

- Increase navbar background opacity so expanded navigation remains readable.
- Reduce blur to approximately 12px if necessary.
- Preserve the hamburger button hit area.
- Verify that the expanded menu does not become transparent enough to expose distracting content.
- Do not change the single-column content layout.

### 7. Compatibility fallback

Add an `@supports not` fallback for browsers without backdrop-filter support.

```scss
@supports not ((backdrop-filter: blur(1px)) or (-webkit-backdrop-filter: blur(1px))) {
  #navbar,
  #light-toggle,
  .button-secondary {
    background: var(--glass-bg-strong);
  }
}
```

The fallback must remain readable without relying on blur.

### 8. Motion and accessibility

- Preserve the existing `:focus-visible` outline.
- Do not remove outlines or replace them with shadow-only focus states.
- Under `prefers-reduced-motion: reduce`, disable new transform transitions.
- Avoid continuously running animations.
- Check text and icon contrast in both themes.

## Implementation sequence

1. Inspect the current navbar markup and the imported theme rules that affect `#navbar`, active nav items, `#light-toggle`, and the mobile menu.
2. Add light and dark glass tokens beside the existing site-specific variables.
3. Replace the current custom `#navbar` border rule with the glass surface rules.
4. Add the active-nav state.
5. Add theme-toggle surface and interaction states while preserving its 8px desktop offset.
6. Add primary and secondary button surfaces and interaction states.
7. Add mobile overrides.
8. Add the backdrop-filter fallback.
9. Extend the existing reduced-motion block for any new transitions.
10. Format the Sass and run validation.

## Validation

Run:

```bash
git diff --check
bundle exec jekyll build
```

Inspect the rendered site at these viewport sizes:

- 1440 × 900
- 1024 × 768
- 390 × 844
- 360 × 800

At each viewport, inspect both light and dark modes on:

- Home
- Research
- Publications
- CV

Also test:

- Scrolling content behind the fixed navbar.
- Switching light, dark, and system theme states.
- Hover, keyboard focus, and active states.
- Opening and closing the mobile navigation.
- A simulated browser state with backdrop-filter disabled.
- Reduced-motion mode.

## Definition of done

- The navbar visibly reads as a translucent glass control layer without obscuring labels.
- Light and dark modes use appropriate tint and contrast.
- The theme icon remains vertically aligned with About, Research, Publications, and CV.
- Theme switching does not move the button or resize the navbar.
- Primary and secondary buttons remain clearly distinguishable.
- Mobile navigation remains legible and fully operable.
- Browsers without backdrop-filter receive an opaque, readable fallback.
- No content cards or document sections receive the glass treatment.
- No new JavaScript, dependency, layout override, or include override is introduced.
- `git diff --check` and `bundle exec jekyll build` pass.

## Handoff

Report:

- The selectors and tokens added or changed.
- Any values adjusted from the starting recommendations and why.
- Build result.
- Viewports and theme states visually checked.
- Any remaining browser-specific limitation.
