# WP Native Builder — Master Specification

**Status:** Canonical durable product/project specification  
**Repository:** `ach1992/wp-native-builder`  
**Companion runtime:** `ach1992/wp-native-builder-bridge`

This document defines the stable product intent and architectural constraints for WP Native Builder. It is not a changelog, release log, recovery checkpoint, or copy of issue history. Current implementation and release history belong to Git, GitHub Issues/Pull Requests/Actions, and GitHub Releases.

## 1. Product purpose

WP Native Builder is a compact ChatGPT Skill for professional WordPress site planning, design, implementation, review, troubleshooting, and lightweight project continuity.

The Skill should behave like an experienced WordPress designer/developer: understand enough of the real site and design intent to choose the correct owner/mechanism, reuse suitable existing architecture, make the smallest maintainable change, and produce polished results without unnecessary questioning or process ceremony.

The Skill must remain useful in both modes:

- **Manual:** provide exact, stack-aware guidance/output without requiring a connector.
- **Connected:** inspect and operate WordPress only through capabilities actually exposed by the current runtime.

The Skill is not a CMS by itself and does not make the connector or Bridge the site's architecture.

## 2. Stable product principles

1. **Stack-adaptive, not stack-forcing.** Existing suitable site architecture outranks preferred defaults.
2. **WordPress-native/public/supported surfaces first.** Prefer supported ownership and APIs over brittle internals or direct third-party file edits.
3. **Mechanism first, transport second.** Decide what should own the behavior before choosing which tool/Ability executes it.
4. **Evidence before questions.** Discover decision-relevant facts when possible; ask only for material unknowns.
5. **Smallest maintainable change.** Preserve unrelated content, configuration, data, visual language, and ownership.
6. **Strong design quality.** Visual work should be intentional, responsive, accessible, performant, maintainable, and appropriate to the site's audience and brand.
7. **Low-friction safety.** Routine non-consequential reversible work should not trigger repetitive confirmation; consequential boundaries still require valid authorization.
8. **Progressive context.** Keep `SKILL.md` compact and load detailed references only when relevant.
9. **Lightweight continuity.** Persistent Workspace state stores only future-useful project context, not full chats or duplicated live WordPress content.
10. **Live state wins.** Workspace/project memory never authorizes blind overwrite of newer live WordPress state.

## 3. Source authority

Use each source for the question it owns:

1. Current explicit user instruction controls the requested outcome/change.
2. Supplied project/brand/visual context controls project-specific intent and constraints.
3. Verified connected WordPress state controls what currently exists and is active.
4. Persistent Workspace state, when available, supplies durable project intent, accepted decisions, unresolved progress, and useful references.
5. Skill defaults fill only unresolved choices.

A stored Workspace note that says something is complete is not proof that a live WordPress object is unchanged. Re-read current live state before overwrite-sensitive work when that state matters.

## 4. Preferred defaults and stack adaptation

When a new or unspecified project has no better established stack, preferred defaults are:

| Area | Preferred default when applicable |
|---|---|
| CMS | WordPress |
| Theme | Astra + Astra Pro |
| Editor | Gutenberg / Block Editor |
| Forms | Gravity Forms |
| Reusable custom code | Code Snippets Pro when a centralized code-management mechanism is justified |
| Typography | Theme/site-managed fonts |
| Icons | Font Awesome 5 Free only when the current project/site establishes it is available |
| Global Astra concerns | Astra-native facilities when Astra cleanly owns the concern |
| New-site permalinks | Post name |

These are fallbacks, not migration targets. A site using a block theme, Elementor, Kadence, another form system, WooCommerce, ACF, CPTs, or another established architecture must not be converted merely to match defaults.

## 5. Ask / infer / defer

Before a substantial design or architecture decision:

- **Ask now** only when a missing answer can materially change audience/purpose fit, required content/CTA, brand/visual direction, architecture/ownership, compatibility, or another choice that could make the first implementation meaningfully wrong, and the fact cannot be discovered safely.
- **Infer/choose** ordinary professional reversible details such as spacing rhythm, radii, common responsive values, minor decoration, and routine component styling when no explicit constraint exists.
- **Defer** polish that can be refined after a useful first draft without invalidating mechanism or structure.

