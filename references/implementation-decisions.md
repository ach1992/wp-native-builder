# Implementation Decisions

Use this reference when selecting the WordPress mechanism is non-trivial or the change is reusable/site-wide.

## Selection rules

| Need | Preferred path |
|---|---|
| Standard page layout/content | Gutenberg Core blocks first |
| Repeated structure with independently editable instances | Unsynced Pattern when native reuse is useful |
| Repeated content that must stay identical everywhere | Synced Pattern when native synchronized reuse fits |
| Theme layout/global presentation | Astra / Astra Pro when it owns the concern cleanly |
| Forms | Gravity Forms when available and suitable |
| Existing plugin capability | Reuse the installed plugin when it cleanly satisfies the requirement |
| One-off custom visual section | Scoped Gutenberg Custom HTML block when native blocks cannot achieve it cleanly |
| Shared CSS/JS/PHP behavior | Centralize in the smallest maintainable existing mechanism |
| Site-wide header/footer/announcement placement | Appropriate Astra/global hook or site-level mechanism |
| Capability requiring lifecycle/settings/data/API surface | Small purpose-built plugin/custom extension only when simpler options are insufficient |

## Decision checks

Before moving to a more custom mechanism, confirm that the simpler option fails on a material requirement such as fidelity, editability, reuse, behavior, accessibility, performance, maintainability, or compatibility.

Do not replace a working existing stack merely to match Skill defaults. Preserve an existing page's current builder unless migration is explicitly requested. Do not install a second plugin for capability already provided cleanly by WordPress, Astra, Gravity Forms, or an installed suitable plugin.

## Custom code placement

- Keep one-off section CSS scoped to a unique section ID or stable project prefix.
- Keep JavaScript out unless native HTML/CSS behavior is insufficient. Do not assume inline `<script>` in a Custom HTML block is supported or maintainable; use it only when the site setup is verified to support that placement.
- Move genuinely shared/reusable styles or scripts to a centralized location rather than duplicating them across page blocks.
- Put reusable/routine PHP in Code Snippets Pro when appropriate and available, or use the smallest purpose-built plugin when lifecycle, permissions, data, integration, or maintainability justify it.
- For custom PHP/plugin work, validate expected input, sanitize where appropriate, escape output at the point of rendering, enforce capabilities for privileged operations, use nonces for CSRF protection without treating them as authorization, require suitable REST `permission_callback` checks, and prefer WordPress APIs/prepared queries over raw SQL.
- Do not edit `functions.php`, WordPress core, Astra, or third-party plugin files directly for routine customization.

## Existing-site configuration

Defaults apply mainly to new work. On an existing site:

- inspect first;
- preserve the page's current builder/ownership model unless migration is explicitly requested;
- preserve permalink structure, typography, global colors, plugin choices, and other global configuration unless change is explicitly requested;
- review impact before any global setting change;
- prefer narrow changes with straightforward rollback.

## Forms

When Gravity Forms is available and suitable, use it instead of hand-coding form submission, validation, spam handling, storage, or notifications. Custom HTML may style or frame the form, but should not recreate the form engine without a justified requirement.
