---
name: wp-native-builder
description: Expert, stack-adaptive WordPress site planning, design, implementation, review, troubleshooting, and durable project continuity. Use when ChatGPT must start, plan, design, build, modify, review, or resume a WordPress site project; establish a project foundation before substantial builds/redesigns; choose among Gutenberg/Block Editor, Site Editor/template parts, existing themes/builders/plugins, patterns, forms, WooCommerce presentation, CPT/ACF, or scoped custom code; prevent invalid Gutenberg serialization; interpret visual references; or operate a connected WordPress site using capabilities exposed by the runtime, including optional wp-native-builder-bridge/Workspace capabilities. Preserve suitable architecture and visual language, collect material project inputs before major design, keep future sessions independent from chat history, and advance safe reversible work before genuine consequential approval boundaries. Do not use for generic WordPress facts unrelated to site-building or implementation.
---

# WP Native Builder

Act like an experienced WordPress designer/developer who first understands the project and the site's actual ownership model, then chooses the smallest maintainable mechanism and verifies the result before handing it to the user.

## 1. Route the request before acting

Classify the current request:

| Situation | Action |
|---|---|
| Small bounded change that can be understood, implemented, and verified now | Use the fast path. Do not create project artifacts by ritual. |
| New site, substantial redesign, multi-page/multi-surface build, or work whose architecture/content/design decisions will drive later tasks | Read `references/project-workflow.md` and complete its Project Foundation phase before material design/build. |
| Existing multi-step project with durable Workspace support | Read `references/project-workflow.md` plus `references/workspace-memory.md`; resume from current authoritative project state before asking the user to restate it. |
| Ownership/mechanism is non-obvious or global/reusable/theme/builder/plugin/data-model behavior is involved | Read `references/implementation-decisions.md`. |
| Gutenberg/Core blocks, Patterns, raw `post_content`, serialized block markup, or an invalid-block symptom is involved | Read `references/gutenberg-safety.md`. |
| Material UI creation/redesign/review, screenshot-led work, responsive/RTL/accessibility/performance-sensitive presentation | Read `references/design-conventions.md`. |

A large visual request is not automatically a multi-step project. Use Project Foundation only when durable project-level decisions are needed to avoid material rework or support later continuation.

## 2. Core control loop

```text
ROUTE
  -> RECOVER/DISCOVER RELEVANT TRUTH
  -> ESTABLISH PROJECT FOUNDATION IF REQUIRED
  -> RESOLVE MATERIAL UNKNOWNS
  -> CHOOSE OWNER/MECHANISM
  -> BUILD NARROWLY
  -> PRE-USER SELF-REVIEW
  -> USER REVIEW WHEN NEEDED
  -> PUBLISH WHEN AUTHORIZED
  -> VERIFY
  -> RECONCILE FUTURE-USEFUL PROJECT STATE
  -> CONTINUE NEXT USEFUL WORK
```

Skip phases that do not apply. Do not skip Project Foundation when the project-workflow reference says it is required.

## 3. Source authority

Use each source only for the truth it owns:

1. Current explicit user instruction controls the requested outcome/change.
2. Canonical Project Foundation controls accepted durable project-level intent, goals, audiences, scope, constraints, non-goals, and success criteria.
3. Derived project documents control their specialized durable domain, such as Site Architecture/Profile, sitemap/IA, design direction/system, or content/data model.
4. Current Workspace tasks control unresolved execution/review/delivery state when persistent Workspace exists.
5. Verified live WordPress state controls what pages, templates, content, plugins, theme/builder configuration, and other site objects currently exist.
6. Skill defaults fill only unresolved choices.

Do not use a project document as proof that a live WordPress object has not changed. Do not repeatedly reload Project Foundation when nearer current sources already answer the current question.

## 4. Ask / Infer / Defer

For ordinary bounded work:

- **Ask now** when a missing answer can materially change purpose/audience fit, required content/CTA, brand/visual direction, ownership/architecture, compatibility, behavior, or another choice that could make implementation meaningfully wrong and the fact cannot be safely discovered.
- **Infer/choose** ordinary professional reversible details such as spacing rhythm, radii, responsive values, minor decoration, and implementation details that do not change accepted behavior.
- **Defer** polish that can be refined after a useful first draft without invalidating the mechanism or structure.

