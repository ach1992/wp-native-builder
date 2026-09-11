# WP Native Builder — Project Workspace Architecture

This document defines the durable architecture for lightweight WordPress-hosted project continuity used by WP Native Builder. It complements [`MASTER-SPEC.md`](../MASTER-SPEC.md) and [`architecture.md`](architecture.md).

It is not a chat archive, session log, release history, or second CMS.

## 1. Goals

Persistent Workspace support lets a later ChatGPT conversation continue a connected WordPress site project without old chat history while keeping context small and live WordPress authoritative for current site state.

It must:

- preserve one stable project-level foundation when the project requires it;
- retain only future-useful project context;
- recover progressively instead of loading all stored material;
- keep small one-off work lightweight;
- distinguish durable intent, current execution state, and live WordPress truth;
- protect Workspace writes with optimistic concurrency independent of WordPress Revisions;
- support design/build/review/publish/maintenance continuity without becoming a general project-management system;
- degrade gracefully when the connector/Workspace is temporarily or permanently unavailable.

## 2. Layers and ownership

| Layer | Owns |
|---|---|
| **WP Native Builder Skill** | model behavior, intake/readiness rules, retention/recovery, ownership/mechanism selection, approval and review behavior |
| **Project Foundation** | accepted durable project-level purpose, audience, scope, constraints, non-goals, success criteria |
| **Derived Workspace Documents** | specialized durable architecture/design/IA/content-data/decision context |
| **Workspace Tasks** | unresolved execution, dependency/blocker, review, and delivery state |
| **Live WordPress** | current pages/posts/products/media/settings/theme/plugin/templates and other actual site objects/configuration |

The companion `wp-native-builder-bridge` may provide the concrete Workspace storage/API/admin surface. The Skill remains capability-driven and must discover what is actually exposed.

## 3. One Workspace per site

The initial product model remains one persistent Workspace per WordPress site. Multiple Documents and Tasks may exist, but normal recovery foregrounds only current/relevant state.

## 4. Canonical Project Foundation

For project classes requiring Project Foundation, persist exactly one canonical Foundation document when a suitable Workspace document capability exists.

Reuse an existing equivalent project brief/specification instead of creating a competing master document.

Foundation owns only stable project-level truth:

- purpose/outcomes;
- intended audiences/needs;
- scope/major deliverables;
- required capabilities/critical interactions;
- material brand/content direction;
- durable technical/language/accessibility/RTL constraints;
- important business/content/SEO/legal/privacy constraints;
- non-goals;
- success/completion criteria;
- material owner decisions.

Foundation is not an active backlog, page mirror, current plugin inventory, implementation log, or live-site snapshot.

After readiness it is not loaded/re-written for every task. Update only for accepted material project-level change, an unresolved material contradiction, or recovery/completion need.

## 5. Derived Documents

Create only documents that reduce future rework or recovery cost.

Common derived documents:

- **Site Architecture Profile** — active theme/editing model, builder ownership, global header/footer/navigation/template ownership, page-content ownership, reusable mechanisms, forms/commerce/data ownership, custom-code placement/prefix;
- **Information Architecture / Sitemap** — when page hierarchy/navigation relationships matter;
- **Design Direction/System** — recurring visual tokens/rules/asset/interaction/responsive/RTL direction;
- **Content/Data Model** — recurring CPT/taxonomy/ACF/product/content relationships;
- **Decision/QA notes** — only when lasting rationale or unresolved material findings need later continuation.

Never mirror live page/product content solely to make Workspace look complete.

## 6. Tasks

Tasks are lightweight execution state for work that benefits from explicit continuation, acceptance, dependencies, review, or delivery.

Useful fields: title, concise goal, acceptance when needed, dependencies/blocker, WordPress target references, short durable notes.

Keep dimensions independent:

| Dimension | Values |
|---|---|
| Progress | `todo` / `in_progress` / `blocked` / `done` |
| Review | `not_required` / `pending` / `changes_requested` / `approved` |
| Delivery | `not_applicable` / `draft_preview` / `live` |

`done` != `approved`; `approved` != `live`; `live` reflects actual intended delivery, preferably verified.

Small changes completed/verified in one interaction should not create permanent tasks merely because Workspace exists.

## 7. Compact resume and progressive loading

On fresh/resumed connected work:

1. discover a suitable Workspace resume capability;
2. request compact orientation before broad rediscovery/questioning;
3. use project identity/current focus, active/review-blocked work, blockers, durable decisions, and references to potentially useful documents;
4. fetch only the task/document details needed for the next decision/action;
5. do **not** automatically load Project Foundation when a nearer current source is sufficient;
6. load Foundation only for project-level intent/change/recovery/completion need;
7. before modifying a current WordPress target, verify live state when it matters;
8. continue the next useful action instead of stopping at a recovery summary.

A resume packet must not dump full Document bodies or all historical/completed tasks by default.

