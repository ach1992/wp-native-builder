# WP Native Builder — Persistent Workspace and Site Project Lifecycle

Status: Accepted architecture; Skill-side runtime integrated; connected Bridge implementation/E2E tracked separately
Repository: `ach1992/wp-native-builder`
Companion: `ach1992/wp-native-builder-bridge`
Parent program: https://github.com/ach1992/wp-native-builder/issues/13

## 1. Purpose

This document defines how WP Native Builder should retain enough durable project context to continue a WordPress site project across chats and how it should progress a site from discovery through design, implementation, review, approval, publication, and later maintenance without becoming a heavyweight project-management system.

The design is intentionally lightweight. The Skill remains primarily a WordPress site-building and design assistant. Persistent project memory, documents, and tasks exist only to reduce repeated briefing, preserve important decisions, support safe recovery, and help the model continue the user's requested site outcome.

This document owns the detailed Skill-side architecture for Workspace continuity and project lifecycle. `MASTER-SPEC.md` remains authoritative for project-level product intent and durable constraints. Live implementation status remains in GitHub Issues/PRs and the current repository source.

## 2. Core principles

1. **Live WordPress is the source of truth for the live site.** Workspace memory may describe intent, decisions, progress, and object references, but it never proves the current content/configuration of a WordPress object.
2. **Workspace is durable project context, not a chat archive.** Persist only information a future chat materially needs to continue correctly.
3. **Recovery is progressive.** A fresh chat should begin from a compact orientation/resume packet and load only decision-relevant documents/tasks afterward.
4. **Planning is proportional.** Create documentation and tasks only when they materially improve execution, continuity, review, or completion. Do not turn small edits into project ceremonies.
5. **Design remains central.** For substantial visual work, the normal path should support preview, AI self-review, user visual review, revisions, approval, and then live publication when appropriate.
6. **Task progress, review, and delivery are separate facts.** A task can be implementation-complete while still waiting for user review or publication.
7. **User instructions remain highest-priority project direction.** Stored Workspace conventions do not override an explicit current redesign, scope change, or other clear user instruction.
8. **No false persistence.** If the connected Workspace capability is absent, the Skill must remain useful but must not imply that cross-chat state has been saved.
9. **No unnecessary infrastructure.** The initial architecture requires no vector database, embeddings service, external project database, or hosted memory service.
10. **Companion responsibilities stay separated.** This repository defines Skill behavior and the expected Workspace contract; the companion Bridge owns WordPress storage, abilities, isolation, permissions, and admin UI implementation.
11. **Workspace correctness is revision-independent.** Current Workspace state, fresh-chat recovery, and stale-write protection must not depend on WordPress Revisions; Workspace Documents/Tasks use a Workspace-owned current-state identity such as `version + state_hash`.

## 3. Site-project operating loop

For a substantial or multi-step site project, use the following conceptual loop when relevant:

```text
RESUME / DISCOVER
        ↓
UNDERSTAND REQUEST
        ↓
PLAN ENOUGH TO ACT
        ↓
CREATE / UPDATE ONLY USEFUL TASKS OR DOCS
        ↓
BUILD / MODIFY
        ↓
SELF-VERIFY
        ↓
USER VISUAL REVIEW WHEN MATERIAL
        ↓
REVISE OR APPROVE
        ↓
PUBLISH WHEN AUTHORIZED
        ↓
VERIFY LIVE RESULT
        ↓
UPDATE WORKSPACE
        ↓
NEXT USEFUL TASK
```

This is a decision loop, not a mandatory state machine. Skip phases that do not apply. A request such as “reduce the footer spacing” should not trigger project planning, document creation, or a persistent task when it can be safely completed and verified immediately.

For a broad request such as “build the complete website for this company,” the Skill should discover the actual WordPress stack, ask only material missing business/content/design questions, create the minimum useful durable project context, derive sensible work, and begin implementation rather than remaining in planning mode.

## 4. Persistent Workspace concept

The initial product model is **one persistent Workspace per WordPress site**.

