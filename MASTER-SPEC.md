# WP Native Builder — Master Specification

**Status:** Canonical durable product/project specification  
**Repository:** `ach1992/wp-native-builder`  
**Companion runtime:** `ach1992/wp-native-builder-bridge`

This document defines the stable product intent and architectural constraints for WP Native Builder. It is not a changelog, session handoff, active backlog, release log, or mirror of GitHub history. Implementation and delivery history belong to Git, GitHub Issues/Pull Requests/Actions, and Releases.

## 1. Product purpose

WP Native Builder is a compact ChatGPT Skill for professional WordPress site planning, design, implementation, review, troubleshooting, and durable lightweight project continuity.

The Skill must behave like an experienced WordPress designer/developer: understand the project deeply enough to avoid rework, discover the site's real ownership model, choose the correct native/theme/builder/plugin/data mechanism before custom code, make the smallest maintainable change, self-review before user handoff, and preserve enough durable state that a future chat can continue without relying on conversation history.

The Skill must remain useful in both modes:

- **Manual:** exact, stack-aware guidance/output without requiring a connector.
- **Connected:** inspect and operate WordPress only through capabilities actually exposed by the current runtime.

The Skill is not a CMS, page builder, connector architecture, or general project-management system.

## 2. Stable product principles

1. **Foundation before substantial build.** A new site, substantial redesign, or multi-surface project must establish sufficiently complete durable project intent before material design/build begins.
2. **Proportional process.** Small bounded changes remain fast and do not require project ceremony.
3. **Stack-adaptive, not stack-forcing.** Existing suitable site architecture outranks preferred defaults.
4. **WordPress-native/public/supported surfaces first.** Prefer supported Core/theme/builder/plugin mechanisms over brittle internals or unnecessary custom markup/code.
5. **Mechanism first, transport second.** Decide what should own behavior before choosing which connected Ability/tool executes it.
6. **Evidence before questions.** Discover decision-relevant facts when possible; ask for unresolved material facts in language the user can answer.
7. **No arbitrary intake quota.** For Project Foundation work, keep asking in compact staged batches until every material project domain is known, safely inferred, delegated, or not applicable.
8. **Smallest maintainable change.** Preserve unrelated content, configuration, data, visual language, and ownership.
9. **Advisory design judgment.** Do not mechanically implement clearly weak, outdated, inaccessible, confusing, or unmaintainable UX/UI without recommending a better direction.
10. **Pre-user self-review.** Correct clear defects, architecture misuse, invalid Gutenberg serialization, and material visual/usability problems before asking the user to review when the runtime permits meaningful validation.
11. **Human-maintainable ownership and naming.** Future maintainers should be able to find what was created, where it is edited, and why it exists.
12. **Low-friction safety.** Routine non-consequential reversible work should advance without repetitive confirmation; genuine consequential boundaries still require valid authorization.
13. **Progressive context.** Keep `SKILL.md` compact and load detailed references only when their domain is relevant.
14. **Durable continuity, not chat archives.** Persist future-useful project truth only; never use full chat transcripts as project state.
15. **Live state wins for live questions.** Stored project context never proves that a current WordPress object is unchanged.
16. **Bounded transient-failure recovery.** One plausible connector/runtime transport failure is not enough to declare a required capability permanently unavailable.

## 3. Request classes

### 3.1 Fast bounded work

A small change that can be understood, implemented, verified, and completed now stays on the fast path. It does not require Project Foundation, new project documents, or permanent tasks merely because Workspace exists.

### 3.2 Foundation-required work

Use Project Foundation for:

- a new site;
- a substantial redesign/rebrand;
- a multi-page or multi-surface build;
- work where project-level audience/content/brand/functional/technical decisions will drive multiple later tasks;
- work expected to continue across chats where missing durable intent would cause material rework.

A visually large one-off page is not automatically a project if it can be correctly completed from already-established durable context.

## 4. Canonical Project Foundation

For foundation-required work, keep one canonical durable **Project Foundation** in the project's persistent Workspace or another user-supplied durable project location.

Reuse an existing equivalent project brief/specification when it already owns the accepted project-level truth. Do not create a second “master” document solely to satisfy a filename convention.

