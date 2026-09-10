---
name: wp-native-builder
description: Stack-adaptive expert WordPress site-building and design guidance for planning, creating, modifying, reviewing, and refining WordPress sites. Use for Gutenberg/Block Editor, Site Editor/block themes, existing page builders/themes/plugins, WooCommerce presentation, forms, ACF/custom post types, scoped HTML/CSS/JS, responsive/RTL design, accessibility/performance review, and connected WordPress work through wp-native-builder-bridge. Inspect or use supplied site architecture before choosing a mechanism, reuse suitable current-site capabilities, prefer supported WordPress/public APIs, preserve unrelated state, and advance safe reversible work before any genuinely required consequential approval boundary.
---

# WP Native Builder

Build and refine WordPress sites with a stack-adaptive, WordPress-native-first workflow. Use the site's actual architecture rather than forcing a preferred stack.

## Operating workflow

1. Apply this precedence when instructions conflict:
   1. current explicit user instruction;
   2. current project/site profile supplied by the user;
   3. verified connected-site state;
   4. the preferred defaults in this Skill.
2. Establish enough current architecture to choose correctly: active theme/child theme, editing model, relevant installed/active plugins or workloads, content/data model, supported public/native surfaces, and connected abilities when available.
3. In connected mode, inspect discoverable architecture/capabilities before asking. In manual mode, use supplied context and ask only for missing stack facts that can materially change the implementation.
4. Choose the site's implementation mechanism first; treat Bridge/tool abilities as execution transport for that mechanism, not as the architecture itself.
5. Choose the smallest maintainable implementation path using the decision model below.
6. Produce or apply the requested work with narrow scope and preserve unrelated content/configuration.
7. Check only quality concerns that materially apply to the current task.
8. Advance safe read, draft, preview, validation, preparation, and reversible work without approval friction. Pause only at a genuinely required live/consequential boundary not already covered by the user's current explicit instruction.

## Stack-adaptive decision model

Choose based on the current site's architecture and capabilities:

```text
REQUEST
  -> understand the relevant current site architecture/capabilities
  -> reuse the site's existing suitable mechanism
  -> prefer WordPress-native/public/supported surfaces
  -> prefer suitable capabilities of the current theme/builder/plugins
  -> in connected mode, use an exposed ability that safely operates the chosen mechanism
  -> use scoped custom HTML/CSS/JS for genuine gaps
  -> use the smallest justified custom extension/plugin only when simpler paths are insufficient
```

Do not install, replace, or migrate a theme/plugin/builder merely to match this Skill's defaults. A site already using a suitable supported mechanism should normally keep using it.

Read [references/implementation-decisions.md](references/implementation-decisions.md) when the site's architecture is mixed/non-trivial, the request is site-wide/reusable, or forms, WooCommerce, custom post types/ACF, plugins, custom PHP, or connected abilities materially affect the implementation.

## Preferred default stack

The owner's common environment remains a useful default when applicable, but it is not the only supported stack:

- WordPress with Gutenberg / Block Editor.
- Astra + Astra Pro.
- Gravity Forms for forms.
- Code Snippets Pro for justified centralized/reusable custom code.
- Font Awesome 5 Free when established by the current project/site profile.
- Theme/site-managed fonts; custom components inherit typography unless explicitly directed otherwise.
- Astra-native facilities/hooks for suitable header/footer/global placement when Astra owns that concern.
- Post-name permalinks for a new site only; never change an existing permalink structure without explicit instruction and impact review.

If the actual site uses another suitable theme, block theme/Site Editor, page builder, form plugin, commerce stack, data model, or plugin capability, adapt to it. Never install or rely on a preferred default solely because it appears here.

## Manual mode

Choose output that fits the site's actual editor and stack:

- For modifications, inspect supplied/current implementation first when available. If unavailable, ask only for the exact stack/page/section state needed to make the targeted change safely.
- For review requests, return prioritized, implementation-aware findings and concrete next actions instead of a generic checklist.
- For Gutenberg work, provide the exact block hierarchy plus only important settings/content. Prefer Patterns or Synced Patterns when native reuse fits. Output serialized `<!-- wp:... -->` markup only when paste/import-ready block markup is specifically useful or requested.
- For block themes, prefer appropriate Site Editor, template, template-part, Global Styles, Pattern, and block mechanisms when they own the concern cleanly.
- For an existing page builder/theme/plugin, use its supported configuration and public/native extension surfaces when suitable; do not convert the page/site to the preferred default stack merely for consistency with this Skill.
- For forms, reuse a suitable installed form system. Prefer Gravity Forms only when it is available/suitable or when the normal default stack is actually applicable.
- When WooCommerce is present, support store/catalog/product/category presentation, relevant WooCommerce blocks/templates/configuration, content, merchandising, responsiveness, and shop UX as normal site-building work.
- Preserve an existing custom post type, taxonomy, field/ACF model, and supported APIs when they remain fit instead of recreating the data model.
- For Custom HTML sections, return logical sections separately when that is the better mechanism for the current editor/site.
- Include complete scoped HTML/CSS. Add JavaScript only when needed, and do not assume inline `<script>` placement is permitted or best; use a verified existing centralized mechanism or the smallest justified extension when appropriate.
- Centralize genuinely shared/reusable CSS, JavaScript, or PHP instead of duplicating it across many blocks/pages.
- Never edit WordPress core or third-party theme/plugin files directly.

