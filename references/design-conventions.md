# Design and Visual Review Conventions

Load this reference only for material UI creation/redesign/review, screenshot/reference-led work, custom sections, or presentation where responsive/RTL/accessibility/performance details materially affect quality.

## Establish a design direction before components

For substantial design work, infer three anchors from available evidence before composing the page:

1. **Hierarchy:** what must be noticed first, second, and acted on?
2. **Visual character:** e.g. restrained/editorial, technical/precise, warm/human, premium/minimal, dense/utility-led — derived from the subject, brand, existing site, or reference rather than chosen generically.
3. **Layout signature:** the recurring geometry/spacing/component behavior that makes the result coherent rather than a collection of unrelated cards.

Use existing approved site language as the default for modifications. An explicit redesign/rebrand can replace it. Reference screenshots/images are evidence for hierarchy, composition, density, whitespace, shape language, typography character, color behavior, imagery, and interaction; reproduce literally only when the user requests that fidelity.

Avoid unsupported generic-AI habits such as gratuitous gradients, excessive rounded cards/pills, decorative floating blobs, identical three-card rows everywhere, or a stock “hero + cards + CTA” structure when the content/site evidence calls for another composition.

## Make the system intentional

Apply only the dimensions that affect the current result:

- **Hierarchy/content:** one dominant message/action per region; section order should support the page goal, not a template sequence.
- **Layout:** consistent container logic, alignment, spacing rhythm, and deliberate density changes; avoid arbitrary per-section spacing values.
- **Typography:** inherit site/theme fonts by default; use a small coherent type scale/weight system and do not assume unavailable weights.
- **Color:** reuse established tokens where present; create restrained roles (background/surface/text/muted/accent/state) rather than unrelated hex values; maintain sufficient contrast.
- **Responsive behavior:** design reflow, order, grouping, touch targets, and spacing for desktop/tablet/mobile instead of only shrinking font sizes at one breakpoint.
- **RTL/LTR:** verify logical alignment, directional spacing, icon/arrow meaning, control order, mixed-direction content, and mirrored assumptions rather than adding only `direction: rtl`.
- **Accessibility:** semantic structure, valid heading order, keyboard/focus visibility, meaningful alternatives/labels, appropriate ARIA only when native semantics are insufficient, no hover-only essential interaction.
- **Motion:** keep purposeful and restrained; support `prefers-reduced-motion` when motion exists.
- **Performance:** avoid duplicate fonts/icon libraries/frameworks; protect hero/LCP imagery; lazy-load only non-critical media; do not add JS for CSS/native behavior.

## Existing site versus redesign

For a targeted modification, preserve established tokens, component geometry, typography, spacing conventions, and builder/theme ownership unless the requested change specifically targets them. Do not “improve” an unrelated design system during a small edit.

For an explicit redesign, preserve only constraints that remain requirements (brand/content/data/technical compatibility); do not let old aesthetics silently constrain the new direction.

## Custom sections

When Custom HTML/CSS is the justified mechanism:

- keep logical sections independently editable when practical;
- use a unique ID/stable project prefix and scope selectors beneath it;
- use semantic HTML and logical headings;
- inherit current typography and reuse existing tokens/assets where possible;
- avoid unnecessary `!important`, global selectors, duplicate libraries, and JS;
- add interaction states, focus behavior, mobile/tablet treatment, and RTL/LTR handling when applicable;
- centralize shared code only when it is genuinely reused.

## Visual self-review

When a preview/render is available for material UI, inspect the actual result rather than trusting markup/configuration. Check the highest-signal failures first: hierarchy, obvious spacing/alignment breaks, overflow/reflow, typography/contrast, target fidelity, interaction/focus, RTL issues, broken/missing assets, and any performance-heavy choice introduced by the change.

Correct clear defects before showing the preview when safe. Surface only material residual choices/findings to the user; do not dump this section as a checklist.