When the companion Bridge exposes the accepted Workspace capability, the Workspace is stored in WordPress so a later ChatGPT conversation can recover project context from the site itself. The Skill should not require the previous conversation to be available.

The Workspace contains two logical classes of durable objects:

- **Documents** — Markdown-oriented project context and lasting decisions.
- **Tasks** — lightweight executable/reviewable work items.

The companion Bridge may use private internal WordPress post types or another equally WordPress-native mechanism, but the exact storage implementation is owned by the Bridge project. From the Skill perspective, Workspace objects must be isolated from ordinary site content and available through typed Workspace capabilities rather than generic Posts/Pages editing.

## 5. Retention test

Persist information only when all applicable parts of this test are satisfied:

1. a future chat/model is likely to need the information to decide correctly, continue unresolved work, preserve an accepted design/architecture constraint, understand a blocker, or know what remains;
2. the information is not already better recoverable from a stronger source such as current live WordPress state;
3. retaining it meaningfully reduces future rediscovery or prevents loss of accepted project intent; and
4. storing it is appropriate from a privacy/security perspective.

### Good candidates to persist

Create or update these only when the project actually needs them:

- project brief: purpose, audience, goals, important scope/constraints;
- site profile: architecture and durable project-specific conventions that are not cheaper to rediscover every time;
- sitemap / page-template plan;
- design system or approved visual direction;
- content/data model when CPTs, taxonomies, ACF/fields, products, forms, or other structures make it useful;
- lasting architecture/design/content decisions whose rationale or result matters later;
- unresolved launch/QA findings;
- active tasks, dependencies, blockers, review state, and relevant target references;
- concise durable notes required to continue a non-obvious unfinished task.

### Do not persist by default

- full conversation transcripts;
- hidden model reasoning or chain-of-thought;
- routine step-by-step worklogs;
- repeated session summaries or checkpoint documents;
- every completed micro-edit;
- full copies of page/post/media content already owned by WordPress;
- disposable implementation experimentation;
- information that can be safely and cheaply rediscovered from the live site;
- credentials, application passwords, tokens, auth headers, salts, private keys, or other secrets;
- unnecessary customer/order/payment/financial or similarly sensitive payloads.

Do not create `session-1`, `checkpoint-2`, `handoff-3`, or equivalent ever-growing archives. Update the current useful document/task instead. Workspace correctness does not rely on WordPress Revisions; revisions may remain optional secondary history when available, while any stronger durable Workspace history is owned by the Bridge's bounded private snapshot/version mechanism and retention policy.

## 6. Workspace Documents

Documents should be Markdown-oriented and named by purpose rather than session. Typical examples, only when useful:

| Document | Purpose |
|---|---|
| `project-brief` | business/site purpose, audience, high-level scope, goals, durable constraints |
| `site-profile` | current architecture and project-specific site conventions worth retaining |
| `sitemap` | pages/templates, intent, relationships, important status/coverage notes |
| `design-system` | approved visual direction, colors/tokens when relevant, typography/layout/component conventions |
| `content-model` | durable content/CPT/taxonomy/ACF/product/form relationships when material |
| `decisions` | only lasting accepted decisions that future work must respect |
| `qa` | unresolved launch/review findings that genuinely need continuity |

The list is illustrative, not a required template. Do not create empty documents merely because their names appear here. Prefer a small number of current documents over many fragmented notes.

Workspace documents describe project intent/context. If a document says a page or setting has a certain value but current WordPress says otherwise, the model must reconcile against current WordPress before acting.

## 7. Lightweight Tasks

A persistent Task exists only when it materially improves continuation, coordination, review, dependency handling, or completion visibility.

A useful compact task can contain:

```text
Title / Goal
Progress
Acceptance (only enough to define done)
Dependencies / blocker (when any)
Target references (when useful)
Review state
Delivery state
Concise durable notes (only when future continuation needs them)
```

### Progress

Use a small progress lifecycle:

`todo | in_progress | blocked | done`

### Review

Keep review independent from progress:

`not_required | pending | changes_requested | approved`

### Delivery

Keep live delivery independent from progress/review:

`not_applicable | draft_preview | live`

Examples:

- A homepage implementation may be `progress=done`, `review=pending`, `delivery=draft_preview`.
- After the user approves it, it may be `progress=done`, `review=approved`, `delivery=draft_preview` until publication.
- A small backend-safe correction may require no user visual review and can use `review=not_required`.

Do not create many status dimensions beyond these without evidence that the site-building workflow genuinely needs them.

### Acceptance criteria

Use concise observable acceptance only where it prevents ambiguity. Example:

```text
Homepage includes approved hero, services, and primary CTA;
responsive behavior is intentional on mobile;
result follows the approved design direction;
preview is ready for owner review.
```

Do not turn every task into a software-engineering contract.

### Target references

When helpful for safe resume, a task may point to live WordPress objects/surfaces such as:

- Page/Post/CPT object ID;
- template/template part/pattern;
- navigation/menu;
- form;
- product/category/archive surface;
- relevant theme/plugin-owned surface.

A target reference accelerates discovery; it never removes the requirement to read current live state when that state affects the next write.

## 8. Recovery and fresh-chat resume

When connected Workspace capabilities exist and the user is continuing work on the same site, the preferred recovery flow is:

```text
1. workspace-resume
2. establish project identity, current stage/focus, active tasks, blockers/review needs,
   and the index of potentially relevant documents
3. fetch only the task/document(s) needed for the current decision
4. inspect the current live WordPress target/state when it matters
5. reconcile any stale contradiction
6. continue the next useful action
```

A good resume packet is compact. It should orient the model, not restore the entire project into the prompt.

Illustrative shape:

```text
Project: Example Company Site
Current focus: Homepage
Open work:
- T12 Homepage — in_progress — review pending
- T15 Services — todo
Blocked: none
Relevant docs: project-brief, design-system, sitemap
Recent durable decision: homepage hero direction approved
```

The model then reads only what it needs, for example `T12` and `design-system`, rather than every document and completed task.

`workspace-resume` must derive from current primary Workspace object state and remain functional when WordPress Revisions are disabled, limited, or pruned.

### New project / empty Workspace

If no durable Workspace exists, do not manufacture a large project structure immediately. Discover the site/request and create only the first useful documents/tasks once enough intent is known.

### Manual mode / no Workspace capability

Manual mode remains fully supported. The Skill can use conversation context and supplied project documents, but it must not claim that state was persisted into WordPress. If continuity is important and no persistent connection exists, it may provide or update a concise portable project checkpoint only when the user asks or when such an artifact is otherwise genuinely useful.

## 9. Source-of-truth and reconciliation

Use this hierarchy for project continuation:

```text
Current explicit user instruction
        ↓
Durable project intent / accepted decisions in Workspace
        ↓
Current live WordPress state for what actually exists
```

This is not a simple overwrite precedence: Workspace owns intent/context; live WordPress owns current site reality.

Examples:

- Workspace: “Homepage hero complete.” Human later edits the page manually. The model re-reads the page before further mutation and reconciles the task/document if necessary.
- Workspace target points to Page 42 but Page 42 was replaced/deleted. Re-discover the correct target before updating memory or content.
- Stored design system says “preserve current dark navy palette,” but the user explicitly requests a full rebrand. The current explicit request wins; update the durable design context after the new direction is accepted.

Never use stale Workspace state to authorize blind replacement of newer live content.

## 10. Concurrency and stale writes

Multiple chats or humans may work on the same site. Keep Workspace-object concurrency distinct from ordinary live WordPress content history.

For a Workspace Document/Task, the current state lives in the primary Workspace object and overwrite protection must use a Workspace-owned identity independent of WordPress Revision IDs. A suitable contract can expose a monotonic `version` plus deterministic `state_hash`, or an equivalently strong typed identity. The exact representation is Bridge-owned; the Skill must use only the identity actually exposed by the current runtime.

Expected Workspace behavior:

1. read the current Workspace Document/Task and its current identity before an overwrite-sensitive change;
2. submit the expected Workspace identity with the change when supported;
3. if the identity is stale/conflicted, do not overwrite;
4. re-read current primary Workspace state;
5. reconcile the intended update with newer valid work;
6. retry only after the conflict is understood.

