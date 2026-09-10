# WP Native Builder — Master Specification

Status: Canonical project specification
Repository: `ach1992/wp-native-builder`
Companion project: `ach1992/wp-native-builder-bridge`

## 1. Purpose

`wp-native-builder` is a compact, professional ChatGPT Skill for planning, designing, building, reviewing, and refining WordPress sites with a stack-adaptive, WordPress-native-first workflow.

The Skill exists to remove repeated briefing overhead while helping an AI model make good implementation decisions instead of blindly generating code. It should behave like an experienced WordPress designer/developer who inspects or uses the actual site architecture, asks only necessary questions, reuses suitable current-site capabilities, chooses the smallest maintainable implementation, and produces polished results.

The Skill is not an autonomous CMS by itself. When connected capabilities are available through `wp-native-builder-bridge` and the current WordPress runtime, it may inspect and perform supported operations. Without a connection, it must remain useful through exact, stack-aware manual guidance and implementation output.

## 2. Preferred default stack and supported architecture

The owner's common environment is a preferred/default workflow, not the only supported stack.

**Default stack != only supported stack.**

| Area | Preferred default when applicable |
|---|---|
| CMS | WordPress |
| Theme | Astra + Astra Pro |
| Editor | Gutenberg / WordPress Block Editor |
| Custom code | Code Snippets Pro when centralized/reusable code is justified |
| Icons | Font Awesome 5 Free when established by the current project/site profile |
| Fonts | Loaded/configured by the theme/site; custom components inherit typography |
| Forms | Gravity Forms |
| Header/footer/global insertion | Astra-native facilities/hooks when Astra owns the concern cleanly |
| New-site permalinks | Post name |
| Page construction | Native/current-editor mechanisms first; Custom HTML/CSS/JS only when better justified |

The Skill must adapt to the actual current site. Valid architectures can include, without creating a static compatibility list in the runtime instructions:

- classic themes or block themes/Site Editor;
- Astra, Kadence, GeneratePress, OceanWP, or other current/future themes;
- Gutenberg or existing page builders such as Elementor;
- WooCommerce;
- Gravity Forms, Fluent Forms, Contact Form 7, or another suitable installed form system;
- ACF, custom post types, taxonomies, or other established content/data models;
- SEO, multilingual, caching/performance, and other relevant plugins;
- supported current/future WordPress or plugin/theme public APIs and Abilities.

Do not install, replace, migrate, or rely on technology merely because it appears in the preferred defaults. Conversely, do not repeatedly ask about a capability already established by current project/site context.

## 3. Decision precedence

Resolve conflicts in this order:

1. Explicit instruction in the current request.
2. Current project/site profile supplied by the user.
3. Verified state of the connected WordPress site.
4. This Skill's preferred defaults.

Never change an existing site's architecture or global configuration merely to make it match a Skill default.

## 4. Core operating principle

Before choosing an implementation path, determine enough about the actual site to identify the mechanism that should own the requested behavior.

Relevant architecture can include:

- active theme and child theme;
- block theme/Site Editor vs classic theme behavior;
- current editor or page builder and ownership of the target surface;
- relevant installed/active plugins and workloads;
- WooCommerce when present;
- forms, custom post types, taxonomies, ACF/field models, or other task-relevant data structures;
- supported WordPress/theme/plugin public APIs and extension surfaces;
- connected native/plugin/Bridge abilities actually available for the task.

Do not inventory every plugin/theme by ritual. Inspect or ask only for facts that can materially change the implementation.

Use this conceptual hierarchy:

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

Separate two decisions:

1. **Implementation mechanism:** what should own the behavior on this WordPress site?
2. **Execution transport:** in connected mode, which actually exposed Ability/tool can safely operate that mechanism?

Bridge capabilities are an execution surface, not the site's architecture. Do not force an older custom Bridge integration when the runtime exposes a better supported native/plugin capability.

## 5. Interaction modes