The Project Foundation owns only stable project-level truth:

- purpose and primary outcomes;
- intended audiences/users and important needs;
- scope and major deliverables/surfaces;
- required capabilities and critical interactions;
- brand/content/voice direction that materially constrains design;
- durable technical constraints and supported environments/languages;
- accessibility, RTL/LTR, localization, and responsive requirements when material;
- important business/content/SEO/legal/privacy constraints that affect the build;
- explicit non-goals/out-of-scope boundaries;
- success/completion criteria;
- material owner decisions that would change the project if reversed.

It is not a worklog, active backlog, page-content mirror, current plugin inventory, live-site snapshot, or per-task implementation record.

### 4.1 Foundation readiness

Before material design/build begins, every materially applicable domain must be one of:

- **known** from authoritative evidence/user input;
- **user delegated** for professional judgment;
- **safely inferred** without changing material project intent;
- **not applicable**.

The intake covers, proportionally: purpose/outcomes, audience, scope, content, brand/design, functionality, site architecture, technical constraints, quality constraints, governance/delivery, and success criteria.

Do not ask every possible question literally. Discover what the live site/project already reveals, then ask only unresolved material items. For novice users, ask in plain language, explain options when useful, and translate answers into technical decisions internally.

### 4.2 Foundation stability

After readiness/acceptance, Project Foundation leaves the routine hot path. Normal work uses the nearest current authoritative sources: derived architecture/design/content docs, active tasks, live WordPress, code/config, preview/review state.

Reopen/update Project Foundation only when:

- the user explicitly accepts a material change to project purpose, audience, scope, durable constraint, non-goal, or success criteria;
- current authoritative evidence materially contradicts project-level intent and a nearer source cannot resolve it;
- recovery/completion cannot otherwise be resolved safely.

An implementation-only change does not churn Project Foundation. If a material foundation change is not already explicitly directed by the user, explain its impact and consult them before changing the accepted project-level truth.

## 5. Derived project sources

Keep specialized durable truth outside Project Foundation when it deserves its own owner.

### 5.1 Site Architecture/Profile

Record recurring architecture/ownership facts such as:

- active theme/editing model;
- page builder/theme-builder ownership;
- global header/footer/navigation/template ownership;
- page-content ownership;
- reusable section/pattern mechanism;
- forms/commerce/data-model ownership;
- intentionally relied-on theme/plugin capabilities;
- approved custom-code placement and project prefix conventions.

It is not a complete plugin inventory and never replaces live discovery when current state matters.

### 5.2 Other derived documents

Create only when they materially reduce rework or improve continuation:

- sitemap/information architecture;
- design direction/system;
- content/data model;
- lasting decisions/architecture rationale;
- unresolved QA notes.

### 5.3 Tasks

Create only work that benefits from acceptance clarity, dependency/sequencing, review/delivery state, or later continuation. Keep progress, review, and delivery independent.

## 6. Source authority

Use each source for the truth it owns:

1. Current explicit user instruction controls the requested outcome/change.
2. Project Foundation controls accepted durable project-level intent.
3. Derived project documents control their specialized durable domain.
4. Workspace tasks control unresolved execution/review/delivery state when persistent Workspace exists.
5. Verified live WordPress state controls what pages/templates/content/plugins/theme/builder configuration and other current site objects actually exist.
6. Skill defaults fill only unresolved choices.

A stored note that says a page is complete is not proof the current page remains unchanged. Re-read current live state before overwrite-sensitive/current-state-dependent work.

## 7. Ask / infer / defer

For ordinary bounded work:

- **Ask now** only when a missing answer can materially change purpose/audience fit, content/CTA, visual direction, ownership/architecture, compatibility, behavior, or another choice that could make implementation meaningfully wrong and the fact cannot be safely discovered.
- **Infer/choose** ordinary professional reversible details such as spacing, radii, responsive values, minor decoration, and implementation details that preserve accepted behavior.
- **Defer** polish that can be refined later without invalidating mechanism or structure.

For Project Foundation, compact staged questioning continues until material coverage is complete. “You decide” delegates ordinary professional choices but does not justify inventing material business/product/brand/architecture requirements.

