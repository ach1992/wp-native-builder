# Implementation Decisions

Load this reference only when ownership/mechanism selection is not obvious or the work is reusable/site-wide, template/builder/plugin/data-model dependent, commerce/forms related, custom-PHP/plugin related, or connected-capability dependent.

## Discover the decision surface

Establish only facts that can change the chosen owner/mechanism:

| Concern | Decision-relevant evidence |
|---|---|
| Theme / editing model | classic vs block theme; Site Editor; active child theme; page-builder ownership; template/global surface ownership |
| Existing capability | relevant active theme/plugin feature that already satisfies the need; avoid overlapping dependencies |
| Forms / commerce | existing form system; WooCommerce-owned templates/blocks/settings; current theme/builder integration |
| Content/data model | CPT, taxonomy, ACF/fields, products/catalog, reusable/global content relationships |
| Connected execution | native/plugin/theme/Bridge abilities actually exposed for the selected mechanism |

Do not inventory unrelated plugins or rebuild a site profile for a narrow change.

## Ownership choices

| Situation | Prefer |
|---|---|
| Gutenberg-owned page content | Core blocks; Pattern/Synced Pattern according to reuse semantics |
| Block-theme global/template concern | Site Editor, templates/template parts, Global Styles, Patterns, supported block mechanisms |
| Existing page-builder-owned surface | Current builder's supported mechanism unless migration is explicit |
| Theme-owned presentation/layout | Current theme facility when it cleanly owns the concern |
| Existing suitable plugin capability | Reuse that plugin rather than add a second implementation |
| Forms | Suitable installed form plugin; Gravity Forms only as applicable/default |
| WooCommerce presentation | WooCommerce-supported blocks/templates/settings plus current theme/builder integration |
| Existing CPT/taxonomy/ACF model | Preserve and use the established model/APIs when fit |
| Site media/content changes | WordPress Media Library plus normal content/revision APIs |
| One-off presentation gap | Scoped HTML/CSS and only needed JS |
| Shared reusable behavior | Smallest maintainable existing centralized mechanism |
| Mature nontrivial capability missing from the site | Focused maintained plugin/theme capability when it provides lower lifecycle/risk burden than rebuilding it |
| New site-specific lifecycle/settings/data/API behavior | Small purpose-built plugin/extension when a third-party dependency would be heavier, less fit, or worse-owned |

Before moving to a more custom or replacement path, identify the material requirement the simpler existing path cannot meet: fidelity, editability, reuse, behavior, accessibility, performance, maintainability, compatibility, lifecycle, permissions, or data ownership. “I prefer another stack” is not enough on an existing site unless the user requested that change.

## Capability gap: reuse, add a plugin, or build

Do not wait for the user to name a plugin when the current stack is missing a capability that materially affects the requested outcome. Identify the capability first, then compare the smallest credible paths:

1. configure/reuse WordPress core or an already-installed suitable theme/builder/plugin feature;
2. add one focused maintained plugin/theme capability when it provides mature behavior with lower implementation and maintenance burden;
3. use scoped custom HTML/CSS/JS for a presentation-only gap;
4. use a small site-specific extension/plugin when ownership, lifecycle, permissions, data/API behavior, or unusual requirements make custom implementation the better long-term fit.

Choose by total lifecycle cost, not by “fewer plugins” or “less code” in isolation. For a new dependency, evaluate only decision-relevant factors: exact feature fit, overlap with current plugins, current WordPress/PHP/theme/builder compatibility, maintenance activity/support, material security history, performance footprint, accessibility/UX quality, editability, data ownership/lock-in, licensing/cost, and uninstall/reversibility. Verify current official/product/security information when the recommendation materially depends on it.

Keep the recommendation decision-ready: normally name one best-fit option and why; include one materially different alternative only when there is a real trade-off. Avoid generic “top plugins” lists, installing overlapping systems, or introducing a paid/external dependency whose benefit does not clearly repay its cost and maintenance.

A recommendation is not automatic authorization to install/activate a new plugin/theme, change broad global settings, buy a license, or commit to a vendor. Prepare the best path and continue any independent safe work; apply the core approval boundary to the actual install/activation/global/external action. A current exact user instruction for that action can already satisfy the approval requirement when nothing material has drifted.

## Mechanism versus transport

Keep these decisions separate:

1. **Mechanism:** what should own the behavior on this WordPress site?
2. **Transport:** which currently exposed capability can inspect/change that mechanism safely?

Do not choose architecture based on whichever tool happens to be connected. Do not assume a custom Bridge namespace is exhaustive. Prefer a supported native/plugin/theme ability when it better matches the chosen mechanism. If no safe connected write exists, preserve the mechanism choice and provide a manual implementation path.

## Existing-site changes

- Read/inspect the current target before a material modification when possible.
- Preserve editor/builder ownership, design tokens, global configuration, data models, plugin/theme choices, and permalink structure unless the requested outcome requires changing them.
- Prefer the smallest target-local change. Treat global/template/shared edits as broader-impact changes and inspect affected reuse before mutation.
- When an explicit redesign/migration is requested, the new instruction can replace prior conventions, but inspect dependencies/impact before changing global ownership.

## Forms

Use an existing suitable form system for submission handling, validation, anti-spam, notifications, storage, and integration. Custom layout/styling may frame a form; do not recreate a form engine without a material requirement.

## WooCommerce and sensitive boundaries

Normal builder scope includes product/catalog/category/store presentation, shop/product/archive templates, WooCommerce blocks, responsive store UX, merchandising/presentation, product content, and relevant non-sensitive presentation/structure settings.

Do not silently expand that scope into refunds, payment actions, destructive order mutation, or consequential customer/order/financial operations. Treat those as separate sensitive operations requiring the applicable capability and approval boundary.

## Custom code placement

- Scope one-off CSS to a unique section ID or stable project prefix; avoid global selectors and unnecessary `!important`.
- Add JavaScript only when current/native behavior is insufficient; do not assume inline `<script>` in content is supported or maintainable.
- Centralize genuinely shared CSS/JS/PHP only when reuse justifies it.
- Use an existing safe code-management mechanism when appropriate, or the smallest purpose-built plugin when lifecycle, permissions, data, API, or maintainability requires it.
- Never edit WordPress core or third-party theme/plugin files directly.
- For custom PHP/plugin code, enforce WordPress validation/sanitization/escaping/capability/nonce/REST permission/prepared-query rules from the core Skill.
