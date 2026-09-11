# Implementation and Ownership Decisions

Load this reference when owner/mechanism selection is non-obvious; work is global/reusable/template/theme/builder/plugin/data-model dependent; or a new capability/custom-code decision could materially affect maintainability.

**Contents:** [Discovery](#1-discover-only-decision-relevant-architecture) · [Surface ownership](#2-resolve-surface-ownership-before-markup) · [Native before HTML](#3-nativeblock-capability-check-before-custom-html) · [Capability gaps](#4-capability-gap-reuse-add-or-build) · [Mechanism vs transport](#5-mechanism-versus-transport) · [Existing-site impact](#6-existing-site-impact) · [Naming](#7-maintainability-and-naming) · [Forms/WooCommerce](#8-forms-and-woocommerce-boundaries) · [Custom code](#9-custom-code-placement)

## 1. Discover only decision-relevant architecture

Establish enough evidence to answer:

- What theme/editing model is active: classic/hybrid/block theme?
- Is a page builder or theme builder the owner of the target surface?
- Which installed theme/plugin/Core capability already owns or can cleanly satisfy the requirement?
- Is the target page-local, reusable, template/global, data-driven, form/commerce-owned, or behavior/lifecycle-owned?
- Which connected abilities actually operate the chosen owner safely?

Do not inventory unrelated plugins for a narrow task.

For multi-step projects, record stable answers that will recur in the derived Site Architecture Profile rather than rediscovering them from chat each time.

## 2. Resolve surface ownership before markup

| Target surface / need | Preferred owner/mechanism | Avoid by default |
|---|---|---|
| Block-theme header/footer/site shell | Site Editor + template/template part + Global Styles/Patterns as appropriate | Page-local Custom HTML duplicating global shell |
| Classic/theme-managed header/footer | Current theme's supported header/footer/layout facility; child-theme/public hook only when needed | Pasting a separate header/footer into every page |
| Existing builder-owned global shell | Builder's Theme Builder/global template mechanism | Reimplementing the shell in Gutenberg/HTML without migration intent |
| Gutenberg page content | Core blocks and supported block settings first | Handcrafted serialized Core-block HTML merely for convenience |
| Reusable Gutenberg section | Pattern or Synced Pattern according to reuse/update semantics | Duplicated per-page HTML/CSS copies |
| Reusable global template structure | Template/template part/theme or builder-global mechanism | Page-local duplication |
| Navigation | Current theme/Site Editor/builder navigation mechanism | Static duplicated link markup in page sections |
| Dynamic post/content listing | Query Loop/Core/theme/plugin/data mechanism appropriate to the model | Hard-coded repeated cards when content is dynamic |
| Form | Suitable installed form system | Rebuilding validation, anti-spam, submission, storage, notifications manually |
| WooCommerce presentation | WooCommerce-supported blocks/templates/settings + current theme/builder integration | Rebuilding commerce logic in custom frontend markup |
| Existing CPT/taxonomy/ACF model | Existing model/APIs/blocks/templates | Parallel duplicate data model |
| Media/content | Media Library + normal content APIs | Unmanaged duplicate assets or direct DB edits |
| Presentation-only gap | Scoped CSS; scoped HTML/CSS and only needed JS when native mechanism cannot represent it cleanly | New plugin/PHP for a styling-only need |
| Shared site-specific behavior/lifecycle/API/settings | Existing centralized safe mechanism or smallest purpose-built extension | Scattered page snippets/inline scripts |
| Mature missing capability | Focused maintained plugin/theme capability when lifecycle/risk burden is lower | Rebuilding a mature subsystem without material reason |

Header/footer/global shell is a strong ownership signal. Never default to page HTML for a concern that the theme, Site Editor, template part, or builder-global system already owns.

## 3. Native/block capability check before Custom HTML

Before choosing Custom HTML for a Gutenberg surface, ask in order:

1. Can a Core block or existing installed block express the structure and behavior safely?
2. Can block settings/styles, Group/Row/Stack/Cover/Columns/Grid, Buttons, Navigation, Query Loop, Details, Media & Text, or other appropriate native blocks satisfy it?
3. Is the section reusable enough to be a Pattern/Synced Pattern?
4. Is the concern actually template/global and therefore owned elsewhere?
5. Does a focused existing plugin/theme block already own it?
6. Only then: is a scoped Custom HTML/CSS/JS section genuinely the lower-burden, more maintainable solution?

Do not choose Custom HTML simply because translating a design to HTML is easier for the model.

If raw block markup is involved, the Gutenberg safety rules in `gutenberg-safety.md` also apply.

## 4. Capability gap: reuse, add, or build

Compare the smallest credible paths:

1. configure/reuse WordPress Core or an installed suitable theme/builder/plugin feature;
2. add one focused maintained capability when it provides lower implementation/lifecycle burden;
3. use scoped custom HTML/CSS/JS for a presentation-only gap;
4. use a small purpose-built extension when ownership, lifecycle, permissions, data/API behavior, or unusual requirements make custom implementation better long term.

For a new dependency, evaluate only decision-relevant factors: exact fit, overlap, current WordPress/PHP/theme/builder compatibility, maintenance/support, material security history, performance footprint, accessibility/UX, editability, data ownership/lock-in, licensing/cost, uninstall/reversibility. Verify current official/product/security information when the recommendation materially depends on it.

Normally recommend one best-fit option and one materially different alternative only when the trade-off is real. Avoid generic “top plugins” lists, overlapping systems, or paid/external dependencies whose benefit does not clearly repay cost and maintenance.

A recommendation is not authorization to install/activate a plugin/theme, change broad global settings, buy a license, or make a vendor commitment. Prepare the best path and continue independent safe work; apply the core approval boundary to the actual install/activation/global/external action. A current exact instruction can already satisfy that boundary when target/scope/effect remain unchanged.

## 5. Mechanism versus transport

Do not choose architecture from whichever tool happens to be connected.

```text
MECHANISM = site owner of behavior
TRANSPORT = currently exposed ability/tool that safely operates that owner
```

Native/plugin/theme abilities may be preferable to Bridge-owned operations. If the correct mechanism has no safe connected write path, preserve the mechanism decision and continue with safe preparation/manual implementation rather than switching architecture merely to fit the connector.

## 6. Existing-site impact

- Read the current target before material modification when possible.
- Preserve current theme/builder/editor ownership, design tokens, data models, plugin choices, and permalink structure unless accepted scope changes them.
- Inspect reuse/impact before editing global/template/shared surfaces.
- Before a global/template/shared mutation, capture the current target identity and the practical revision/rollback route when the runtime exposes one; use that evidence to preserve or restore shared state if the change regresses.
- Explicit redesign/migration can replace prior ownership, but inspect dependencies and migration effect first.

## 7. Maintainability and naming

Use names that tell a future human **what this is, where it belongs, and why it exists**.

### Human-facing artifacts

Prefer forms such as:

- Page: `About`, `Pricing`, `Support`
- Template: `Single — Knowledge Base Article`
- Template part: `Header — Main`, `Footer — Primary`
- Pattern: `Home — Hero`, `Global — Trust Bar`
- Snippet: `Site — Mobile Navigation Enhancement`
- Workspace doc: `Project Foundation`, `Site Architecture Profile`, `Design Direction`
- Task: `Home — Rebuild posts pagination without page reload`

Avoid `Section 1`, `New Pattern`, `Custom CSS 2`, `Untitled`, random IDs, or internal tool labels as the main maintainer-facing name.

### Code-facing identifiers

Choose one stable project/site prefix when custom identifiers are needed, e.g. `brand-` or a short domain-derived slug.

- CSS: `.brand-home-hero`, `#brand-site-notice`
- JS/PHP/custom block/plugin identifiers: consistent namespace/prefix
- Snippet functions/hooks: stable purpose-based names

Do not reuse WordPress/plugin namespaces. Avoid unnecessary global selectors and random hashes for identifiers humans are expected to maintain.

### Ownership note

For custom or non-obvious work, make edit ownership discoverable in the relevant durable project artifact/task: page editor, Site Editor/template part, theme facility, builder global template, Pattern, snippet, or custom extension.

## 8. Forms and WooCommerce boundaries

Reuse a suitable installed form system for submission handling, validation, anti-spam, notifications, storage, and integrations.

Normal WooCommerce builder scope includes product/catalog/category/store presentation, blocks/templates, responsive store UX, merchandising presentation, product content, and relevant non-sensitive presentation/structure settings.

Do not silently expand into refunds, payment actions, destructive order/customer mutation, or financial operations.

## 9. Custom code placement

Place code at the narrowest owner that matches its scope and lifecycle: presentation belongs with the relevant block/theme/builder styling surface when possible; genuinely shared frontend behavior belongs in one central reusable location; privileged/server-side behavior belongs in an appropriate PHP/snippet/extension owner; data/API/permission lifecycle belongs in a purpose-built extension when no suitable existing owner exists.

- Scope one-off CSS beneath a stable project-prefixed owner/section selector.
- Add JS only when current/native behavior is insufficient.
- Do not assume inline `<script>` inside page content is supported or maintainable.
- Centralize genuinely shared CSS/JS/PHP only when reuse/lifecycle justifies it.
- Use a safe existing code-management mechanism when fit, or the smallest purpose-built extension when lifecycle/permissions/data/API needs require it.
- Never edit WordPress Core or third-party plugin/theme files directly.