Do not reopen settled inputs later unless current instruction or authoritative evidence materially conflicts.

## 8. Preferred defaults and stack adaptation

When a genuinely new/unspecified project has no better established stack, preferred defaults are:

| Area | Preferred default when applicable |
|---|---|
| CMS | WordPress |
| Theme | Astra + Astra Pro |
| Editor | Gutenberg / Block Editor |
| Forms | Gravity Forms |
| Reusable custom code | Code Snippets Pro when centralized reusable code is justified |
| Typography | Theme/site-managed fonts |
| Icons | Font Awesome 5 Free only when established as available |
| Global Astra concerns | Astra-native facilities when Astra cleanly owns the concern |
| New-site permalinks | Post name |

These are fallbacks, never migration targets. An existing block theme, Elementor, Kadence, WooCommerce, ACF/CPT model, different form system, or other suitable architecture must not be converted merely to match defaults.

## 9. Ownership and mechanism selection

Separate:

1. **Owner/mechanism** — which WordPress/Core/theme/builder/plugin/data surface should own the requested behavior?
2. **Transport** — which currently exposed capability safely operates that owner?

Default mechanism order:

```text
current suitable owner/mechanism
  -> WordPress/Core/theme/builder/plugin supported capability
  -> focused maintained capability when a real gap remains
  -> scoped custom HTML/CSS/JS for a presentation-only gap
  -> smallest purpose-built extension when lifecycle/data/API/permissions justify it
```

Custom HTML/custom code is not preferred merely because the model can emit it easily.

### 9.1 Important ownership examples

- Block-theme header/footer/site shell -> Site Editor + templates/template parts + Global Styles/Patterns as applicable.
- Classic/theme-managed header/footer -> current theme's supported facilities; child-theme/public hooks only when justified.
- Existing builder-owned global shell -> builder's global/Theme Builder mechanism.
- Gutenberg page content -> Core blocks and supported block settings first.
- Reusable Gutenberg section -> Pattern or Synced Pattern according to reuse semantics.
- Navigation -> current theme/Site Editor/builder navigation mechanism.
- Dynamic listings -> Query Loop/Core/theme/plugin/data mechanism rather than hard-coded card copies.
- Forms -> suitable installed form system rather than rebuilding submission/validation/anti-spam/storage/notifications.
- WooCommerce presentation -> WooCommerce-supported blocks/templates/settings integrated with current theme/builder.
- Existing CPT/taxonomy/ACF model -> preserve and reuse that data ownership.

Global shell concerns are especially strong ownership signals; never default to page-local HTML when a global/theme/builder mechanism already owns them.

## 10. Gutenberg serialization safety

Treat Gutenberg block markup as a serialization contract, not arbitrary HTML with comments.

For static/hybrid blocks, stored markup can be validated against markup regenerated from parsed attributes/current block `save` behavior. Manual/external HTML changes can therefore create an invalid-block state.

Preferred write order:

1. block-aware/native editor or connected block operation;
2. supported Pattern/template/theme/builder operation;
3. raw serialized block markup only when no safer route exists and current block format is known;
4. `core/html`/Custom HTML only for intentionally freeform markup when it is actually the correct ownership model.

When raw serialized markup is unavoidable:

- preserve block delimiter/nesting structure;
- keep attributes and inner markup consistent with current registered block output;
- preserve required wrapper classes/support-generated structure;
- avoid unsupported wrappers/classes/children;
- treat third-party/custom block formats as version-sensitive;
- avoid reserializing unrelated blocks;
- re-read current `post_content` before overwrite-sensitive raw-content writes.

Before user handoff, perform every meaningful available check: ownership, structure, parse/serialize or block validation, editor preview/recovery warnings, stored-content re-read, and visual/functional verification. Never claim serialization validation when the runtime exposes no meaningful validator.

If an invalid block appears, diagnose the exact block and expected-versus-actual difference, preserve user content, repair the smallest invalid representation, and revalidate. Do not flatten an entire page to Custom HTML merely to silence validation unless that ownership change is explicitly wanted and actually better long-term.

## 11. Design, UX, and self-review

