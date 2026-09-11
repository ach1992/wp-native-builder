# WP Native Builder — Project Workspace Architecture

This document defines the stable detailed architecture for lightweight WordPress-hosted project continuity used by WP Native Builder. It complements [`MASTER-SPEC.md`](../MASTER-SPEC.md) and the concise [`docs/architecture.md`](architecture.md).

It is not a session log, release history, or manager checkpoint. Git/GitHub own implementation history; this document owns the durable Workspace behavior and boundaries.

## 1. Goals

Persistent Workspace support lets a later ChatGPT conversation continue a connected WordPress site project without requiring the previous chat, while keeping context small and preserving live WordPress as the authority for actual site state.

The architecture must:

- retain only future-useful project context;
- recover progressively rather than loading all stored material;
- keep small one-off work lightweight;
- distinguish project intent from current live WordPress truth;
- protect Workspace writes with optimistic concurrency independent of WordPress Revisions;
- support multi-step design/build/review/publish/maintenance work without becoming a general project-management system;
- preserve strong manual behavior when Workspace capabilities are unavailable.

## 2. System boundaries

There are three distinct layers:

| Layer | Owns |
|---|---|
| **WP Native Builder Skill** | Model behavior, retention/recovery rules, task/document semantics, source-of-truth policy, mechanism selection, approval behavior |
| **Persistent Workspace** | Durable project intent, accepted decisions, unresolved progress, lightweight documents/tasks and useful references |
| **Live WordPress** | Current pages/posts/products/media/settings/theme/plugin state and other actual site objects/configuration |

The companion `wp-native-builder-bridge` owns the concrete WordPress storage, permissions, Ability implementation, and admin UI for its Workspace surface. The maintained Bridge provides this accepted contract for the supported direct connected setup. The Skill remains capability-driven and must still discover what the current runtime actually exposes.

A connector, MCP transport, or Bridge namespace is an execution transport. It does not replace WordPress architecture ownership.

## 3. One Workspace per site

The initial product model is one persistent Workspace per WordPress site. The Workspace is a site-project continuity layer, not a second CMS.

It may contain multiple durable documents and tasks, but normal recovery should foreground only current/relevant state.

## 4. Documents

Workspace Documents are Markdown-oriented durable project artifacts. Create one only when future continuation materially benefits.

Useful examples include:

- concise project brief;
- durable site/stack profile when not cheaply discoverable each time;
- sitemap/information architecture decision;
- approved design-system or visual-direction notes;
- content/data model decisions;
- lasting implementation/architecture decisions;
- unresolved QA findings that need later continuation.

Do not create all document types by default. A project may need only one or two.

Documents must not become mirrors of live page/post/product content when WordPress already owns that truth.

## 5. Tasks

Workspace Tasks are lightweight execution-oriented state for work that benefits from explicit continuation, dependencies, review, or delivery state.

Useful fields are intentionally small:

- title;
- concise goal;
- acceptance criteria when completion would otherwise be ambiguous;
- dependencies/blocker when real;
- target references to relevant WordPress objects/surfaces;
- concise durable notes;
- progress, review, and delivery dimensions.

Keep these dimensions independent:

| Dimension | Values | Meaning |
|---|---|---|
| Progress | `todo` / `in_progress` / `blocked` / `done` | Implementation progress |
| Review | `not_required` / `pending` / `changes_requested` / `approved` | Human/visual review state |
| Delivery | `not_applicable` / `draft_preview` / `live` | Where the intended result actually exists |

`done` does not imply `approved`. `approved` does not imply `live`. `live` should reflect actual publication/delivery, preferably after verification.

Small changes completed and verified in the current interaction should not create a permanent task merely because Workspace exists.

## 6. Compact resume and progressive loading

On a fresh or resumed connected project:

1. Discover a suitable Workspace resume capability that actually exists.
2. Request a compact orientation packet before broad project/site rediscovery.
3. Use only decision-relevant orientation: site/project identity, current focus, active or review-blocked work, blockers, and a small index/reference to potentially useful documents.
4. Fetch only the task/document details needed for the current decision or next action.
5. Reuse settled durable context instead of asking the user to repeat it unless current instruction/evidence materially conflicts.
6. Before modifying an existing WordPress target, verify its current live state when that state matters.
7. Continue the next useful project action instead of stopping after a recovery summary.

A resume packet must not dump full document bodies or a historical list of every completed task into model context by default.

## 7. Retention test

Persist an item only when all applicable conditions make retention worthwhile:

1. a future session materially needs it to decide or continue correctly;
2. it is not better recovered from a stronger/current source such as live WordPress;
3. retaining it reduces repeated briefing, ambiguity, rework, or lost progress;
4. the information is safe and appropriate to store.

Do not persist:

- full chat transcripts;
- hidden reasoning or chain-of-thought;
- routine worklogs or repeated session checkpoints;
- every micro-edit;
- copied live content solely to mirror WordPress;
- credentials, application passwords, tokens, auth headers, salts, private keys, or secrets;
- unnecessary customer/order/payment/financial payloads;
- broad plugin/database dumps unrelated to a durable project decision.

Archive completed temporary/test/project items when keeping them active would clutter normal resume state.

## 8. Source-of-truth model

Use different sources for different questions:

- **Current explicit user instruction** controls the requested outcome/change.
- **Workspace** controls retained project intent, accepted decisions, unresolved progress, and useful project references.
- **Live WordPress** controls what content/configuration/objects actually exist now.

Workspace must never be used as proof that a live target has not changed.

If Workspace and live state disagree:

1. re-read the live target;
2. determine whether the live change is newer/valid or whether current user instruction supersedes retained intent;
3. preserve newer valid work;
4. apply only the still-correct intended change;
5. update durable Workspace context only if the new fact will matter later.

## 9. Workspace-owned optimistic concurrency

Workspace current state and write safety must not depend on WordPress Revision IDs.

Each overwrite-sensitive Document/Task operation should expose a Workspace-owned current-state identity, such as:

- `version` — monotonically changing logical version;
- `state_hash` — digest representing current Workspace object state.

For an overwrite-sensitive update:

1. read the current Workspace object and capture its current Workspace-owned identity;
2. require the update operation to accept that expected identity;
3. if the capability cannot expose/accept a suitable guard, do not perform a blind overwrite;
4. submit the intended update with the expected identity;
5. if accepted, verify resulting state when practical;
6. if stale/mismatched/conflicted, do not overwrite—re-read current primary state, reconcile newer valid work, then retry only if still correct;
7. if the write outcome is ambiguous, re-read authoritative current state before any retry.

A transport-level error after submission is not proof that the mutation failed. Re-reading current state prevents duplicate or contradictory retries.

## 10. Revision independence

`workspace-resume`, Workspace current state, and stale-write protection must remain functional when WordPress Revisions are disabled, limited, cleaned, or pruned.

WordPress Revisions may remain useful for ordinary Posts/Pages/live content and may be available as optional secondary history, but they are not the Workspace current-state or concurrency dependency.

If the Bridge maintains private Workspace history/snapshots for its own admin UX or recovery, that is an implementation detail. The Skill should use only behavior actually exposed by the runtime rather than assuming hidden storage internals.

Site/database disaster recovery remains the normal WordPress hosting/backup boundary; Workspace does not replace backups.

## 11. Logical capability roles

The initial logical roles are:

| Role | Expected behavior |
|---|---|
| `workspace-resume` | Return compact active orientation without full Workspace dump |
| `workspace-document` | List/get/create/update/archive durable Markdown-oriented documents |
| `workspace-task` | List/get/create/update/transition/archive lightweight tasks |

These are logical role names from the Skill contract. The model must discover the current runtime and use only actual exposed capabilities whose documented schema/permissions safely match the required operation.

If suitable Workspace capabilities are absent, continue in manual mode. Do not fabricate persistence or make the Bridge a prerequisite for useful WordPress work.

