# Design and Custom-Section Conventions

Load this reference for UI design/review, current-editor custom sections, responsive behavior, RTL/LTR, accessibility, or performance-sensitive presentation.

## Design quality

Apply only what matters to the current task:

| Dimension | Target |
|---|---|
| Hierarchy | obvious primary/secondary emphasis and controlled density |
| Layout | coherent grid, alignment, spacing rhythm, and container behavior |
| Typography | theme-aware readable hierarchy without unsupported font-weight assumptions |
| Color | restrained palette and sufficient contrast |
| Responsive behavior | intentional desktop/tablet/mobile behavior, not a single-breakpoint patch |
| Accessibility | semantic structure, valid heading order, keyboard/focus support, meaningful alternatives, appropriate ARIA |
| Motion | avoid unnecessary motion and respect `prefers-reduced-motion` when motion exists |
| Performance | avoid unnecessary assets/dependencies; protect hero/LCP imagery; lazy-load only appropriate media |
| Maintainability | independent logical sections and scoped selectors; centralize only genuinely shared rules |
| Creativity | fit the subject/audience instead of repeating generic AI landing-page patterns |

## Interpret design intent

Before coding a substantial design, translate the available goal, audience, content, brand/site conventions, and visual references into one coherent design direction. Preserve the current site's visual language when it remains suitable; treat a supplied reference as evidence for hierarchy, composition, density, typography character, color behavior, shape language, imagery, and interaction rather than copying it blindly. If materially different interpretations remain possible and the choice would significantly change the result, use the focused question strategy in [site-profile.md](site-profile.md) instead of guessing.

## Current-editor-aware output

Use the site's current editing architecture when it remains suitable:

- on Gutenberg-owned pages, prefer native blocks and Patterns when they can achieve the result cleanly;
- on block themes, use Site Editor/template/template-part/Global Styles mechanisms for concerns they own;
- on an existing page-builder-owned surface, preserve that builder and use its supported mechanisms rather than rebuilding in Gutenberg/Astra merely to match defaults;
- for manual instructions, provide only the hierarchy/settings necessary for the actual editor in use.

## Custom HTML sections

When scoped Custom HTML/CSS is the better path for the current site/editor:

- normally keep one logical page section independently editable;
- give each custom section a unique ID and stable site/project prefix;
- scope all CSS to that section/prefix;
- use semantic HTML and a logical heading hierarchy;
- inherit current site/theme typography by default;
- avoid global element selectors and unnecessary `!important`;
- use native HTML/current-stack behavior before JavaScript;
- include JavaScript only for behavior that cannot be achieved cleanly otherwise; do not assume inline `<script>` in content is supported or appropriate;
- use Font Awesome 5 Free only when the current site/profile establishes that it is already available; otherwise prefer existing site icons or dependency-free/native alternatives;
- include intentional mobile/tablet behavior rather than only shrinking desktop values;
- for RTL sites, verify alignment, direction-sensitive spacing, icon/arrow meaning, and interaction order;
- provide visible keyboard focus and avoid hover-only access to essential behavior;
- respect reduced-motion preferences when transitions/animation are used.

Self-contained code is appropriate for a one-off section. Do not duplicate common code across many blocks/pages merely to keep each section self-contained.
