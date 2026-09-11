# Design and Visual Review Conventions

Load this reference for material UI creation/redesign/review, screenshot/reference-led work, custom sections, or presentation where responsive/RTL/accessibility/performance details materially affect quality.

## 1. Establish direction before components

For substantial visual work, derive a compact internal direction from available evidence:

1. outcome and hierarchy;
2. visual character appropriate to brand/audience/content;
3. layout signature and spacing/density behavior;
4. asset/imagery direction;
5. one useful distinctive idea that gives the design character without gimmicks.

Use existing approved site language as the default for modifications. Explicit redesign/rebrand may replace it. References are evidence for hierarchy, density, geometry, typography character, color behavior, imagery, and interaction; reproduce literally only when the user requests high fidelity.

Avoid unsupported generic-AI habits such as gratuitous gradients, excessive pills/cards, decorative blobs, identical card rows everywhere, or a stock hero/cards/CTA structure when the content calls for another composition.

## 2. Be an advisor, not a passive copier

If a user-suggested design pattern is clearly weak for the stated goal, outdated, confusing, inaccessible, excessively complex, inconsistent with the existing design system, or likely to create maintenance/responsive problems:

1. identify the concrete problem briefly;
2. recommend one better direction and why it better serves the goal;
3. implement the better direction when the user has delegated ordinary design judgment;
4. if the user explicitly insists on the original preference and it remains safe/valid, respect it without misrepresenting it as best practice.

Do not escalate cosmetic preferences into unnecessary decision gates. Do not override explicit brand/fidelity requirements merely because another style is fashionable.

## 3. Compose for the user journey

Let content importance determine composition. Build a clear path through orientation, understanding/trust, and action where appropriate; do not force a template sequence.

For a recurring visual system, establish only reusable decisions that actually recur: container behavior, spacing rhythm, type scale, color roles, radius/border/depth language, imagery treatment, interaction states. Use theme/global tokens or CSS variables supported by the selected mechanism rather than scattering near-duplicate values.

Prefer one strong primary direction. Show alternatives only when a material choice remains unresolved.

## 4. Use references/content/assets deliberately

If references exist, identify why they work rather than copying surface decoration. If direction is weak and allowed search/reference tools are available, inspect a small set of relevant high-quality examples when it materially improves the result; extract principles without copying identity/protected artwork.

Treat real content and imagery as design inputs. Improve headings, labels, CTA wording, section order, and microcopy when that clearly improves comprehension and stays within known facts. Never invent testimonials, statistics, certifications, guarantees, or product claims.

## 5. Quality dimensions

Apply only what affects the current result:

- **Hierarchy/content:** dominant reading/action path where appropriate.
- **Layout:** coherent container/alignment/spacing/density; intentional symmetry/asymmetry.
- **Typography:** inherit site/theme fonts by default; coherent scale/weight/line-height; respect active script/language.
- **Color/depth:** established tokens where available; restrained semantic roles; sufficient contrast.
- **Responsive:** recompose order/grouping/emphasis/crop/touch targets/spacing rather than merely shrinking.
- **RTL/LTR:** logical alignment/spacing, icon/arrow meaning, control order, mixed-direction content, mirrored assumptions.
- **Interaction/UX:** obvious/predictable controls and primary actions; states only when needed.
- **Accessibility:** semantic structure, heading order, keyboard/focus visibility, meaningful alternatives/labels, ARIA only when native semantics are insufficient.
- **Motion:** purposeful/restrained; support `prefers-reduced-motion` when motion exists.
- **Performance:** avoid duplicate fonts/icon libraries/frameworks; protect hero/LCP media; lazy-load only non-critical media; avoid JS for CSS/native behavior.
- **Maintainability:** owner/mechanism and edit location remain understandable.

## 6. Existing site versus redesign

For targeted modification, preserve established tokens, geometry, typography, spacing conventions, and builder/theme ownership unless the requested change targets them.

For explicit redesign, preserve only constraints that remain requirements. Do not let old aesthetics silently constrain the new direction.

## 7. Custom sections

When Custom HTML/CSS is justified:

- keep logical sections independently editable when practical;
- use a stable project-prefixed ID/class and scope selectors beneath it;
- use semantic HTML and logical headings;
- inherit current typography/tokens/assets where possible;
- avoid unnecessary `!important`, global selectors, duplicate libraries, and JS;
- implement focus/interaction/mobile/tablet/RTL behavior when applicable;
- centralize shared code only when genuinely reused.

## 8. Mandatory pre-user self-review for material UI

When preview/render is available, inspect the actual result before asking the user to review it.

### First-impression review

Check clarity, balance, credibility, visual character, focal path, and whether the result feels generic/template-like relative to the project.

### Task-level review

Check spacing/alignment, overflow/reflow, typography/contrast, content/CTA clarity, target/reference fidelity, interaction/focus, RTL issues, broken/missing assets, performance-heavy choices, editability/ownership, and any obvious architecture misuse.

When Gutenberg is involved, also follow `gutenberg-safety.md` and explicitly look for invalid/recovery warnings before user review.

Correct clear defects and weak generic choices before showing the result when safe. Surface only material residual choices/findings to the user; do not dump the entire checklist.
