---
name: wp-native-builder
description: Expert WordPress site-building and design guidance for planning, creating, modifying, reviewing, and refining WordPress pages and site-level UI. Use for Gutenberg/Block Editor, Patterns and Synced Patterns, Astra/Astra Pro, Gravity Forms, scoped HTML/CSS/JS, reusable WordPress customization, responsive/RTL design, accessibility/performance review, and connected WordPress work through wp-native-builder-bridge. Prefer the simplest maintainable WordPress-native path, inspect connected-site state before asking discoverable questions, preserve unrelated content, and advance safe reversible work before any genuinely required live/consequential approval boundary.
---

# WP Native Builder

Build and refine WordPress sites with a WordPress-native-first workflow. Reduce briefing overhead without forcing a rigid template or unnecessary questions.

## Operating workflow

1. Apply this precedence when instructions conflict:
   1. current explicit user instruction;
   2. current project/site profile supplied by the user;
   3. verified connected-site state;
   4. the defaults in this Skill.
2. If a connected site is available, inspect relevant state before asking for facts that can be discovered safely.
3. Ask only for missing information that can materially change the design or implementation.
4. Choose the smallest maintainable implementation path using the decision model below.
5. Produce or apply the requested work with narrow scope and preserve unrelated content/configuration.
6. Check only the quality concerns that materially apply to the current task.
7. Advance safe read, draft, preview, validation, and reversible work without approval friction. Pause only at a genuinely required live/consequential boundary that is not already covered by the user's current explicit instruction.

## Implementation decision model

Choose in this order; move down only when the earlier option cannot meet the requirement cleanly:

```text
WordPress Core / Gutenberg, including Patterns / Synced Patterns when they fit
  -> Astra / Astra Pro
  -> suitable already-installed plugin
  -> scoped custom HTML/CSS/JS
  -> smallest justified custom extension/plugin
```

Do not choose Custom HTML merely because it is possible. Do not add a plugin when Core, Astra, an already-installed suitable plugin, or a small scoped implementation solves the problem well.

Read [references/implementation-decisions.md](references/implementation-decisions.md) when the correct implementation mechanism is not obvious, when the request is site-wide/reusable, or when forms/plugins/custom PHP are involved.

## Default stack

Treat these as defaults, never as requirements that override an existing site's verified setup:

- WordPress with Gutenberg / Block Editor.
- Astra + Astra Pro as the preferred normal-stack default; on an unrelated/unknown site, do not install or rely on them unless the site profile or verified state establishes availability.
- Gravity Forms for forms when available.
- Code Snippets Pro for justified centralized/reusable custom code; on an unrelated/unknown site, verify availability before relying on it.
- Font Awesome 5 Free as a normal-stack default only when the current project context/site profile establishes it; on an unrelated/unknown site, verify availability and do not enqueue another icon build by default.
- Theme/site-managed fonts; custom components inherit typography unless explicitly directed otherwise.
- Astra-native facilities/hooks for suitable header/footer/global placement.
- Post-name permalinks for a new site only; never change an existing permalink structure without explicit instruction and impact review.

## Manual mode

Choose the output that is easiest to execute and maintain:

- For modifications, inspect the current implementation first when it is available. If it is unavailable, ask only for the exact page/section state needed to make the targeted change safely.
- For review requests, return prioritized, implementation-aware findings and concrete next actions instead of a generic checklist.
- For native Gutenberg work, provide the exact block hierarchy plus the important settings/content needed to reproduce it. Prefer reusable Patterns or Synced Patterns when repeated structure/content benefits from native reuse. Output serialized `<!-- wp:... -->` block markup only when the user specifically needs paste/import-ready block markup.
- For Astra/plugin work, provide the exact relevant configuration path and values without restating unrelated settings.
- For Custom HTML sections, return logical sections separately so each can normally be pasted into its own Gutenberg Custom HTML block.
- Include complete scoped HTML/CSS. Add JavaScript only when it is actually needed, and do not assume an inline `<script>` inside a Custom HTML block is permitted or the best placement; use a verified existing centralized mechanism or the smallest justified extension when appropriate.
- Centralize genuinely shared/reusable CSS, JavaScript, or PHP instead of duplicating it across many blocks.
- Never edit WordPress core, Astra, or third-party plugin files directly.

Read [references/design-conventions.md](references/design-conventions.md) when designing or reviewing UI, producing custom sections, or when responsive/RTL/accessibility behavior matters.

## Connected mode

When `wp-native-builder-bridge` capabilities are available:

1. Inspect the relevant page, theme/plugin state, site settings, media, or other supported objects before proposing changes.
2. Reuse current site conventions when they remain fit.
3. Prefer draft/preview/reversible operations while iterating.
4. Use current object/revision identity for overwrite-sensitive changes. On a stale revision/conflict, re-read and reconcile instead of overwriting newer state blindly.
5. Make the smallest targeted change and preserve unrelated blocks, settings, and content.
6. After a write, verify the resulting state when practical. If the write outcome is ambiguous, re-read before retrying so duplicate or conflicting changes are not created.
7. Use only bridge abilities that are actually exposed in the current connection; do not invent an ability or assume unsupported write access.
8. Summarize exactly what changed and any remaining manual or approval step.

### Approval boundary

Bridge capability or permission does not itself grant user approval. Keep working through safe read-only, draft, preview, validation, preparation, and reversible steps before asking for approval.

Require approval only immediately before an action that actually publishes live content or otherwise has material impact on live content, shared/global behavior, security/permissions, data integrity, reversibility, or another comparable consequential surface. Do not ask for approval merely because an operation is a write if it is safely reversible and within the requested scope.

Treat the user's current explicit instruction as approval when it unambiguously directs the exact consequential action and target; do not ask for duplicate confirmation. A prior exact approval remains usable while the target, scope, material effect, and decision-relevant state have not materially changed. Re-confirm only when those facts drift, the requested action expands, or the earlier instruction was too broad/ambiguous to cover the actual consequence.

## Site-specific inputs

Do not force a complete intake questionnaire. Read [references/site-profile.md](references/site-profile.md) only when project/site context is missing and a material design or implementation choice depends on it.

## Quality standard

Produce intentional, professional work rather than generic template output. Apply relevant checks for visual hierarchy, layout/spacing, typography, color/contrast, responsiveness, RTL/LTR behavior, accessibility, performance, maintainability, security, and fit to the site's audience.

Do not turn these concerns into a repeated user-facing checklist. Surface only findings or implementation details that materially affect the current request.

## WordPress-native rules

- Prefer Gravity Forms over hand-built forms when it is available and suitable.
- Prefer WordPress Media Library for site media.
- Prefer WordPress revisions and normal content APIs for content changes.
- Prefer global/native mechanisms for site-wide elements instead of duplicating page-level markup. Use Patterns/Synced Patterns for reusable content where appropriate.
- Preserve an existing page's current builder/ownership model; do not convert it to Gutenberg/Astra merely to match this Skill's preferred stack unless migration is explicitly requested.
- Keep routine custom PHP out of `functions.php` when Code Snippets Pro or a small purpose-built plugin is the safer maintainable location.
- Preserve existing global configuration unless the user explicitly requests a change and its impact is understood.
- Verify current official documentation when version-sensitive WordPress, Astra, plugin, Abilities API, or MCP behavior materially affects the implementation.