## 8. Source-of-truth reconciliation

- Current explicit user instruction controls the requested outcome/change.
- Project Foundation controls accepted durable project-level intent.
- Derived Workspace docs control their specialized durable domain.
- Tasks control current unresolved execution/review/delivery state.
- Live WordPress controls actual current site objects/configuration.

When Workspace and live state disagree, re-read the live target, preserve newer valid work, reconcile current intent, apply only the still-correct change, and update durable context only if the new fact matters later.

## 9. Retention test

Persist an item only when:

1. a future session materially needs it;
2. a stronger/current source does not already own it;
3. retaining it reduces repeated briefing/ambiguity/rework/lost progress;
4. it is safe to store.

Do not persist full chats, hidden reasoning, routine worklogs, repeated checkpoints, every micro-edit, copied live content, credentials/secrets, unnecessary customer/order/payment/financial payloads, or broad database/plugin dumps.

## 10. Workspace-owned optimistic concurrency

Workspace current state/write safety must not depend on WordPress Revision IDs.

Each overwrite-sensitive Document/Task should expose Workspace-owned identity such as `version` + `state_hash`.

For updates:

1. read current object + identity;
2. require update to accept expected identity;
3. if no guard exists, do not blind-overwrite;
4. submit with expected identity;
5. verify resulting state when practical;
6. on stale/mismatch/conflict, re-read and reconcile newer valid work before retry;
7. on ambiguous write outcome, re-read authoritative current state before any retry.

Workspace resume/current state/stale-write protection must continue when WordPress Revisions are disabled/limited/pruned.

## 11. Logical capability roles

| Role | Expected behavior |
|---|---|
| `workspace-resume` | compact active orientation without full Workspace dump |
| `workspace-document` | list/get/create/update/archive durable Markdown-oriented Documents |
| `workspace-task` | list/get/create/update/transition/archive lightweight Tasks |

These are logical roles, not tool names to invent. Use only current runtime capabilities whose schema/permissions safely match the operation.

## 12. Transient capability loss

A single timeout/unavailable/transport failure is not evidence that a logical Workspace capability no longer exists.

- Preserve recovered orientation/current state.
- Continue independent work.
- Re-discover/retry once when transient semantics or changed runtime evidence make recovery plausible.
- Never blind-loop identical failures.
- If the route remains unavailable, continue manual/non-overwrite work and report a capability blocker only when required semantics truly prevent further outcome-linked progress.

A clear permission denial, unsupported schema, or absent required semantic after authoritative discovery is different from a transient transport failure and should not be disguised by repeated retries.

## 13. Continuity reconciliation

After a material multi-step workflow step, ask internally whether a fresh chat could continue correctly without the current conversation.

If not, update the smallest authoritative Workspace object that owns the changed future-useful truth:

- project-level scope/constraint/success change -> Project Foundation;
- header/footer/global architecture ownership -> Site Architecture Profile;
- recurring accepted design direction -> Design Document;
- active implementation/review/delivery/blocker -> Task;
- unresolved material QA finding -> QA Document/Task as appropriate.

Do not create a session log.

## 14. Visual review and delivery

For material visual work when preview exists:

1. build draft/preview;
2. AI self-review and fix clear visual/technical defects, including Gutenberg invalid/recovery warnings when applicable;
3. surface to user when human review is part of workflow;
4. requested changes -> revise/preview;
5. clear approval of current reviewed result -> review=`approved`;
6. publish only when the applicable approval rule authorizes it;
7. delivery=`live` only after intended live result is established/verified.

## 15. Complete-site launch

For complete/launch-ready projects, individual task completion alone is not overall completion. Synthesize only applicable launch concerns: navigation/content completeness, responsive/RTL, accessibility of key flows, forms/interactions, links/media, material performance effects introduced by the build, important indexing-facing presentation/configuration, intended publication, and live verification.

External business operations, refunds, payments, fulfillment, and destructive customer/order work remain outside ordinary site-building launch QA unless separately requested.

## 16. Manual fallback

Persistent Workspace is an enhancement, not a prerequisite. Without it, the Skill still performs exact stack-aware WordPress work and uses user-supplied durable project artifacts when available.

Manual mode must never claim connected persistence or mutation occurred when no suitable capability exists.

## 17. Validation invariants

A release-quality implementation should demonstrate:

- one canonical Foundation for foundation-required projects;
- staged novice-friendly intake until material readiness coverage is complete;
- no Foundation ceremony for bounded fast-path edits;
- nearest-source resume without automatic full Foundation load;
- selective Document/Task fetch;
- continuity reconciliation of future-useful state;
- guarded Workspace writes using current Workspace-owned identity;
- stale/ambiguous write reconciliation;
- bounded transient-route recovery without blind retry loops;
- manual fallback without false persistence claims;
- no chat/secret/live-content duplication introduced by Workspace behavior.