When questions are genuinely needed, ask one compact batch of the highest-impact unknowns rather than an intake interview. Do not reopen settled inputs unless current instruction or evidence materially conflicts with them.

## 6. Mechanism selection

Use this conceptual order:

```text
REQUEST
  -> identify relevant current site architecture and owner of the target behavior
  -> reuse an existing suitable WordPress/theme/builder/plugin/data mechanism
  -> prefer supported public/native extension surfaces
  -> when a real capability gap remains, compare a focused maintained capability with scoped custom code or a small custom extension
  -> choose the lowest-burden path that satisfies quality, editability, lifecycle, compatibility, accessibility, performance, maintainability, and security

CONNECTED EXECUTION
  -> discover abilities that actually exist now
  -> choose an ability that safely operates the selected mechanism
```

Do not choose site architecture merely because a connected tool happens to expose one operation. Native/theme/plugin abilities can be preferable to Bridge-owned abilities when they better match the selected mechanism.

## 7. WordPress implementation rules

- Preserve the current editor/builder/theme/plugin ownership when fit.
- Gutenberg-owned content should use Core blocks/Patterns when appropriate.
- Block-theme global/template concerns should use Site Editor, templates/template parts, Global Styles, Patterns, and supported block mechanisms when they own the concern.
- Existing page-builder-owned surfaces should remain in that builder unless migration/redesign is explicit.
- Reuse suitable installed form systems instead of recreating submission, validation, anti-spam, storage, or notifications.
- Preserve suitable CPT/taxonomy/ACF/field models and established data ownership.
- Use WordPress Media Library and normal content/revision APIs for site media/content where appropriate.
- Use scoped HTML/CSS/JS only when it is the better mechanism; avoid global selectors and unnecessary dependencies.
- Centralize genuinely shared code only when reuse/lifecycle justifies it.
- Never edit WordPress core or third-party plugin/theme files directly.
- Custom PHP/plugin work must follow WordPress validation, sanitization, escaping, capability, nonce/CSRF, REST permission, and prepared-query conventions.
- Do not change existing permalink structure or other broad global architecture merely to match defaults.

### WooCommerce

Ordinary builder scope includes product/catalog/category/store presentation, shop/product/archive UX, WooCommerce blocks/templates, theme/builder integration, merchandising presentation, product content, and relevant non-sensitive presentation/structure settings.

Do not silently broaden ordinary site-building into refunds, payment actions, destructive order/customer mutation, or consequential financial operations. Those are separate sensitive operations requiring applicable capabilities and authorization.

## 8. Design and review standard

For substantial visual work, derive a coherent direction from the page goal, audience, content, current visual language, brand constraints, and visual references before composing components.

Applicable quality dimensions include:

- hierarchy and content clarity;
- coherent layout/grid/container/spacing rhythm;
- typography appropriate to active fonts/script/language;
- restrained color/depth roles and sufficient contrast;
- intentional desktop/tablet/mobile recomposition;
- correct RTL/LTR directional behavior;
- semantic structure, keyboard/focus behavior, labels/alternatives, and appropriate ARIA;
- restrained purposeful motion with reduced-motion support when needed;
- performance-aware media/assets and no duplicate frameworks/fonts/icon libraries;
- maintainable ownership and scope;
- visual character appropriate to the project rather than generic AI-template patterns.

When rendering/preview is available and material, use a proportional loop:

```text
BUILD -> PREVIEW/RENDER -> AI SELF-REVIEW -> USER REVIEW WHEN THE WORKFLOW REQUIRES IT
      -> REVISE/APPROVE -> PUBLISH WHEN AUTHORIZED -> VERIFY LIVE
```

Do not force this ceremony onto tiny reversible changes.

## 9. Approval and consequential actions

Technical capability or permission is not automatically user approval, but neither is every write consequential.

The Skill may proceed through safe reads, drafts, previews, validation, preparation, and non-consequential reversible edits within scope. Treat an action as consequential when it actually publishes live content or materially affects shared/global behavior, security/permissions, customer/order/financial state, data integrity, difficult reversibility, or a comparable surface.

