# WP Native Builder — Product Specification

**Status:** Canonical durable product specification  
**Repository:** `ach1992/wp-native-builder`  
**Companion runtime:** `ach1992/wp-native-builder-bridge`

This file defines the stable product intent and non-negotiable behavior of **WP Native Builder**. It is repository-level product truth for the Skill itself. It is **not** a per-site `Project Foundation`, worklog, backlog, session handoff, release log, or mirror of runtime instructions. Operational detail belongs to `SKILL.md`, its direct runtime references, and the maintained architecture/evaluation docs.

## 1. Product purpose

WP Native Builder is a compact ChatGPT Skill for professional WordPress site planning, design, implementation, review, troubleshooting, and lightweight project continuity.

It must behave like an experienced WordPress designer/developer: understand enough of the real project and current site to avoid predictable rework, resolve the actual owner of a behavior before choosing tooling, prefer the smallest maintainable WordPress-native/public mechanism, verify work before handoff, and preserve only the future-useful context needed for later continuation.

The Skill must remain strong in both modes:

- **Manual:** exact, stack-aware guidance/output without requiring a connector.
- **Connected:** inspect and operate WordPress only through capabilities actually exposed by the current runtime.

The Skill is not a CMS, page builder, connector architecture, or general project-management system.

## 2. Stable product invariants

1. **Proportional process.** Small bounded changes remain fast and do not gain project ceremony merely because Workspace exists.
2. **Foundation before substantial build.** New sites, substantial redesigns, and genuinely multi-step/multi-surface projects establish sufficient project-level intent before material design/build whether or not persistence is available; persistence determines durability, not Foundation readiness.
3. **No intake quota.** Foundation discovery continues in compact staged batches until every material domain is known, explicitly delegated, safely inferred, or not applicable.
4. **Evidence before questions.** Discover decision-relevant live/project facts when possible; ask only unresolved material questions in language the user can answer.
5. **Stack-adaptive, not stack-forcing.** Existing suitable site architecture, editor, theme, builder, plugin, form, commerce, and data ownership outrank preferred defaults.
6. **Mechanism first, transport second.** Decide what should own behavior before choosing which connected Ability/tool can operate it.
7. **WordPress-native/public/supported surfaces first.** Prefer supported Core/theme/builder/plugin/data mechanisms over brittle internals or unnecessary custom markup/code.
8. **Smallest maintainable change.** Preserve unrelated content, configuration, data, visual language, and ownership.
9. **Gutenberg serialization is a contract.** Raw block markup is version/registration-sensitive and receives proportional structural/serialization/editor validation when used.
10. **Advisor, not passive copier.** Clearly weak, outdated, inaccessible, confusing, or predictably unmaintainable UX/UI should be challenged with a better direction unless explicit safe fidelity governs.
11. **Pre-user self-review.** Static review always applies; rendered/editor/parser/live checks are additive when relevant capabilities exist. Never claim evidence that was not actually obtained.
12. **Human-maintainable naming and ownership.** Future maintainers should be able to identify what was created, where it is edited, and why it exists.
13. **Low-friction safety.** Safe reversible reads/edits/drafts/previews/validation proceed without repetitive confirmation; genuine consequential actions still require valid authorization.
14. **Progressive loading.** `SKILL.md` remains a compact control plane and detailed domain rules stay in shallow direct references.
15. **Durable continuity only when persistence exists.** Persistent Workspace or another user-supplied durable project location may provide cross-chat continuity; manual mode must never pretend persistence occurred.
16. **Live state owns live questions.** Stored project context never proves a current WordPress object/configuration is unchanged.
17. **Bounded transient-failure recovery.** One plausible timeout/unavailable transport failure is not enough to declare a logical capability permanently unavailable; blind retry loops are forbidden.
18. **No duplicate truth owners.** One canonical owner should exist for each durable kind of project truth; derived documents specialize rather than mirror each other.

## 3. Request classes and Project Foundation

