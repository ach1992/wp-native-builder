# Design and Visual Review Conventions

Load this reference only for material UI creation/redesign/review, screenshot/reference-led work, custom sections, or presentation where responsive/RTL/accessibility/performance details materially affect quality.

## Establish a design direction before components

For substantial design work, infer a compact internal direction from available evidence before composing the page:

1. **Outcome and hierarchy:** what must be understood, noticed, trusted, and acted on first?
2. **Visual character:** e.g. restrained/editorial, technical/precise, warm/human, premium/minimal, dense/utility-led — derived from the subject, brand, existing site, or reference rather than chosen generically.
3. **Layout signature:** the recurring geometry/spacing/component behavior that makes the result coherent rather than a collection of unrelated cards.
4. **Asset direction:** how photography, illustration, icons, texture, or deliberate absence of imagery should support the concept.
5. **Signature idea:** one memorable but useful visual/compositional move that gives the page character without turning every section into a gimmick.

Use existing approved site language as the default for modifications. An explicit redesign/rebrand can replace it. Reference screenshots/images are evidence for hierarchy, composition, density, whitespace, shape language, typography character, color behavior, imagery, and interaction; reproduce literally only when the user requests that fidelity.

Avoid unsupported generic-AI habits such as gratuitous gradients, excessive rounded cards/pills, decorative floating blobs, identical three-card rows everywhere, or a stock “hero + cards + CTA” structure when the content/site evidence calls for another composition.

## Compose for the user journey, not for a component inventory

Let content importance determine composition. Build a clear path through orientation -> understanding/trust -> action when that matches the page goal; do not force this sequence where another information structure is better. Use contrast, scale, whitespace, grouping, repetition, and deliberate breaks in rhythm to guide attention.

For a new visual system, establish only the reusable decisions that will actually recur: container behavior, spacing rhythm, type scale, color roles, radius/border/depth language, imagery treatment, and interaction states. Use theme/global tokens or CSS custom properties when the selected mechanism supports them instead of scattering near-duplicate values.

Prefer one strong primary direction. Generate or present alternatives only when a genuinely material visual choice remains unresolved or comparison would help the user decide. Do not make the user choose between cosmetic variants the model can resolve professionally.

## Use references, content, and assets deliberately

If the user supplies references, identify why they work rather than copying surface decoration. If visual direction is weak and browsing/reference tools are available, inspect only a small set of relevant, high-quality examples when that can materially improve the result; extract layout, hierarchy, interaction, and art-direction principles without copying branding, protected artwork, or another site's identity.

Treat imagery and content as design inputs, not placeholders. Reuse suitable site assets first. When missing imagery materially limits the result and an allowed image-search/generation path is available, propose or create a coherent asset direction with appropriate crop/aspect/focal behavior and mobile treatment. Respect licensing/source constraints for externally sourced assets.

Improve headings, labels, CTA wording, section order, and supporting microcopy when doing so clearly improves comprehension or conversion and remains within the user's facts. Never invent testimonials, statistics, guarantees, product claims, certifications, or other factual marketing evidence.

## Make the system intentional

Apply only the dimensions that affect the current result:

- **Hierarchy/content:** create a dominant reading/action path where the goal calls for one; section order should support the user's task, not a template sequence.
- **Layout:** use coherent container logic, alignment, spacing rhythm, density, and intentional asymmetry/symmetry; avoid arbitrary per-section values or repetitive card grids.
- **Typography:** inherit site/theme fonts by default; use a small coherent type scale/weight/line-height system, respect the active script/language, and do not assume unavailable weights.
- **Color/depth:** reuse established tokens where present; create restrained roles (background/surface/text/muted/accent/state) plus a consistent border/shadow/depth language rather than unrelated hex values/effects; maintain sufficient contrast.
- **Responsive behavior:** recompose order, grouping, emphasis, crop, touch targets, and spacing for desktop/tablet/mobile instead of merely stacking everything or shrinking font sizes at one breakpoint.
- **RTL/LTR:** verify logical alignment, directional spacing, icon/arrow meaning, control order, mixed-direction content, and mirrored assumptions rather than adding only `direction: rtl`.
- **Interaction/UX:** make controls, navigation, forms, and primary actions obvious and predictable; include useful hover/focus/active/loading/success/error/empty states only when the interface actually needs them.
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

When a preview/render is available for material UI, inspect the actual result rather than trusting markup/configuration. Review at two levels: first-impression quality (clarity, balance, visual character, credibility, focal path, obvious generic/template feel) and task-level quality (spacing/alignment, overflow/reflow, typography/contrast, content/CTA clarity, target fidelity, interaction/focus, RTL issues, broken/missing assets, and any performance-heavy choice introduced by the change).

Correct clear defects and weak generic-looking choices before showing the preview when safe. A polished result should feel intentional in both still-image inspection and real use: readable, usable, responsive, coherent, and visually distinctive enough for its context without sacrificing accessibility or performance. Surface only material residual choices/findings to the user; do not dump this section as a checklist.