A current explicit instruction counts as authorization when it unambiguously directs the exact consequential action and target. Do not ask for duplicate confirmation merely because execution is next. Prior exact approval remains usable while target, scope, material effect, and decision-relevant state remain materially unchanged. Re-confirm only the affected action after meaningful drift or expansion.

Generic positive feedback is not publication authorization unless a previously established condition clearly makes approval of the current preview the publish trigger.

## 10. Connected execution

When a WordPress runtime is connected:

1. inspect only relevant current architecture, targets, and abilities;
2. select the site mechanism before the execution transport;
3. prefer narrow draft/preview/reversible operations during iteration;
4. use current object/revision/version identity for overwrite-sensitive live WordPress writes when supported;
5. on stale/conflict state, re-read and reconcile rather than blindly overwriting;
6. after writes, verify resulting state when practical;
7. on ambiguous outcomes, re-read authoritative state before any retry;
8. never invent an ability, permission, identity, or successful mutation;
9. fall back to useful manual output when no safe connected route exists.

## 11. Persistent Workspace contract

Persistent Workspace is optional and capability-driven. It exists to reduce repeated briefing across multi-session site projects without becoming a chat archive, duplicate CMS, or heavyweight project-management system.

### 11.1 Resume and progressive loading

A resumed connected project should:

1. request a compact orientation/resume packet;
2. identify only useful current focus, active/review-blocked work, blockers, and document references;
3. fetch only the task/document details needed for the next decision/action;
4. reuse settled durable intent rather than asking the user to restate it;
5. re-read live WordPress state before modifying a target when current state matters;
6. continue the next useful action instead of stopping at a recovery summary.

### 11.2 Retention

Persist only information that a future session materially needs and that is not better recovered from a stronger source. Suitable examples include a concise project brief, site profile, sitemap/IA decision, design-system direction, content/data model, lasting decision, unresolved QA finding, or active task.

Never persist full chats, hidden reasoning/chain-of-thought, routine worklogs, repeated checkpoint prose, copied live content merely to mirror WordPress, credentials/secrets, or unnecessary customer/order/payment/financial payloads.

### 11.3 Documents and tasks

Documents are Markdown-oriented durable context. Tasks are lightweight execution-oriented state. A task may hold concise goal, acceptance, dependencies/blocker, target references, and durable notes when useful.

Keep these task dimensions separate:

| Dimension | Values |
|---|---|
| Progress | `todo` / `in_progress` / `blocked` / `done` |
| Review | `not_required` / `pending` / `changes_requested` / `approved` |
| Delivery | `not_applicable` / `draft_preview` / `live` |

`done` does not imply `approved`; `approved` does not imply `live`; delivery should reflect actual verified state.

### 11.4 Concurrency and revision independence

Workspace Document/Task current state must use Workspace-owned optimistic-concurrency identity independent of WordPress Revision IDs, such as `version + state_hash`.

For overwrite-sensitive Workspace updates:

1. read the current Workspace object and its current identity;
2. require the update capability to accept that expected identity;
3. if no such guard exists, do not perform a blind overwrite;
4. if stale/mismatched/conflicted, re-read current state, reconcile newer valid work, then retry only if still correct;
5. if write outcome is ambiguous, re-read authoritative state before any retry.

Workspace resume/current state/stale-write protection must remain usable when WordPress Revisions are disabled, limited, or pruned. Ordinary Posts/Pages/live WordPress content may continue to use the revision/history mechanisms appropriate to their actual surface.

### 11.5 Companion Bridge boundary

The Skill repository owns Skill behavior and the logical Workspace contract. The companion Bridge repository owns the concrete WordPress storage/API/admin implementation.

The logical Workspace capability roles are:

- `workspace-resume` — compact orientation;
- `workspace-document` — list/get/create/update/archive durable documents;
- `workspace-task` — list/get/create/update/transition/archive lightweight tasks.

Treat these as logical roles, not names to invent. Discover the current runtime and use only capabilities whose documented behavior safely matches the required operation. The maintained companion Bridge implements this contract for the supported direct connected setup, while the Skill remains capability-driven so absence or future transport differences degrade gracefully to manual continuity.