| Mode | Expected behavior |
|---|---|
| Plan/design | Clarify only material unknowns, identify relevant stack constraints, propose structure, then choose the implementation path |
| Manual build | Give exact instructions/output for the actual editor/theme/plugins in use; use preferred defaults only when they truly apply |
| Connected build | Inspect relevant architecture/capabilities first, then apply supported narrow/reversible changes through suitable exposed Abilities |
| Modify | Read the current implementation when possible and make the smallest safe targeted change without changing ownership/stack unnecessarily |
| Review | Evaluate visual quality, responsiveness, accessibility, performance, maintainability, security, and fit with the current WordPress architecture |
| Site-level feature | Prefer the current site's appropriate global/native mechanism instead of duplicating page-level markup |
| WooCommerce presentation | Treat store/catalog/product/category design/content/presentation as normal supported site-building work when WooCommerce is present |

## 6. Questions and site profile

Ask questions only when the answer can materially change design/implementation and cannot be discovered safely from a connected site or supplied context.

Potential project-specific inputs include:

- active theme/child theme and editing model;
- relevant active plugins/workloads and connected abilities;
- content/data model such as post types, taxonomies, ACF/fields, product/catalog objects;
- site purpose and audience;
- language and RTL/LTR direction;
- visual direction and brand personality;
- colors and existing design tokens;
- full-width/boxed/container expectations;
- page goal, content, CTA, and required sections;
- reference sites or visual examples when relevant;
- project-specific compatibility constraints.

Do not force a complete site-intake questionnaire or full plugin inventory.

## 7. Design-quality standard

The Skill should produce work that looks intentional and professionally designed, not template-like or mechanically generated.

For every applicable design, reason about:

| Dimension | Expected result |
|---|---|
| Visual hierarchy | Clear primary/secondary emphasis, useful whitespace, controlled density |
| Layout | Coherent grid, alignment, spacing rhythm, sensible container behavior |
| Typography | Current-site/theme-aware, readable hierarchy, no unsupported font assumptions |
| Color | Consistent palette, sufficient contrast, restrained accents |
| Responsiveness | Desktop/tablet/mobile behavior designed intentionally |
| Accessibility | Semantic elements, heading order, keyboard/focus states, meaningful alternatives, appropriate ARIA, reduced motion |
| Performance | Avoid unnecessary assets/dependencies; protect hero/LCP imagery; use current performance stack appropriately |
| Maintainability | Reuse existing architecture; isolate custom sections; centralize only genuinely shared rules |
| Security | Use supported APIs/safe defaults; do not bypass permissions or expose unsafe server behavior |
| Creativity | Fit the site's subject/audience instead of repeating generic AI layouts |

Do not turn this table into a ritual user-facing checklist.

## 8. Editor, theme, and custom-section conventions

### Current editor/site architecture

Use the current site's established editing model when it remains suitable:

- Gutenberg-owned pages -> native blocks and Patterns/Synced Patterns when appropriate;
- block themes -> Site Editor, templates/template parts, Global Styles, Patterns, and supported block mechanisms when they own the concern;
- page-builder-owned surfaces -> preserve and use the current builder's supported mechanisms unless migration is explicitly requested;
- theme-owned presentation -> use the current theme's supported facilities when suitable;
- plugin-owned behavior -> use supported plugin configuration/APIs when that plugin already cleanly owns the feature.

When manual execution is needed, provide the exact hierarchy/settings for the actual editor in use. Output serialized block markup only when paste/import-ready markup is specifically useful or requested.

### Custom HTML/CSS/JS

Use custom code only for genuine gaps:

- keep one-off custom sections independently editable where practical;
- use unique section IDs/stable project prefixes and scoped CSS;
- use semantic HTML and logical headings;
- inherit current site typography by default;
- prefer native/current-stack behavior before JavaScript;
- do not assume inline `<script>` placement is permitted or best;
- centralize genuinely shared styles/scripts instead of duplicating them;
- avoid global selectors and unnecessary `!important`;
- use current site icon/font assets rather than injecting duplicate dependencies;
- include intentional responsive, RTL/LTR, accessibility, and reduced-motion behavior when applicable.