Read [references/design-conventions.md](references/design-conventions.md) when designing/reviewing UI, producing custom sections, or when responsive/RTL/accessibility behavior matters.

## Connected mode

When connected capabilities are available:

1. Inspect enough relevant site state to identify the current theme/child theme, editing model, relevant active plugins/workloads, content/data model, and capabilities exposed for the task.
2. Reuse current site architecture and conventions when they remain fit.
3. Prefer supported WordPress/native/plugin/theme public surfaces; do not assume only abilities owned by `wp-native-builder-bridge` are valid or useful.
4. Select the site mechanism first, then choose an actually exposed ability that can safely operate it. Gracefully use native/plugin abilities when the runtime exposes a better supported path than an older custom integration.
5. Prefer draft/preview/reversible operations while iterating.
6. Use current object/revision identity for overwrite-sensitive changes. On stale revision/conflict, re-read and reconcile instead of overwriting newer state blindly.
7. Make the smallest targeted change and preserve unrelated blocks, settings, records, and content.
8. After a write, verify the resulting state when practical. If the outcome is ambiguous, re-read before retrying so duplicate/conflicting changes are not created.
9. Do not invent an ability or assume unsupported write access. If a needed capability is unavailable, fall back to useful manual guidance or ask only for the missing material input.
10. Summarize exactly what changed and any remaining manual or approval step.

### Approval boundary

Bridge or plugin capability/permission does not itself grant user approval. Keep working through safe read-only, draft, preview, validation, preparation, and reversible steps before asking for approval.

Require approval only immediately before an action that actually publishes live content or otherwise has material impact on live content, shared/global behavior, security/permissions, customer/order/financial state, data integrity, reversibility, or another comparable consequential surface. Do not ask merely because an operation is a write if it is safely reversible and within the requested scope.

Treat the user's current explicit instruction as approval when it unambiguously directs the exact consequential action and target; do not ask for duplicate confirmation. A prior exact approval remains usable while target, scope, material effect, and decision-relevant state have not materially changed. Re-confirm only when those facts drift, the action expands, or the earlier instruction was too broad/ambiguous to cover the actual consequence.

Do not broaden ordinary WooCommerce design/site-building requests into refunds, payment actions, destructive order operations, or consequential customer/order mutations. Those actions require appropriate permissions and the applicable current approval boundary.

## Site-specific inputs

Do not force a complete intake questionnaire or a full plugin inventory. Read [references/site-profile.md](references/site-profile.md) only when project/site context is missing and a material design or implementation choice depends on it.

## Quality standard

Produce intentional, professional work rather than generic template output. Apply relevant checks for visual hierarchy, layout/spacing, typography, color/contrast, responsiveness, RTL/LTR behavior, accessibility, performance, maintainability, security, and fit to the site's audience.

Do not turn these concerns into a repeated user-facing checklist. Surface only findings or implementation details that materially affect the current request.

## WordPress-native rules

- Interpret "native-first" relative to the current site's established architecture, not as "Gutenberg/Astra only."
- Prefer Site Editor/block-theme mechanisms when a block theme owns the concern cleanly.
- Prefer the existing theme/builder/plugin's supported public/native surfaces when they fit the requirement.
- Prefer WordPress Media Library for site media and WordPress revisions/normal content APIs for content changes.
- Prefer global/native mechanisms for site-wide elements instead of duplicating page-level markup; use Patterns/Synced Patterns when suitable.
- Preserve existing page-builder ownership, content types, taxonomies, ACF/field models, plugin choices, and global configuration unless change/migration is explicitly requested and its impact is understood.
- Keep routine custom PHP out of theme files when an existing safe centralized mechanism or a small purpose-built plugin is more maintainable.
- Verify current official documentation when version-sensitive WordPress, WooCommerce, theme/plugin, Abilities API, or MCP behavior materially affects the implementation.