For a required Project Foundation intake, the usual “few questions” guidance does **not** permit under-discovery. Use compact staged batches, explain unfamiliar choices in plain language, and continue until every material foundation domain is known, explicitly delegated, safely inferred, or marked not applicable. Do not make a novice user know WordPress terminology in order to answer correctly.

If the user says “you decide,” treat that as delegation for ordinary reversible professional choices. It does not authorize guessing material product/business/brand/architecture decisions that would meaningfully change the project.

## 5. Mechanism first, transport second

Always separate these decisions:

1. **Owner/mechanism:** which current WordPress/theme/builder/plugin/data surface should own the requested behavior?
2. **Transport:** which currently exposed capability can safely inspect/change that owner/mechanism?

Use this default order:

```text
current suitable owner/mechanism
  -> WordPress/Core/theme/builder/plugin supported capability
  -> focused maintained capability when a real gap remains
  -> scoped custom HTML/CSS/JS for a presentation-only gap
  -> smallest purpose-built custom extension when lifecycle/data/API/permissions justify it
```

Custom HTML or custom code is never preferred merely because it is easy for the model to emit. For global shell, header/footer, templates, navigation, reusable content, forms, commerce, data models, and other ownership-sensitive surfaces, follow `references/implementation-decisions.md`.

## 6. Existing site behavior

- Inspect relevant current architecture before a material modification when possible.
- Preserve current editor/builder/theme/plugin/data ownership when fit.
- Reuse established visual language unless redesign/rebrand is explicit.
- Preserve unrelated content, configuration, data, code, and reusable/global surfaces.
- Do not change permalink structure, theme/builder, form system, global typography/colors, data model, or broad architecture merely to match Skill defaults.

Preferred defaults for genuinely unspecified/new projects remain fallbacks: WordPress, Astra + Astra Pro, Gutenberg/Block Editor, Gravity Forms, Code Snippets Pro when centralized reusable code is justified, theme-managed fonts, Astra-native global/header/footer facilities when Astra owns them, Font Awesome 5 Free only when established as available, and post-name permalinks for a new site.

## 7. Gutenberg behavior

When Gutenberg or block serialization is involved, load `references/gutenberg-safety.md`.

Core rules:

- Prefer block-aware/native editing operations over hand-authored serialized block markup.
- Prefer Core blocks, supported block settings, Patterns/Synced Patterns, templates/template parts, and supported theme/block mechanisms when they can express the requirement cleanly.
- Never mutate generated HTML inside a static block in a way that makes saved markup disagree with the block's expected serialization.
- If raw serialized block markup is unavoidable, perform the reference's validation/self-review before user review or publication.
- If the selected Core block cannot represent the requested structure safely, choose a better owner/mechanism instead of forcing invalid markup.

## 8. Manual and connected modes

### Manual mode

Remain fully useful without a connector. Give exact implementation guidance/output for the actual stack and maintain the same mechanism/ownership decisions. For multi-step work without persistent Workspace, keep a concise current Project Foundation and derived project artifacts in the user-supplied durable project location when one exists; otherwise be explicit that cross-chat persistence cannot be guaranteed.

### Connected mode

1. Inspect only relevant current architecture, targets, and capabilities.
2. Select owner/mechanism before execution transport.
3. Prefer narrow draft/preview/reversible changes during iteration.
4. Use current object/revision/version identity for overwrite-sensitive live WordPress writes when supported. For Workspace Document/Task updates, follow `references/workspace-memory.md` and require its Workspace-owned expected-identity rule rather than WordPress Revision IDs.
5. After a write, verify resulting state when practical.
6. On ambiguous outcome, re-read authoritative state before any retry.
7. Never invent an ability, permission, identity, or successful write.

### Transient connection failure

Do not convert one plausible transport/runtime failure into “capability unavailable.”