This flow must continue to work when WordPress Revisions are disabled, limited, or removed by cleanup tooling. WordPress Revisions may be retained as optional secondary history, but they are not authority for current Workspace state, fresh-chat recovery, or stale-write detection.

For ordinary live WordPress content such as Posts/Pages, use the current object/revision/version identity appropriate to the actual WordPress mechanism; this Workspace rule does not remove the usefulness of normal WordPress revisions for live-content history/rollback.

The Skill must not invent a successful state when a Workspace write outcome is ambiguous. Re-read before any retry that could duplicate or destroy newer information.

## 11. Visual review and user approval

Substantial visual work benefits from a deliberate review loop. When preview/rendering capability is available and the workflow calls for review:

```text
BUILD
  ↓
PREVIEW / RENDER
  ↓
AI VISUAL + TECHNICAL SELF-REVIEW
  ↓
USER SEES RESULT
  ↓
changes requested? ─ yes → revise → preview again
  ↓ no / approved
PUBLISH WHEN THE APPLICABLE APPROVAL CONDITION IS SATISFIED
  ↓
VERIFY LIVE RESULT
```

The AI self-review should focus on applicable visual hierarchy, spacing/layout, typography, content hierarchy, responsive behavior, RTL/LTR, accessibility, performance-affecting choices, and fit with the approved site direction. Do not turn this into a repeated giant checklist in user-facing messages.

### When user visual review is normally important

Prefer user review before publication for material visual changes such as:

- a new homepage/landing page or large redesign;
- a major template/archive/product/store presentation change;
- a materially new design direction;
- site-wide header/footer/global visual changes where the user asked to review before going live.

Do not force a preview/approval ritual for every tiny reversible adjustment if the user has already clearly authorized the exact live change.

### Approval semantics

Bridge permission/capability is not user approval.

A current explicit instruction can satisfy the relevant approval requirement when it clearly authorizes the exact consequential action/target. Do not request duplicate confirmation.

If the user established a condition such as “show me the design first and publish it after I approve,” then an unambiguous approval of that shown/current preview (for example “approved” or a clearly equivalent response) can satisfy that condition when the target/scope/effect have not materially changed. Do not ask “are you sure?” again solely because publication is next.

Conversely, generic positive feedback such as “looks better” must not be silently interpreted as publication authorization when no prior publish-after-approval condition or exact publish instruction makes that meaning clear.

## 12. Launch and completion

A site project is not automatically complete merely because all page-building tasks are marked `done`.

When the user asked for a complete site, the Skill should synthesize only the remaining launch-relevant checks/tasks that materially apply, for example:

- required pages/templates/navigation/content present;
- key visual surfaces reviewed;
- responsive and RTL/LTR behavior appropriate;
- accessibility issues that materially affect the delivered site addressed;
- forms and critical interactions verified;
- important broken/missing links/assets resolved;
- performance-impacting implementation problems addressed where material;
- relevant site-building SEO/indexing-facing configuration checked when it belongs to the requested site scope;
- live publication/verification completed for the requested delivery target.

Do not create a universal launch checklist by ritual. Adapt to the site and accepted scope.

After launch, keep the active Workspace compact. Completed historical tasks should not dominate normal resume results. They may remain recoverable through current Workspace objects and bounded Bridge-managed history when useful; WordPress Revisions, if present, are optional secondary history rather than a continuity dependency. Preserve durable approved project context and unresolved work so future maintenance can resume cleanly.

## 13. Security and privacy boundaries

Workspace persistence must never become a secret store or a way around existing WordPress/Bridge permissions.

Do not persist:

- passwords, application passwords, API tokens, auth headers, salts, private keys;
- hidden chain-of-thought/internal reasoning;
- unnecessary personal/customer/order/payment/financial payloads;
- arbitrary sensitive plugin/database dumps.

If a future task legitimately requires sensitive operational data, use the specific supported live capability and applicable permissions rather than copying the data into general project memory.

The Skill's existing restrictions around consequential WooCommerce/customer/order/payment actions remain unchanged. Workspace tasks may describe that such work is blocked/out of ordinary builder scope, but they do not grant authority to execute it.