### 3.1 Fast bounded work

A change that can be understood, implemented, and verified now stays on the fast path. It does not require a Project Foundation, new permanent task, broad site audit, or persistent document by ritual.

### 3.2 Foundation-required work

Use Project Foundation when project-level decisions will materially drive multiple later tasks or continuation, including a new site, substantial redesign/rebrand, multi-page/multi-surface build, or comparable long-lived work.

One visually large page is not automatically a project if current durable context already resolves the material decisions.

### 3.3 Foundation semantics

A project that needs Project Foundation establishes the same logical project-level brief regardless of whether persistence is available. When a suitable durable location exists, keep **one** canonical durable Project Foundation there and reuse an existing equivalent brief/specification rather than creating a competing “master” document. Without a durable location, keep the Foundation coherent in current-session context and never claim automatic cross-chat recovery.

The Foundation owns accepted purpose/outcomes, audience, scope/non-goals, content/primary actions, functional requirements, brand/design constraints, durable technical/quality constraints, governance/delivery expectations, success criteria, and material owner decisions.

It does **not** own worklogs, active task progress, current plugin inventory, copied page content, live-site snapshots, or implementation history. Foundation readiness is determined from coverage of material domains; the product does not require a separate Foundation lifecycle/status enum.

After readiness, Foundation leaves the routine hot path. Reopen it only for accepted material project-level change, unresolved contradiction, or recovery/completion need.

## 4. Canonical project sources

Use these canonical names when a singleton project document is created by the Skill:

- `Project Foundation`
- `Site Architecture Profile`
- `Information Architecture`
- `Design Direction`
- `Content/Data Model`

Equivalent existing project artifacts may retain their established names when they already own the same truth. Canonical names are defaults, not a reason to duplicate documents. Workspace tasks are work items, not singleton canonical documents; title them by purpose/surface/outcome rather than giving every task the same `Workspace Task` name.

Source authority remains separated:

1. current explicit user instruction — requested outcome/change;
2. Project Foundation — accepted durable project-level intent when persisted, or current-session project-level intent when no durable location exists;
3. derived project documents — their specialized durable domain;
4. Workspace tasks — unresolved execution/review/delivery state when persistent Workspace exists;
5. verified live WordPress — current site objects/configuration;
6. Skill defaults — unresolved fallback choices only.

## 5. WordPress ownership and implementation

Every implementation first resolves owner/mechanism, then transport.

Preferred direction is:

```text
current suitable owner/mechanism
  -> WordPress/Core/theme/builder/plugin supported capability
  -> focused maintained capability when a real gap remains
  -> scoped custom HTML/CSS/JS for a presentation-only gap
  -> smallest purpose-built extension when lifecycle/data/API/permissions justify it
```

Global shell/header/footer/navigation/template/reusable surfaces must resolve their actual Site Editor/theme/builder owner before page-local markup is considered. Gutenberg content checks Core blocks/settings/Patterns/template ownership before Custom HTML. Existing CPT/taxonomy/ACF, forms, WooCommerce presentation, and other mature data/function owners are reused when fit.

Preferred defaults for genuinely new/unspecified projects remain fallbacks, not migration targets: WordPress, Astra + Astra Pro, Gutenberg/Block Editor, Gravity Forms, Code Snippets Pro when centralized reusable code is justified, theme-managed fonts, Astra-native global facilities when Astra owns them, Font Awesome 5 Free only when established as available, and post-name permalinks for a new site.

Custom code is placed at the narrowest owner matching its scope/lifecycle. Never edit WordPress Core or third-party plugin/theme files directly.

## 6. Gutenberg, design, and pre-user review

Gutenberg block markup must be treated as a serialization contract. Prefer block-aware/native writes. When raw serialization is unavoidable, preserve delimiter/nesting/current block structure, avoid unrelated reserialization, use current identity for overwrite-sensitive writes, and perform every meaningful available parse/serialize/editor/re-read check before claiming validation.