Detailed Workspace architecture is maintained in [`docs/PROJECT-WORKSPACE-ARCHITECTURE.md`](docs/PROJECT-WORKSPACE-ARCHITECTURE.md).

## 12. Lightweight project progression

Small requests that can be completed and verified now stay on the normal fast path and should not create permanent project artifacts by ritual.

For genuinely multi-step site work, use only enough project structure to reduce rework and support continuation:

```text
RESUME / DISCOVER -> UNDERSTAND -> PLAN ENOUGH TO ACT -> BUILD -> VERIFY
  -> REVIEW WHEN MATERIAL -> REVISE / APPROVE -> PUBLISH WHEN AUTHORIZED
  -> VERIFY LIVE -> UPDATE USEFUL PROJECT STATE -> NEXT USEFUL WORK
```

When the requested outcome is a complete/launch-ready site, project completion is not inferred merely because individual tasks are done. Synthesize only applicable launch concerns such as navigation/content completeness, responsive/RTL behavior, accessibility, forms/interactions, links/media, material performance effects, important indexing-facing presentation/configuration, publication, and live verification. Do not impose a fixed giant launch checklist.

## 13. Runtime architecture

The distributable Skill must remain small and progressively loaded:

```text
wp-native-builder/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── design-conventions.md
    ├── implementation-decisions.md
    ├── project-workflow.md
    └── workspace-memory.md
```

`SKILL.md` is the compact control plane. References are shallow and loaded conditionally. Do not add a product/plugin encyclopedia or restore removed references merely for historical symmetry. Add a reference only when its conditional-loading benefit materially repays context and maintenance cost.

## 14. Non-goals

- General-purpose WordPress administration or commerce operations unrelated to site building/design.
- Forcing Astra, Gutenberg, Gravity Forms, WooCommerce, Elementor, or any named product universally.
- Maintaining a static encyclopedia of themes/plugins.
- Recreating functionality already cleanly owned by WordPress or a suitable installed capability.
- Forcing Custom HTML or custom code for every section.
- Depending on proprietary hosted WordPress AI services.
- Recreating GitHub/Jira-style project orchestration inside WordPress.
- Treating every request as a persistent task.
- Storing chat transcripts, chain-of-thought, secrets, or broad live-site/database mirrors in Workspace.
- Adding vector-memory/RAG infrastructure or an external persistence service merely for project continuity.
- Excessive output boilerplate, repeated confirmations, or process ceremony.

## 15. Success criteria

A release-quality revision should demonstrate that:

- a valid installable ChatGPT Skill can be packaged from the intended runtime files;
- actual site architecture is understood well enough to choose mechanisms intelligently;
- materially different WordPress stacks are not forced toward preferred defaults;
- suitable native/theme/builder/plugin/data mechanisms are reused;
- design output is coherent, responsive, accessible, performant, and maintainable;
- manual mode remains strong without a Bridge;
- connected mode adapts to capabilities actually exposed by the runtime without inventing access;
- Workspace recovery is compact/progressive and reduces repeated briefing;
- Workspace stale/ambiguous writes reconcile instead of overwriting newer state;
- live WordPress remains authoritative for actual site state;
- safe reversible work advances without unnecessary confirmation while genuine consequential actions remain properly authorized;
- WooCommerce presentation remains supported without accidental expansion into sensitive commerce operations;
- the Skill remains compact and progressively loaded.

## 16. Repository and release model

Repository roles are intentionally separated:

| Path/system | Responsibility |
|---|---|
| `README.md` | User-facing installation and usage guide |
| `SKILL.md` + `references/` + `agents/` | Installable runtime Skill |
| `MASTER-SPEC.md` | Canonical durable product/project requirements |
| `docs/architecture.md` | Concise maintained architecture overview |
| `docs/PROJECT-WORKSPACE-ARCHITECTURE.md` | Detailed Workspace/cross-chat project architecture |
| Git history / Issues / PRs | Implementation history and unresolved work |
| Actions / Releases | Validation and immutable public delivery evidence |

Repository-only documentation is not bundled into `skill.zip`. The public package must contain only intentional runtime files and be validated through the current standard Skill validation/package flow before release.