## 9. WordPress workload rules

- Interpret "native-first" relative to the current site's architecture, not as "Astra/Gutenberg only."
- Prefer supported WordPress/public APIs and current theme/plugin extension surfaces over file edits/private internals.
- Use a suitable installed form plugin rather than hand-building a form engine; Gravity Forms is the preferred default only when it is present/applicable.
- Preserve existing page-builder ownership unless migration is explicitly requested.
- Preserve suitable custom post types, taxonomies, ACF/field models, and data ownership instead of recreating them.
- Prefer WordPress Media Library for site media and normal revision/content APIs for content changes.
- Do not edit WordPress core or third-party theme/plugin files directly.
- Keep routine custom PHP out of theme files when an existing safe centralized mechanism or a small purpose-built plugin is more maintainable.
- For custom PHP/plugin work, validate expected input, sanitize where appropriate, escape output at render time, enforce capabilities for privileged operations, use nonces for CSRF without treating them as authorization, require suitable REST `permission_callback` checks, and prefer WordPress APIs/prepared queries over raw SQL.
- Do not change existing permalink structure without explicit instruction and impact review.

### WooCommerce

When WooCommerce is present, support ordinary site-building/design work including:

- product/catalog and category presentation;
- store/shop/product page design;
- WooCommerce blocks/templates and current theme/builder integration;
- responsive shop UX;
- product content and merchandising/presentation;
- relevant non-sensitive configuration that belongs to site presentation/structure.

Do not automatically broaden ordinary site-building work into refunds, payment operations, destructive order actions, or consequential customer/order mutations. Those actions require appropriate permissions and the applicable current user approval.

## 10. Connected-site behavior

The companion `wp-native-builder-bridge` can expose machine-readable WordPress capabilities through the WordPress Abilities API/MCP runtime, but connected capabilities may also come from native/plugin/theme Abilities exposed by the current site/runtime.

When connected:

1. inspect enough relevant state to identify current architecture and capabilities before choosing a mechanism;
2. reuse current site mechanisms/conventions when they remain fit;
3. do not assume only Bridge-owned custom abilities exist or are preferred;
4. prefer supported native/plugin/theme public capabilities when the runtime exposes a better path;
5. choose the site mechanism first, then use an actually exposed ability to operate it;
6. make narrow reversible edits instead of replacing unrelated content/configuration;
7. use current object/revision identity for overwrite-sensitive updates; on stale conflict, re-read/reconcile instead of blindly overwriting;
8. prefer draft/preview/reversible work while iterating;
9. verify write results when practical; on ambiguous outcome, re-read before retrying;
10. do not invent abilities or unsupported access; fall back to useful manual guidance when necessary;
11. summarize exact changed objects/sections and any remaining manual/approval step.

### Publishing and consequential changes

Connected capability/permission does not itself grant user approval. Continue safe read, draft, preview, validation, preparation, and reversible work before any approval request.

Approval is required only immediately before an action that actually publishes live content or otherwise has material impact on live/shared/global behavior, security/permissions, customer/order/financial state, data integrity, reversibility, or another comparable consequential surface. Do not stop merely because an operation is a write when it is safely reversible and within scope.

A current explicit user instruction counts as approval when it unambiguously directs the exact consequential action and target. Do not ask for duplicate confirmation. Re-confirm only when target, scope, material effect, or decision-relevant state materially changes, the requested action expands, or the earlier instruction was too broad/ambiguous.

If approval is still genuinely required, defer the question until all useful safe independent work is complete and state only the exact pending action/material impact needed for the user to decide.

## 11. Skill implementation requirements

The Skill itself must remain small and high-signal.

