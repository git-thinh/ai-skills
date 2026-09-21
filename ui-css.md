---
name: ui-css
description: Create production-ready responsive web interfaces from user requirements using plain HTML and Tailwind CSS v4. Use for UI components, layouts, dashboards, forms, navigation, modals, tables, landing pages, settings pages, chat interfaces, and Kanban boards when the requested output must be a complete standalone HTML document using Tailwind CSS v4 and Bootstrap Icons, with no JavaScript or frontend framework.
---

# ui-css - Tailwind UI Builder

Create complete, production-ready UI code from the user's requirements using HTML and Tailwind CSS v4.

## Core requirements

1. Understand the requested component, layout, dashboard, form, or interaction accurately.
2. Design a modern, clean, minimal, usable interface with strong visual hierarchy.
3. Return a complete standalone HTML document.
4. Use Tailwind CSS v4 for styling.
5. Do not write JavaScript.
6. Use Bootstrap Icons for icons. Do not use SVG icons.
7. Do not use React, Vue, or other frontend frameworks.
8. Do not use UI libraries such as Bootstrap or MUI. Bootstrap Icons are allowed only as the icon set.
9. Make the interface responsive using a mobile-first approach.
10. Support both light and dark themes where appropriate.
11. Ensure accessibility and sufficient color contrast.
12. Keep code clean, readable, optimized, and free of dead or redundant markup/classes.

## Required dependencies

Include these dependencies in the generated HTML:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.13.1/font/bootstrap-icons.min.css" />
<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
```

The Tailwind browser script is permitted only to load Tailwind CSS v4. Do not add application JavaScript.

## Design rules

- Use clear typography hierarchy.
- Use consistent spacing, padding, margins, gaps, radii, and colors.
- Use Flexbox and Grid appropriately.
- Prefer semantic HTML elements.
- Use Tailwind v4 features such as container queries, arbitrary values, logical properties, and current color utilities when they materially improve the implementation.
- Avoid unnecessary custom CSS. If custom CSS is necessary, keep it minimal and easy to understand.

## Responsive behavior

- Design mobile-first.
- Use `sm`, `md`, `lg`, `xl`, and `2xl` breakpoints as appropriate.
- Ensure layouts remain usable across phone, tablet, laptop, and large desktop widths.

## Interaction without JavaScript

When the requested UI includes modal, dropdown, tabs, accordion, sidebar toggle, or basic validation, implement only behavior that can be represented safely with HTML/CSS primitives.

Use native elements such as `details`/`summary`, form validation attributes, checkboxes/radios, anchors, and CSS states when suitable. Do not introduce JavaScript merely to reproduce dynamic behavior.

## Accessibility

- Associate every input with a label.
- Add `aria-*` attributes when semantically necessary.
- Preserve keyboard navigation.
- Use semantic buttons, links, headings, navigation, tables, and forms.
- Maintain readable color contrast in light and dark themes.

## Handling unclear requests

Make reasonable UI and content assumptions when details are missing. Produce a usable interface without asking follow-up questions unless a missing detail makes implementation impossible or would fundamentally change the requested artifact.

## Output contract

Return only the HTML code and no explanation, commentary, Markdown prose, or pseudo-code.

The output must be a complete document beginning with `<!DOCTYPE html>` and containing the required HTML structure.

Example shape:

```html
<!DOCTYPE html>
<html lang="en">
  ...
</html>
```

The generated code must be immediately usable.