## 12. Project progression

For genuinely multi-step site work, use a proportional loop:

```text
RESUME / DISCOVER
  -> UNDERSTAND
  -> PLAN ENOUGH TO ACT
  -> BUILD
  -> VERIFY
  -> REVIEW WHEN MATERIAL
  -> REVISE / APPROVE
  -> PUBLISH WHEN AUTHORIZED
  -> VERIFY LIVE
  -> UPDATE FUTURE-USEFUL WORKSPACE STATE
  -> NEXT USEFUL WORK
```

This is a control model, not mandatory ceremony. Skip irrelevant phases and do not create project documents/tasks merely to satisfy the diagram.

## 13. Visual review and approval

For material visual work where preview/rendering is available:

1. build a draft/preview;
2. inspect the actual result and correct obvious visual/technical defects;
3. when user review is part of the requested workflow, surface the current preview and keep review state distinct from progress/delivery;
4. requested changes -> revise and preview again;
5. clear approval of the current reviewed result -> review can become approved;
6. publish only when the applicable approval rule authorizes the exact action;
7. mark delivery `live` only after the intended live result is established/verified.

If the user established “show me first and publish after I approve,” clear approval of that current preview satisfies the condition while target/scope/material effect remain unchanged. Do not ask for duplicate confirmation.

Generic positive feedback does not silently authorize unrelated publication when no such condition or exact publish instruction exists.

## 14. Complete-site launch behavior

For a complete/launch-ready site, individual page/task completion is not enough by itself. Synthesize only launch concerns that materially apply to the actual site and requested scope, such as:

- navigation/content completeness;
- responsive and RTL/LTR behavior;
- accessibility of key flows;
- forms/interactions;
- broken/missing links or media;
- material performance effects introduced by the build;
- important site-building/indexing-facing presentation/configuration;
- intended publication and live verification.

Do not impose a fixed giant checklist. External business operations, fulfillment, refunds, payments, and destructive order/customer operations are outside ordinary site-building launch QA unless separately requested.

After verified launch, keep normal resume state focused on still-relevant durable context and unresolved/relevant work rather than completed-session history.

## 15. Maintenance behavior

Later maintenance should reuse durable approved architecture/design decisions without reopening settled intake questions. Re-read live WordPress state when modifying a current target.

A current explicit redesign, rebrand, architecture change, or new requirement can supersede stored conventions. Update retained context when the new direction becomes durable.

## 16. Security and privacy boundaries

- Workspace abilities must remain permission/capability checked by their concrete runtime.
- Workspace objects should remain private/internal rather than public content surfaces.
- Generic page/post/content/block operations must not accidentally treat Workspace Documents/Tasks as ordinary live content.
- Do not store secrets or unnecessary sensitive operational/customer data in Workspace.
- Do not infer destructive or financial operations from ordinary site-building work.
- Preserve explicit user approval semantics independently from technical capability/permission.

## 17. Manual fallback

Persistent Workspace is an enhancement, not a core dependency. Without it, the Skill still uses the current conversation and supplied project artifacts to provide exact stack-aware site-building guidance.

Manual mode must never claim that cross-chat persistence or connected mutation occurred when no suitable capability exists.

## 18. Validation invariants

A release-quality implementation of this architecture should demonstrate, through the smallest useful combination of model evaluation, source validation, and connected runtime evidence:

- compact resume rather than full Workspace loading;
- selective Document/Task fetch;
- guarded Workspace updates using current Workspace-owned identity;
- deterministic stale-write rejection followed by re-read/reconciliation behavior;
- ambiguous write outcome handling by authoritative re-read before retry;
- revision-independent Workspace current state/concurrency;
- preservation of normal live WordPress object/revision handling where applicable;
- active resume state that does not remain cluttered with archived/completed disposable fixtures;
- manual fallback without false persistence claims;
- no secret/hidden-reasoning/live-content duplication introduced by Workspace behavior.

Implementation/release history belongs in GitHub, not in this document.