## 14. Expected companion Bridge contract

The companion Bridge project owns implementation, but the Skill is designed around a small typed Workspace surface rather than arbitrary database access.

### Minimum logical capabilities

Names may be reconciled by the Bridge project, but the initial logical surface should remain small:

| Capability | Purpose |
|---|---|
| `workspace-resume` | compact orientation: project identity/focus, active/review-blocked tasks, blockers, recent durable decision/context, relevant document index |
| `workspace-document` | list/get/create/update/archive durable Markdown-oriented Workspace documents |
| `workspace-task` | list/get/create/update/transition lightweight tasks and their progress/review/delivery metadata |

Do not create dozens of tiny tools merely for field-level operations if a typed action contract is clearer and safer.

### Storage/isolation expectations

The Bridge should provide WordPress-native persistence isolated from ordinary site content. The accepted initial direction is internal/private Workspace objects, potentially private custom post types such as logical `wpnb_doc` and `wpnb_task`, provided the Bridge implementation keeps them out of normal public content surfaces.

Workspace objects must not be accessible as ordinary public Posts/Pages/CPT content and must not accidentally become targets of generic Builder content/Gutenberg abilities. They require an explicit Workspace access path.

Expected properties:

- no public front-end permalink/query/search/feed exposure;
- no accidental inclusion in normal content/navigation editing;
- capability/permission checks consistent with the Bridge security model;
- current state stored in each primary Workspace Document/Task object rather than reconstructed from WordPress Revisions;
- a Bridge-owned overwrite identity independent of WordPress Revision IDs, such as `version + state_hash`, exposed strongly enough for optimistic concurrency;
- `workspace-resume`, current Workspace state, and stale-write rejection remain functional with WordPress Revisions disabled or pruned;
- WordPress Revisions, if retained, are optional secondary history only;
- if durable history/rollback must survive revision-cleaner plugins, bounded Bridge-managed private snapshot/version records may be used, must not be ordinary `post_type=revision` records, and must have explicit retention;
- Markdown-oriented document content plus structured task metadata;
- deactivation does not silently destroy project memory;
- uninstall deletion is explicit/opt-in rather than surprising;
- export and explicit clear/delete controls are available to the administrator;
- deletion of the Workspace/database itself, host rollback, or similar disaster recovery remains outside software-level continuity guarantees and relies on normal site/database backups.

### Admin UX expectation

The companion plugin should eventually expose a recognizable top-level WordPress admin menu rather than mixing the Workspace into ordinary Posts/Pages or leaving the whole product under generic Settings:

```text
WP Native Builder
├── Dashboard
├── Documents
├── Tasks
├── Activity
└── Settings
```

Initial human Workspace management can prioritize **View + Export + Clear**. Full manual document/task editing is not required until real usage justifies it.

- **Dashboard:** project/Workspace summary, current focus, tasks needing attention/review, connection status, last meaningful Workspace update.
- **Documents:** inspect durable Workspace documents.
- **Tasks:** inspect/filter active, review-needed, blocked, and completed tasks.
- **Activity:** bounded Bridge action/audit troubleshooting view; Activity is not Workspace memory.
- **Settings:** connection/access groups and Workspace retention/export/clear settings.

This repository does not implement that UI. The Bridge Master must reconcile these expectations into the companion repository's canonical specification and backlog before implementation.

## 15. Context-efficiency requirements

Persistent memory is successful only if it reduces context cost instead of moving a giant chat transcript into WordPress.

The Skill should:

- request a compact resume packet first;
- fetch specific documents/tasks only when needed;
- prefer current concise truth over historical snapshots;
- keep completed work out of normal active orientation;
- avoid restating live WordPress content in Workspace documents;
- summarize only durable decisions/constraints that future work needs;
- keep runtime references shallow and load Workspace/project guidance conditionally.

The implementation should add detailed guidance through shallow Skill references, not by turning `SKILL.md` into a large orchestrator.

Current integrated Skill reference shape:

```text
references/
├── design-conventions.md
├── implementation-decisions.md
├── project-workflow.md
└── workspace-memory.md
```