Material UI work must establish coherent hierarchy and design direction, respect existing visual language unless redesign is explicit, and apply responsive/RTL/accessibility/performance/maintainability judgment proportionally.

Pre-user review has two layers:

- **Static review — always applicable:** content/structure, ownership/mechanism, semantics, obvious accessibility/responsive/RTL/performance/maintainability risks.
- **Runtime/rendered review — capability-dependent:** preview/editor/parser/live checks, invalid-block warnings, visual defects, functional verification, and write-result verification.

Static review never substitutes for rendered evidence, and lack of a renderer/validator never permits a false validation claim.

## 7. Manual, connected, and Workspace behavior

### Manual

Without connected capabilities, provide exact stack-aware implementation guidance/output. Foundation-required work still establishes Foundation context; a user-supplied durable location may provide cross-chat continuity, otherwise persistence is not guaranteed.

### Connected

Connected execution must inspect only decision-relevant current architecture/targets/capabilities, choose mechanism before transport, prefer narrow reversible/draft/preview mutations during iteration, guard overwrite-sensitive writes with current identity when supported, re-read stale/ambiguous state before retry, and verify resulting state when practical.

Capability/permission never proves user approval or successful execution.

### Workspace

Persistent Workspace is optional and capability-driven. Its runtime contract owns persistence/recovery mechanics, not project semantics. Whenever Workspace is relevant to substantial/multi-step work—including starting a new project as well as resuming one—the Skill must load the Workspace-specific procedure and:

- resume progressively rather than dump all history;
- persist only future-useful context;
- discover/reuse/update canonical singleton documents before creating new ones;
- use stable purpose keys when the capability supports them, without assuming key uniqueness unless guaranteed;
- protect overwrite-sensitive Workspace writes with Workspace-owned expected identity such as `version + state_hash`;
- preserve newer valid work on stale/conflict;
- re-read authoritative state after ambiguous write outcomes;
- keep WordPress Revisions separate from Workspace concurrency authority.

## 8. Task-state semantics

Workspace task dimensions remain intentionally small and independent:

| Dimension | Values |
|---|---|
| Progress | `todo` / `in_progress` / `blocked` / `done` |
| Review | `not_required` / `pending` / `changes_requested` / `approved` |
| Delivery | `not_applicable` / `draft_preview` / `live` |

`done` does not imply `approved`; `approved` does not imply `live`.

`delivery=not_applicable` means no draft/live delivery state is currently established. A task may still be intended for later publication; that intent belongs in goal/acceptance/target references/notes. `draft_preview` requires a real draft/preview; `live` requires the intended live result to be established/verified.

Do not add lifecycle states merely to restate intent already owned by task goal/acceptance.

## 9. Approval and safety boundaries

Safe reads, preparation, drafts/previews, validation, and non-consequential reversible edits may proceed within scope. Consequential actions include actual live publication or material shared/global, security/permission, customer/order/financial, data-integrity, destructive, difficult-to-reverse, or comparable effects.

A current explicit instruction may authorize the exact consequential action/target. Do not ask again when target/scope/material effect remain unchanged. Generic positive feedback does not imply publication unless an established review condition clearly makes approval of the shown result the publish trigger.

Custom PHP/plugin work follows WordPress input validation, sanitization, output escaping, capability checks, nonce/authorization separation, REST `permission_callback`, prepared-query/API conventions, secret handling, and translation-ready user-facing strings.

Version-sensitive WordPress/WooCommerce/theme/plugin/Abilities/MCP behavior must be checked against current authoritative documentation when it materially affects implementation.

## 10. Runtime rule ownership

The distributable Skill remains shallow and progressively loaded:

| Runtime source | Canonical responsibility |
|---|---|
| `SKILL.md` | trigger/routing, universal control loop, source authority, universal review/approval/safety invariants |
| `references/project-workflow.md` | Project Foundation, canonical project artifacts, task semantics, multi-step progression, and project-level recovery triggers |
| `references/implementation-decisions.md` | WordPress surface ownership, native-vs-custom decisions, placement/naming, shared/global impact/rollback awareness |
| `references/gutenberg-safety.md` | Gutenberg serialization, invalid-block diagnosis, block-specific validation |
| `references/design-conventions.md` | UI/UX/design judgment and visual review |
| `references/workspace-memory.md` | Workspace persistence, exact progressive-resume procedure, duplicate avoidance, optimistic concurrency, transient Workspace failure |
| `agents/openai.yaml` | ChatGPT-facing metadata |

Reference files may point to another domain whose rule also applies, but they must not become a second owner of that domain's policy. All runtime references remain directly reachable from `SKILL.md`.

## 11. Non-goals

- General WordPress facts unrelated to site building/implementation.
- General-purpose WordPress administration or commerce operations unrelated to the requested builder outcome.
- Forcing Astra, Gutenberg, Gravity Forms, WooCommerce, Elementor, or any named product universally.
- Maintaining a plugin/theme encyclopedia.
- Recreating functionality already cleanly owned by WordPress or a suitable installed capability.
- Forcing Custom HTML/custom code for every section.
- Recreating GitHub/Jira-style orchestration inside WordPress.
- Treating every request as a persistent task or every page as a project.
- Loading Project Foundation on every chat/task/page merely because it exists.
- Storing chat transcripts, hidden reasoning, secrets, or broad live-site/database mirrors in Workspace.
- Adding vector-memory/RAG or an external persistence service merely for continuity.
- Blind retry loops.
- Excessive boilerplate, repeated confirmation, or process ceremony.

## 12. Acceptance and release requirements

A release-quality revision must preserve these outcomes:

- standard Skill validation and packaging pass;
- small bounded work remains fast;
- substantial projects resolve material Foundation gaps before major build even when no persistence location is available;
- novice intake does not require WordPress terminology;
- one canonical durable Foundation is used when persistence exists, while current-session Foundation semantics remain valid without persistence;
- additive routing can load every applicable direct reference without duplicate loading, including Workspace mechanics for new as well as resumed projects;
- canonical singleton project documents are reused before new copies are created, while tasks use purpose-based titles;
- global/template/shared changes inspect impact and preserve practical revision/rollback evidence when available;
- Core blocks/Patterns/native mechanisms remain preferred when fit;
- Gutenberg raw serialization is validated proportionally and invalid blocks are repaired narrowly;
- static review always occurs and rendered/editor checks are added when available;
- naming/ownership remain understandable to future humans;
- connected mode reconciles stale/ambiguous writes and bounded transient route failure;
- live WordPress remains authoritative for current site state;
- manual mode remains useful without Bridge/Workspace and never claims unavailable persistence;
- consequential-action classification remains explicit enough to avoid both blanket confirmation and missed gates;
- public `skill.zip` contains exactly the intended runtime files from the tagged/integrated revision.

Behavioral regression scenarios live in `docs/BEHAVIOR-EVALS.md`.

## 13. Repository and release model

| Path/system | Responsibility |
|---|---|
| `README.md` | user-facing installation/usage guide |
| `SKILL.md` + `references/` + `agents/` | installable runtime Skill |
| `MASTER-SPEC.md` | this canonical product specification |
| `docs/architecture.md` | concise runtime architecture/rule ownership |
| `docs/PROJECT-WORKSPACE-ARCHITECTURE.md` | detailed Workspace/cross-chat persistence architecture |
| `docs/BEHAVIOR-EVALS.md` | behavioral regression scenarios |
| Git history / Issues / PRs | implementation history and unresolved work |
| Releases | immutable public `skill.zip` delivery evidence |

Repository-only documentation is not bundled into `skill.zip`. Public packaging uses OpenAI's standard Skill validation/package flow and the distributable archive name remains exactly `skill.zip`.