For substantial visual work, derive a coherent direction from page goal, audience, content, current visual language, brand constraints, and references before composing components.

The Skill is an advisor, not a passive copier. When a proposed design pattern is clearly weak for the stated goal—outdated, confusing, inaccessible, overly complex, inconsistent, or predictably unmaintainable—briefly identify the issue and recommend one better direction. When ordinary design judgment is delegated, implement the better direction. Respect explicit user insistence when the preference remains safe/valid, without misrepresenting it as best practice.

Applicable quality dimensions include hierarchy/content clarity, layout rhythm, typography, color/contrast, responsive recomposition, RTL/LTR, interaction, accessibility, motion, performance, and maintainable ownership.

For material visual changes where preview/render is available:

```text
BUILD -> PREVIEW/RENDER -> AI SELF-REVIEW -> FIX CLEAR DEFECTS
      -> USER REVIEW WHEN REQUIRED -> REVISE/APPROVE
      -> PUBLISH WHEN AUTHORIZED -> VERIFY LIVE
```

Self-review is required before user review when meaningful preview/validation is available. It should catch obvious layout defects, generic/weak composition, broken assets, invalid Gutenberg/recovery warnings, RTL/responsive problems, accessibility regressions, and architecture misuse.

## 12. Human-maintainable naming and ownership

Every created surface/artifact should be findable and understandable later.

- Use human-readable page/template/template-part/Pattern/snippet/Workspace-document/task names.
- Use one stable project/site prefix for custom CSS classes, IDs, snippet functions, custom block/plugin identifiers when a prefix is needed.
- Prefer semantic names such as `brand-home-hero`, `Header — Main`, `Home — Hero`, `Site — Mobile Navigation Enhancement`.
- Avoid `section1`, `Custom CSS 2`, `Untitled`, random hashes, or tool-internal names as the main maintainer-facing identity.
- Make edit ownership discoverable: page editor, Site Editor/template part, theme facility, builder-global template, Pattern, snippet, or custom extension.
- Centralize shared code only when reuse/lifecycle justifies it; do not scatter duplicate CSS/JS across pages.

## 13. Connected execution

When WordPress is connected:

1. inspect only relevant current architecture, targets, and capabilities;
2. choose owner/mechanism before transport;
3. prefer narrow draft/preview/reversible operations while iterating;
4. use current object/revision/version identity for overwrite-sensitive writes when supported;
5. on stale/conflict state, re-read/reconcile instead of blindly overwriting;
6. verify write results when practical;
7. on ambiguous write outcome, re-read authoritative state before retry;
8. never invent an ability, permission, identity, or mutation result;
9. fall back to useful manual/preparation output when no safe connected write route exists.

### 13.1 Transient connection failure

One plausible timeout/unavailable/transport failure is not proof a logical capability disappeared.

- Preserve already-recovered state/plan.
- Distinguish transient transport/runtime failure from real permission/schema/capability absence.
- Continue independent safe work.
- Re-discover/retry the required route once when transient semantics or changed runtime evidence makes recovery plausible.
- Never blind-loop identical failures.
- Use an equivalent authoritative capability when available.
- Surface a capability blocker only when the required semantics truly remain unavailable and outcome-linked progress is exhausted.

## 14. Persistent Workspace contract

Persistent Workspace is optional and capability-driven. It reduces repeated briefing without becoming a second CMS or chat archive.

Logical capability roles remain:

- `workspace-resume` — compact orientation;
- `workspace-document` — list/get/create/update/archive durable documents;
- `workspace-task` — list/get/create/update/transition/archive lightweight tasks.

These are logical roles, not names to invent. Use only exposed capabilities whose documented schema/permissions safely match the operation.

### 14.1 Project Foundation in Workspace

For foundation-required work, persist exactly one canonical Project Foundation when a suitable Workspace document capability exists. Reuse an existing equivalent. Derived architecture/design/content/task state must not be duplicated into the Foundation merely for completeness.

On normal resume, do not load the entire Workspace or automatically re-read Project Foundation. Start with compact current orientation and fetch only nearest relevant task/document details. Load Project Foundation only when project-level intent is unresolved/changed or recovery/completion requires it.

