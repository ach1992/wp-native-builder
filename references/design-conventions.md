# Design and Custom-Section Conventions

Load this reference for UI design/review, custom Gutenberg sections, responsive behavior, RTL/LTR, accessibility, or performance-sensitive presentation.

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

## Gutenberg-first output

Use native blocks when they remain easy to edit and can achieve the requested result cleanly. For manual instructions, state the block hierarchy and only the settings necessary to reproduce the result.

## Custom HTML sections

When Custom HTML is the better path:

- normally use one logical page section per Gutenberg Custom HTML block;
- give each section a unique ID and stable site/project prefix;
- scope all CSS to that section/prefix;
- use semantic HTML and a logical heading hierarchy;
- inherit theme typography by default;
- avoid global element selectors and unnecessary `!important`;
- use native HTML behavior before JavaScript;
- include JavaScript only for behavior that cannot be achieved cleanly otherwise; do not assume inline `<script>` in a Custom HTML block is supported or appropriate;
- use Font Awesome 5 Free icons only when the current site/profile establishes that the icon set is already available; otherwise prefer existing site icons or dependency-free/native alternatives;
- include intentional mobile/tablet behavior rather than only shrinking desktop values;
- for RTL sites, verify alignment, direction-sensitive spacing, icon/arrow meaning, and interaction order;
- provide visible keyboard focus and avoid hover-only access to essential behavior;
- respect reduced-motion preferences when transitions/animation are used.

Self-contained code is appropriate for a one-off section. Do not duplicate common code across many blocks merely to keep each block self-contained.
