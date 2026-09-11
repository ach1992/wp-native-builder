# WP Native Builder — Project Workspace Architecture

This document defines the persistent Workspace architecture used by WP Native Builder. Product requirements live in [`MASTER-SPEC.md`](../MASTER-SPEC.md); runtime rule ownership lives in [`architecture.md`](architecture.md).

Workspace is an optional persistence layer for project continuity. It is not a chat archive, second CMS, live-site mirror, or general project-management system.

## 1. Goals

Persistent Workspace support must let a fresh connected chat continue useful WordPress work without old conversation history while keeping context small and live WordPress authoritative for current site state.

It must:

- preserve only future-useful durable project context;
- support one canonical Project Foundation when the project requires it;
- recover progressively instead of dumping all stored material;
- keep one-off work lightweight;
- prevent duplicate canonical documents where possible;
- keep task execution/review/delivery state independent;
- protect Workspace writes with optimistic concurrency independent of WordPress Revisions;
- degrade gracefully when the Workspace route is temporarily or permanently unavailable.

## 2. Layers and ownership

| Layer | Owns |
|---|---|
| **WP Native Builder Skill** | project semantics, source authority, intake/readiness, mechanism selection, approval and review behavior |
| **Project Foundation** | accepted durable project-level purpose, audience, scope/non-goals, constraints, success criteria |
| **Derived Workspace Documents** | specialized durable architecture/design/IA/content-data context |
| **Workspace Tasks** | unresolved execution, dependency/blocker, review, and delivery state |
| **Live WordPress** | actual current pages/posts/products/media/settings/theme/plugin/templates and other site objects/configuration |

The companion `wp-native-builder-bridge` may implement the storage/API/admin surface. The Skill remains capability-driven and uses only behavior actually exposed by the current runtime.

## 3. Canonical documents

When WP Native Builder creates singleton project documents, the default canonical names are:

- `Project Foundation`
- `Site Architecture Profile`
- `Information Architecture`
- `Design Direction`
- `Content/Data Model`

An existing equivalent document outranks naming preference. Do not create a second copy merely to normalize a title.

### Duplicate-safe creation

Before creating a canonical singleton document:

```text
DISCOVER -> REUSE/UPDATE -> CREATE ONLY IF ABSENT -> VERIFY
```

Search/list enough decision-relevant Workspace state to identify semantic equivalents. If a stable document `key` is supported, use a stable purpose key after confirming an equivalent object does not already exist. Do not assume key uniqueness unless the runtime schema/storage guarantees it. An incomplete/truncated listing is not proof of absence.

## 4. Project Foundation

Foundation content/coverage semantics are owned by `references/project-workflow.md`, not redefined here. Workspace's responsibility is only to persist/retrieve the canonical document safely when a suitable capability exists.

After Foundation readiness it remains discoverable but is not automatically loaded on every resume.

## 5. Tasks

Tasks exist only when work benefits from explicit continuation, acceptance, dependencies, review, or delivery state.

Useful descriptive fields include title, goal, acceptance, dependencies/blocker, target references, and short durable notes.

State dimensions remain Bridge-compatible and independent:

| Dimension | Values |
|---|---|
| Progress | `todo` / `in_progress` / `blocked` / `done` |
| Review | `not_required` / `pending` / `changes_requested` / `approved` |
| Delivery | `not_applicable` / `draft_preview` / `live` |

`done` != `approved`; `approved` != `live`.

`delivery=not_applicable` means no draft/live delivery state is currently established. A task may still be intended for later publication; represent that intent in goal/acceptance/target references/notes. `draft_preview` requires a real preview/draft and `live` requires intended live delivery to be established/verified.

Small changes completed and verified in one interaction do not gain permanent tasks merely because Workspace exists.

## 6. Compact resume and progressive loading

On fresh/resumed connected work:

1. discover a suitable Workspace resume capability;
2. request compact orientation before broad rediscovery/questioning;
3. orient from project identity/current focus, active/review-blocked work, blockers, and references to potentially useful documents;
4. fetch only task/document details needed for the next decision/action;
5. do not automatically load Project Foundation when a nearer source is sufficient;
6. load Foundation only for project-level change/contradiction/recovery/completion need;
7. verify live WordPress state before current-state-dependent/overwrite-sensitive site mutation;
8. continue useful work instead of stopping at a recovery summary.

A resume packet should not dump full document bodies or all completed/history tasks by default.

## 7. Retention

Persist only when all are true:

1. a future session materially benefits;
2. a stronger/current source does not already own the fact;
3. retention reduces repeated briefing, ambiguity, rework, or lost progress;
4. it is safe to store.

Do not persist full chats, hidden reasoning, routine worklogs, repeated checkpoints, every micro-edit, copied live content, credentials/secrets, unnecessary customer/order/payment/financial payloads, or broad database/plugin dumps.

## 8. Workspace-owned optimistic concurrency

Workspace current state/write safety must not depend on WordPress Revision IDs.

For an overwrite-sensitive document/task update:

1. read the current object plus Workspace-owned identity such as `version + state_hash`;
2. require the update operation to accept expected identity;
3. if no guard exists, do not blind-overwrite;
4. submit with expected identity;
5. verify resulting state when practical;
6. on stale/mismatch/conflict, re-read and preserve newer valid work before retry;
7. on ambiguous write outcome, re-read authoritative current state before any retry.

WordPress Revisions may remain useful secondary history for content but are not Workspace concurrency authority. Site/database disaster recovery remains a hosting/backup concern.

## 9. Transient capability loss

One timeout/unavailable/transport failure is not evidence that the logical Workspace capability disappeared.

- preserve recovered orientation/current state;
- continue independent work;
- re-discover/retry once when transient semantics or changed runtime evidence make success plausible;
- never blind-loop identical failures;
- stop retrying after clear permission denial, unsupported schema, or authoritative absence;
- continue manual/non-overwrite work and report a capability blocker only when required semantics truly prevent further outcome-linked progress.

## 10. Continuity reconciliation

After a material multi-step workflow change, update the smallest Workspace object that owns changed future-useful truth when practical. Do not update Workspace merely because another conversational step occurred.

A fresh chat should be able to recover active intent from durable sources without reconstructing project state from old chat history.

## 11. Review and delivery

Static pre-user review applies even without a renderer. When preview/editor/parser/live capabilities exist, add those checks before user handoff/publication as relevant.

Clear approval of a reviewed result may satisfy an already-established “show me first, publish after approval” condition while target/scope/effect remain unchanged. Generic positive feedback alone does not imply publication authorization.

## 12. Manual fallback

Workspace is an enhancement, not a prerequisite. Without a suitable persistence capability, WP Native Builder remains fully useful in manual mode and does not claim connected persistence/mutation occurred.

## 13. Validation invariants

A release-quality implementation demonstrates:

- canonical documents are reused rather than duplicated;
- Foundation semantics remain owned by project workflow rather than duplicated into Workspace policy;
- nearest-source resume without automatic full Foundation load;
- selective task/document fetch;
- guarded Workspace writes using current Workspace-owned identity;
- stale/ambiguous write reconciliation;
- Bridge-compatible task enums without unnecessary new lifecycle states;
- bounded transient-route recovery;
- manual fallback without false persistence claims;
- no chat/secret/live-content duplication introduced by Workspace behavior.