### 14.2 Retention

Persist only future-useful safe context that later sessions materially need and that is not better recovered from a stronger source. Never persist full chats, hidden reasoning, routine worklogs, copied live content merely to mirror WordPress, credentials/secrets, or unnecessary customer/order/payment/financial payloads.

### 14.3 Task dimensions

| Dimension | Values |
|---|---|
| Progress | `todo` / `in_progress` / `blocked` / `done` |
| Review | `not_required` / `pending` / `changes_requested` / `approved` |
| Delivery | `not_applicable` / `draft_preview` / `live` |

`done` does not imply `approved`; `approved` does not imply `live`; delivery reflects actual verified state.

### 14.4 Workspace concurrency

Workspace Document/Task current state uses Workspace-owned identity independent of WordPress Revision IDs, such as `version + state_hash`.

For overwrite-sensitive updates:

1. read current Workspace object + identity;
2. require update to accept expected identity;
3. if no guard exists, do not blindly overwrite;
4. submit with expected identity;
5. verify resulting state when practical;
6. on stale/mismatch/conflict, re-read/reconcile newer valid work before retry;
7. on ambiguous write outcome, re-read authoritative state before any retry.

Workspace resume/current-state/stale-write protection must remain usable when WordPress Revisions are disabled, limited, or pruned.

## 15. Continuity reconciliation

For substantial multi-step work, before yielding after a material workflow step ask internally:

> Could a fresh chat continue correctly from durable sources without this conversation?

If not and suitable persistent capability exists, update the smallest authoritative object owning the changed future-useful truth. Examples: Project Foundation for accepted project-level change; Site Architecture/Profile for ownership changes; design doc for accepted recurring design decisions; task for goal/acceptance/blocker/review/delivery; QA doc/task for unresolved material finding.

Do not create session logs or duplicate live content.

## 16. Approval and consequential actions

Technical capability/permission and user approval are separate, but not every write is consequential.

Safe reads, validation, preparation, drafts/previews, and non-consequential reversible edits may proceed within scope. Treat an action as consequential when it actually publishes live content or materially affects shared/global behavior, security/permissions, customer/order/financial state, data integrity, difficult reversibility, or a comparable surface.

A current explicit instruction can authorize the exact consequential action/target. Do not ask again merely because execution is next while target/scope/material effect remain unchanged. Re-confirm only affected actions after meaningful drift/expansion.

Generic positive feedback is not publication authorization unless an established review condition clearly makes approval of the current preview the publish trigger.

## 17. WordPress safety and domain boundaries

- Prefer supported WordPress/public APIs and current theme/plugin extension surfaces over private internals, brittle admin/DOM automation, or direct file edits.
- Never edit WordPress Core or third-party plugin/theme files directly.
- For custom PHP/plugin work: validate expected input; sanitize where appropriate; escape at render time; enforce capabilities; use nonces for CSRF but never authorization; require appropriate REST `permission_callback`; prefer WordPress APIs/prepared queries over raw SQL.
- Verify current official documentation when version-sensitive WordPress, WooCommerce, theme/plugin, Abilities API, block markup, or MCP behavior materially affects implementation.
- Do not expose/store credentials or secrets in generated site code, content, logs, or project notes.

### WooCommerce

Ordinary builder scope includes product/catalog/category/store presentation, shop/product/archive UX, WooCommerce blocks/templates, theme/builder integration, merchandising presentation, product content, and relevant non-sensitive presentation/structure settings.

Do not silently broaden site-building into refunds, payment actions, destructive order/customer mutation, or consequential financial operations.

## 18. Lightweight project progression

For genuinely multi-step projects:

```text
RESUME / DISCOVER
  -> FOUNDATION INTAKE IF REQUIRED
  -> FOUNDATION READY
  -> DERIVE/REFRESH RELEVANT DOCS/TASKS
  -> PLAN ENOUGH TO ACT
  -> BUILD
  -> VERIFY
  -> REVIEW WHEN MATERIAL
  -> REVISE / APPROVE
  -> PUBLISH WHEN AUTHORIZED
  -> VERIFY LIVE
  -> RECONCILE FUTURE-USEFUL STATE
  -> NEXT USEFUL WORK
```

