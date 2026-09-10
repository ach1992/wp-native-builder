# Implementation Decisions

Use this reference when the site's architecture is mixed/non-trivial or the change is reusable, site-wide, commerce-related, data-model-related, or capability-dependent.

## Discover only what matters

Before selecting a mechanism, establish only architecture facts that can change the decision:

| Surface | Relevant facts |
|---|---|
| Theme | active theme, child theme, block-theme/Site Editor vs classic behavior, supported theme facilities |
| Editing model | Gutenberg, Site Editor, current page builder, templates/patterns, existing ownership of the target page/region |
| Plugins/workloads | relevant installed/active plugins such as WooCommerce, forms, ACF, multilingual, SEO, caching/performance, or other task-specific capability |
| Content/data model | post type, taxonomy, fields/ACF, product/catalog objects, reusable/global content model |
| Connected capability | native, plugin, theme, or Bridge abilities actually exposed for the task |

Do not inventory every plugin/theme by default. In connected mode inspect safely; in manual mode ask only for unknown facts that can materially change implementation.

## Selection rules

| Need | Preferred path |
|---|---|
| Standard content on a Gutenberg-owned page | WordPress Core blocks first |
| Block-theme global layout/template work | Site Editor, templates/template parts, Global Styles, Patterns, or supported block mechanisms |
| Repeated structure with independently editable instances | Unsynced Pattern when native reuse fits |
| Repeated content that must stay identical everywhere | Synced Pattern when native synchronized reuse fits |
| Existing page-builder-owned page/section | Current builder's supported mechanism; preserve ownership unless migration is requested |
| Theme-owned presentation/layout | Current theme's supported facility when it owns the concern cleanly |
| Forms | Suitable installed form plugin; Gravity Forms is the preferred default only when applicable |
| WooCommerce presentation | WooCommerce-supported blocks/templates/settings and current theme/builder integration when WooCommerce is present |
| Existing CPT/taxonomy/ACF model | Reuse the established content/data model and supported APIs when it remains fit |
| Existing plugin capability | Reuse the installed plugin when it cleanly satisfies the requirement |
| One-off custom visual section | Scoped HTML/CSS/JS only when the current editor/native mechanisms cannot achieve it cleanly |
| Shared CSS/JS/PHP behavior | Centralize in the smallest maintainable existing mechanism |
| Capability requiring lifecycle/settings/data/API surface | Small purpose-built plugin/custom extension only when simpler supported options are insufficient |

The owner's Astra + Astra Pro + Gutenberg + Gravity Forms + Code Snippets Pro stack is a preferred default, not an architecture mandate. Never introduce or replace technology solely to match it.

## Mechanism vs connected transport

Choose the WordPress/site mechanism independently from the tool used to operate it.

- First decide what should own the behavior on this site: Core/Site Editor, current theme/builder, WooCommerce, an installed plugin, existing data model, or justified custom code.
- Then, in connected mode, choose an actually exposed ability that safely operates that mechanism.
- Do not assume the Bridge's custom namespace is exhaustive; use suitable native/plugin abilities exposed by the runtime.
- Prefer supported public/native APIs and extension points over file edits, private internals, or brittle DOM/admin automation.
- When no suitable connected write exists, keep manual mode useful instead of inventing an ability.

## Decision checks

Before moving to a more custom or replacement mechanism, confirm the existing simpler path fails on a material requirement such as fidelity, editability, reuse, behavior, accessibility, performance, maintainability, compatibility, lifecycle, or data ownership.

Do not replace a working stack merely to match Skill defaults. Do not install a second plugin for capability already provided cleanly by WordPress or a suitable current theme/plugin.

## WooCommerce scope

When WooCommerce is present, treat product/catalog structure, category/product presentation, shop pages, WooCommerce blocks/templates, store UX, responsive design, product content, merchandising/presentation, and relevant non-sensitive configuration as supported site-building work.

Do not silently broaden design/content requests into refunds, payment operations, destructive order changes, or other customer/order/financial mutations. Those actions require the appropriate permission and approval boundary.

## Custom code placement

- Keep one-off section CSS scoped to a unique section ID or stable project prefix.
- Keep JavaScript out unless native/current-stack behavior is insufficient. Do not assume inline `<script>` in content is supported or maintainable; use only verified placement.
- Move genuinely shared/reusable styles or scripts to an existing centralized mechanism when one is fit.
- Put reusable/routine PHP in an existing safe code-management mechanism when appropriate and available, or use the smallest purpose-built plugin when lifecycle, permissions, data, integration, or maintainability justify it.
- For custom PHP/plugin work, validate expected input, sanitize where appropriate, escape output at render time, enforce capabilities for privileged operations, use nonces for CSRF protection without treating them as authorization, require suitable REST `permission_callback` checks, and prefer WordPress APIs/prepared queries over raw SQL.
- Do not edit WordPress core or third-party theme/plugin files directly for routine customization.

## Existing-site configuration

Defaults apply mainly as a fallback for new/unspecified work. On an existing site:

- inspect or use supplied architecture first;
- preserve the target's current editor/builder ownership unless migration is explicitly requested;
- preserve permalink structure, typography, global colors, plugins/themes, data models, and other global configuration unless change is explicitly requested;
- review impact before global or cross-site changes;
- prefer narrow changes with straightforward rollback.