- Keep `SKILL.md` as the control plane, not a plugin/theme encyclopedia.
- Encode general stack discovery/adaptation rules rather than hundreds of named-product instructions.
- Use shallow conditional references only when repeated real workflows materially improve reliability.
- Do not add WooCommerce or other domain references speculatively; add one only when evaluation/usage proves enough recurring value to justify context and maintenance cost.
- Use short decision tables/trees only when they materially improve model choice/precision.
- Avoid duplicated instructions and generic web-design advice.
- Preserve model autonomy for ordinary reversible choices; do not force unnecessary questions, confirmations, or ceremony.
- Do not encode one site's colors, URLs, IDs, content, or brand/data values as global defaults.
- Do not depend on WPVibe or another paid/SaaS bridge.
- Verify authoritative current documentation when version-sensitive WordPress/WooCommerce/theme/plugin/Abilities/MCP behavior materially affects implementation.

Expected layout remains compact:

```text
wp-native-builder/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── site-profile.md
    ├── implementation-decisions.md
    └── design-conventions.md
```

Only retain references that prove useful during implementation/evaluation.

## 12. Representative evaluation scenarios

The Skill must eventually demonstrate at least:

1. **Preferred default stack:** Astra + Astra Pro + Gutenberg + Gravity Forms is used sensibly when it is actually the site stack.
2. **Materially different stack:** a site such as WooCommerce + Kadence + ACF is not converted toward Astra/Gravity Forms/Gutenberg solely because they are defaults.
3. **Existing suitable mechanism:** an installed theme/plugin/builder/form system is reused rather than unnecessarily replaced.
4. **Block theme:** Site Editor/templates/template parts/Global Styles are preferred when they correctly own the requested site-level concern.
5. **Existing page builder:** a builder-owned page is modified within that builder instead of being rebuilt in the preferred stack unless migration is requested.
6. **Connected capability adaptation:** native/plugin/theme abilities exposed by the runtime can be selected when they are a better supported execution path than an older custom integration.
7. **Manual fallback:** useful stack-aware guidance remains available with no Bridge connection.
8. **WooCommerce presentation:** ordinary store/catalog/product UX/design work is supported without drifting into sensitive commerce operations.
9. **Approval:** safe reversible preparation continues without friction; exact consequential instructions are not redundantly reconfirmed; sensitive customer/order/financial mutations remain gated.
10. **Compactness:** the Skill remains a small control layer with no speculative plugin/theme encyclopedia.

## 13. Non-goals

- Becoming a complete general-purpose WordPress administration or commerce-operations system unrelated to site building/design.
- Treating Astra, Gutenberg, Gravity Forms, WooCommerce, Elementor, or any other named product as universally required.
- Maintaining a static encyclopedia of every theme/plugin.
- Recreating functionality already provided cleanly by WordPress or a suitable installed theme/plugin.
- Forcing Custom HTML for every section.
- Depending on proprietary WordPress AI services.
- Creating excessive process, output boilerplate, repeated confirmations, or checklists that slow the model.

## 14. Success criteria

A usable/current revision is successful when:

- a valid packaged ChatGPT Skill exists and can be installed;
- preferred-default-stack requests require materially less repeated briefing;
- the Skill identifies enough actual architecture to choose mechanisms intelligently;
- materially different WordPress stacks are not forced toward the preferred defaults;
- existing suitable native/theme/builder/plugin/data-model capabilities are reused;
- native/public/supported surfaces are preferred over replacement or brittle private integration;
- WooCommerce is handled as an important site-building workload when present without broadening into sensitive commerce mutations;
- manual output remains clean, scoped, responsive, accessible, and stack-aware;
- connected mode adapts to actually exposed native/plugin/Bridge capabilities without inventing unsupported access;
- live/consequential actions remain behind explicit user approval only when approval is actually needed, without duplicate confirmation;
- representative evaluation passes without unnecessary questions, repeated approvals, excessive verbosity, fixed-stack bias, or context bloat;
- the Skill remains compact and progressively loaded.

## 15. Delivery

Delivery target for source refinements: a validated `skill.zip` generated from the repository's distributable Skill paths, with the repository remaining source of truth for future revisions.

Public version/tag/release publication is a separate release action. The implementation should move quickly: reconcile requirements, make the smallest correct stack-adaptive change, evaluate representative behavior, package it, and iterate from real usage rather than pre-building a compatibility framework.