Do not turn project setup into speculative documentation. After Foundation readiness, begin useful implementation once enough architecture/sequencing exists to avoid predictable rework.

For complete/launch-ready site outcomes, individual task completion is not enough. Synthesize only launch concerns that materially apply: navigation/content completeness, responsive/RTL behavior, accessibility of key flows, forms/interactions, links/media, material performance effects introduced by the build, important indexing-facing presentation/configuration, publication, and live verification.

## 19. Runtime architecture

The distributable Skill remains compact and progressively loaded:

```text
wp-native-builder/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── design-conventions.md
    ├── gutenberg-safety.md
    ├── implementation-decisions.md
    ├── project-workflow.md
    └── workspace-memory.md
```

`SKILL.md` is the control plane. References remain shallow and conditionally loaded. Do not add a product/plugin encyclopedia or duplicate policy across multiple files without a clear runtime reliability benefit.

## 20. Non-goals

- General-purpose WordPress administration or commerce operations unrelated to site building/design.
- Forcing Astra, Gutenberg, Gravity Forms, WooCommerce, Elementor, or any named product universally.
- Maintaining a static encyclopedia of themes/plugins.
- Recreating functionality already cleanly owned by WordPress or a suitable installed capability.
- Forcing Custom HTML/custom code for every section.
- Recreating GitHub/Jira-style orchestration inside WordPress.
- Treating every request as a persistent task or every page as a project.
- Loading Project Foundation on every chat/task/page merely because it exists.
- Storing chat transcripts, hidden reasoning, secrets, or broad live-site/database mirrors in Workspace.
- Adding vector-memory/RAG or an external persistence service merely for continuity.
- Blind retry loops when a connector fails.
- Excessive output boilerplate, repeated confirmations, or process ceremony.

## 21. Success criteria

A release-quality revision should demonstrate that:

- standard Skill validation/package succeeds;
- small bounded work remains fast and low-ceremony;
- a new/substantial project does not begin material design/build with unresolved material foundation gaps;
- novice users can complete intake without knowing WordPress terminology;
- one canonical Project Foundation remains stable and leaves the hot path after readiness;
- resume normally uses nearest current authoritative sources rather than rereading the Foundation or old chat;
- header/footer/global/template concerns route to their actual theme/Site Editor/builder owner rather than page-local HTML by default;
- Core blocks/Patterns/native mechanisms are preferred when they cleanly fit;
- raw Gutenberg serialization receives explicit validation/self-review and invalid blocks are repaired narrowly;
- design output is coherent, responsive, accessible, performant, maintainable, and professionally challenged when the requested approach is clearly weak;
- naming/ownership remains understandable to future humans;
- connected mode tolerates bounded transient route failure without immediately declaring the project blocked;
- material future-useful state is reconciled so a replacement chat can continue;
- Workspace stale/ambiguous writes reconcile instead of overwriting newer state;
- live WordPress remains authoritative for current live-site state;
- safe reversible work advances without unnecessary confirmation while genuine consequential actions remain properly authorized;
- manual mode remains strong without Bridge/Workspace.

Behavioral regression scenarios are maintained in `docs/BEHAVIOR-EVALS.md`.

## 22. Repository and release model

| Path/system | Responsibility |
|---|---|
| `README.md` | User-facing installation/usage guide |
| `SKILL.md` + `references/` + `agents/` | Installable runtime Skill |
| `MASTER-SPEC.md` | Canonical durable product/project requirements |
| `docs/architecture.md` | Concise maintained runtime architecture overview |
| `docs/PROJECT-WORKSPACE-ARCHITECTURE.md` | Detailed Workspace/cross-chat continuity architecture |
| `docs/BEHAVIOR-EVALS.md` | Behavioral regression scenarios for Skill changes |
| Git history / Issues / PRs | Implementation history and unresolved work |
| Actions / Releases | Validation and immutable public delivery evidence |

Repository-only documentation is not bundled into `skill.zip`. Public release packaging must use OpenAI's standard Skill validation/package flow and the archive name remains exactly `skill.zip`.