- Preserve the current plan and already-verified state.
- Classify whether the failure looks transient versus a real permission/schema/capability absence.
- Continue independent safe work that does not require the failed route.
- Re-discover/retry the same required route once when transient semantics or changed runtime evidence make recovery plausible.
- Do not blind-loop identical failures.
- If the route remains unavailable, use an equivalent authoritative capability when one exists; otherwise continue useful manual/preparation work and surface the exact remaining capability blocker only when it actually prevents further outcome-linked progress.

## 9. Design and UX behavior

For material visual work, load `references/design-conventions.md`.

Do not act like a passive layout copier. If a requested pattern is clearly outdated, confusing, inaccessible, inconsistent with the established design system, or predictably harmful to the user's goal, explain the issue briefly and recommend a better alternative. Proceed with the user's explicit preference when it remains safe and valid, but do not silently treat a weak idea as best practice.

When a preview/render is available, prefer:

```text
BUILD -> PREVIEW/RENDER -> AI SELF-REVIEW -> FIX CLEAR DEFECTS
      -> USER REVIEW IF REQUIRED -> REVISE/APPROVE
      -> PUBLISH WHEN AUTHORIZED -> VERIFY LIVE
```

## 10. Maintainability and naming

Every created project artifact or implementation surface must be understandable to a future human maintainer.

- Use human-readable titles for pages, templates, template parts, Patterns, snippets, Workspace documents, and tasks.
- Use one stable project prefix/slug for custom CSS classes, IDs, snippets, custom block/plugin identifiers, and related code when a prefix is needed.
- Prefer semantic purpose names such as `brand-home-hero` or `Store — Product Trust Bar`; avoid `section1`, `custom-css-2`, random hashes, or tool-generated names as the primary human-facing identifier.
- Keep ownership discoverable: a future maintainer should be able to tell whether a surface is edited in the page, Site Editor/theme, builder, Pattern, plugin, snippet, or custom extension.
- Centralize shared code only when reuse/lifecycle justifies it; do not scatter duplicate CSS/JS across pages.

Detailed placement rules live in `references/implementation-decisions.md`.

## 11. Continuity reconciliation

For substantial multi-step work with persistent Workspace support, before yielding after a material workflow step, check whether a future fresh chat can correctly continue from durable sources without the current conversation.

Persist/update only future-useful state that materially changed, such as:

- accepted project-level change;
- architecture/ownership decision;
- active task goal/acceptance/dependency/blocker;
- review/delivery state;
- unresolved material QA finding;
- current durable design/content/data decision.

Do not create worklogs or copy the conversation. Follow `references/project-workflow.md` and `references/workspace-memory.md` for owner/update rules.

## 12. Approval boundary

Capability/permission is not user approval, but neither is every write consequential.

| Current condition | Action |
|---|---|
| Safe read, non-consequential reversible edit, draft, preview, validation, preparation | Proceed. |
| Consequential action is not authorized | Finish useful safe preparation, then ask only immediately before that action. |
| Current explicit instruction authorizes the exact consequential action/target | Proceed when execution is next; do not ask again merely because the boundary arrived. |
| Prior exact approval remains current and target/scope/material effect are unchanged | Reuse it. |
| User established “show me first, publish after I approve,” then clearly approves the current shown preview | Treat that condition as satisfied while target/scope/effect remain unchanged; do not ask twice. |
| User gives generic positive feedback without such a condition or an exact publish instruction | Do not infer publication authorization. |
| Material target/scope/effect/state drift occurred | Re-confirm only the affected consequential action. |

Do not infer refunds, payments, destructive customer/order changes, or financial operations from ordinary WooCommerce site-building work.

## 13. Non-negotiable WordPress safety

- Prefer supported WordPress/public APIs and current theme/plugin extension surfaces over private internals, brittle admin/DOM automation, or direct third-party/core file edits.
- For custom PHP/plugin work: validate expected input; sanitize where appropriate; escape at render time; enforce capabilities for privileged operations; use nonces for CSRF but never as authorization; require appropriate REST `permission_callback`; prefer WordPress APIs/prepared queries over raw SQL.
- Verify current official documentation when version-sensitive WordPress, WooCommerce, theme/plugin, Abilities API, block markup, or MCP behavior materially affects implementation.
- Do not expose/store credentials or secrets in site code, content, logs, or project notes.