Evidence-first scoping and Ask / Infer / Defer live directly in `SKILL.md`; no separate `site-profile.md` runtime hop is required. Workspace/project references are integrated in current source, while connected Workspace execution remains dependent on the companion Bridge exposing the accepted capabilities.

## 16. Manual versus connected capability

### Connected

When Workspace abilities are available:

- resume from Workspace before asking the user to repeat established context;
- verify relevant live state before mutation;
- update durable task/document state as useful work progresses;
- leave a recoverable project state before a cross-chat handoff naturally occurs;
- use only capabilities actually exposed by the current runtime.

### Manual

Without Workspace abilities:

- continue normal stack-aware design/build/review guidance;
- use the current conversation and any supplied project artifacts;
- do not claim persistent recovery;
- do not require the Bridge merely to answer or produce implementation guidance.

The absence of Workspace persistence must degrade continuity, not the core usefulness of the Skill.

## 17. Evaluation requirements

Implementation must be tested against at least these scenarios:

1. Fresh chat resumes a connected project with no prior conversation available.
2. Workspace contains many documents/tasks; resume remains compact and loads only relevant items.
3. Broad new-site request generates only useful initial docs/tasks and begins work without planning paralysis.
4. Small one-off visual/content modification completes without unnecessary persistent task/document creation.
5. Workspace notes conflict with live WordPress state; live state is re-read and reconciled.
6. Concurrent/stale Workspace write does not overwrite newer valid state, including when WordPress Revisions are disabled, limited, or pruned.
7. Substantial design follows preview -> AI self-review -> user review -> revision/approval -> publish -> live verification when appropriate.
8. Prior “publish after my approval” instruction plus clear approval of the current preview does not trigger duplicate confirmation.
9. Generic positive feedback does not imply unrelated publish authorization.
10. Existing settled design context is reused on later iterations without repetitive intake.
11. Explicit redesign overrides stored prior design conventions.
12. Preferred stack, block-theme, page-builder, WooCommerce/ACF, and other existing-stack cases preserve stack-adaptive behavior.
13. Workspace never stores secrets/hidden reasoning and does not broaden sensitive commerce operations.
14. Manual mode remains useful with no Workspace capability and makes no false persistence claim.
15. Complete-site flow performs proportional launch verification rather than declaring success solely from page-task completion.
16. Added Skill guidance remains compact/progressively loaded and does not recreate `github-project-orchestrator` inside the WordPress Skill.
17. WordPress Revisions remain available for ordinary live-content history/rollback where appropriate; Workspace revision independence does not cause the Skill to discard normal Posts/Pages revision behavior.

## 18. Non-goals

- Recreating GitHub Issues/Projects/PR/Worker orchestration inside WordPress.
- Turning WP Native Builder into a general software engineering project manager.
- Treating every user request as a persistent project task.
- Creating a full conversation/session archive.
- Storing hidden reasoning/chain-of-thought.
- Using Workspace as a duplicate CMS or as authority over current live WordPress state.
- Building a vector-memory/RAG platform for the first implementation.
- Requiring a hosted persistence service or external database.
- Forcing user visual approval for every tiny reversible change.
- Letting stored design conventions override a clear current user request.
- Expanding ordinary site building into sensitive business, payment, order, customer, or destructive operations.

## 19. Repository ownership and cross-project handoff

This repository owns:

- Skill behavior and decision rules;
- project/recovery/visual-review semantics;
- the logical Workspace capability requirements expected by the Skill;
- Skill-side evaluation and packaging.

The companion `wp-native-builder-bridge` repository owns:

- WordPress storage model;
- Workspace Ability registration/contracts;
- permission/capability enforcement;
- Workspace admin UI;
- data lifecycle/uninstall behavior;
- concrete stale-write/version implementation;
- connected end-to-end infrastructure.

Do not implement Bridge changes in this repository. When the companion project is updated, its Master must read the current version of this document and independently reconcile it with the Bridge's own current `MASTER-SPEC.md`, Issues, code, and concurrent work rather than copying stale chat assumptions.
