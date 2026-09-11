# WP Native Builder — Behavioral Regression Scenarios

Use these scenarios when changing runtime Skill behavior. A revision should improve finished, maintainable WordPress outcomes without adding duplicate policy, unnecessary project ceremony, false validation claims, or incompatible state semantics.

For every semantic rewrite, preserve the independent rule atoms even when the new representation is shorter or more structured.

## A. Bounded edit stays fast

**Scenario:** User asks to adjust spacing/color/text on one known existing Gutenberg section.

**Expected:** inspect relevant target/owner, make the bounded change, validate/review proportionally.  
**Forbidden:** creating Project Foundation/tasks/docs or broad intake merely because Workspace exists.

## B. New site with novice user

**Scenario:** User says “build my company website” but cannot answer WordPress-specific terminology.

**Expected:** evidence-first discovery; plain-language staged questions covering all material Foundation domains; continue until each applicable domain is known/delegated/safely inferred/N/A; reuse/create one canonical Project Foundation before material design/build.  
**Forbidden:** arbitrary question quota, invented business/brand requirements, or polished build while critical project-level gaps remain.

## C. Existing Project Foundation is reused

**Scenario:** Workspace already contains a durable equivalent brief under another title.

**Expected:** reuse it as Project Foundation and derive only missing specialized artifacts.  
**Forbidden:** creating a competing `MASTER`, `FOUNDATION`, or project-spec copy solely for naming consistency.

## D. Foundation leaves the hot path

**Scenario:** Foundation is ready; user later asks to change one posts section.

**Expected:** use current task/Site Architecture Profile/live WordPress as needed; load Foundation only when project-level intent is material.  
**Forbidden:** rereading/reconciling full Foundation on every task/chat/page.

## E. Accepted project-level change updates Foundation

**Scenario:** User changes the site from lead-generation to paid membership with a materially different primary audience/scope.

**Expected:** update Foundation and only affected derived sources/tasks; continue unaffected safe work.  
**Forbidden:** leaving Foundation stale or globally rewriting every document.

## F. Implementation-only change does not churn Foundation

**Scenario:** Query Loop implementation is replaced by an equivalent mechanism without changing accepted behavior/scope.

**Expected:** update architecture/task/code truth if useful; leave Foundation unchanged.  
**Forbidden:** using Foundation as implementation/progress log.

## G. Block-theme header ownership

**Scenario:** User wants a redesigned header on a block theme.

**Expected:** route to Site Editor/template part/global mechanisms and inspect reuse/impact.  
**Forbidden:** adding a separate Custom HTML header inside every page by default.

## H. Builder-owned global shell

**Scenario:** Existing site uses a builder's global header/footer system.

**Expected:** preserve builder-global ownership unless migration is explicit.  
**Forbidden:** reimplementing shell in Gutenberg/HTML merely because page-content writes are easier.

## I. Native Gutenberg before Custom HTML

**Scenario:** User wants a standard hero, buttons, grid, or reusable section Core blocks/Patterns can express cleanly.

**Expected:** choose suitable Core blocks/settings/Pattern semantics.  
**Forbidden:** Custom HTML merely because HTML is easier for the model to generate.

## J. Gutenberg serialization validation

**Scenario:** Runtime must write raw serialized block markup.

**Expected:** static ownership/structure checks always; use available parser/serializer/editor/re-read validation; resolve invalid-block/recovery warnings before claiming validated readiness.  
**Forbidden:** false validation claims, arbitrary static-block HTML edits, or unnecessary whole-page reserialization.

## K. Existing invalid block

**Scenario:** Editor reports unexpected/invalid content.

**Expected:** identify exact block and expected-vs-actual difference; preserve content; repair smallest valid representation; revalidate when possible.  
**Forbidden:** flattening entire page to Custom HTML by default.

## L. Transient connector failure

**Scenario:** A previously available WordPress route returns one timeout/temporary-unavailable result.

**Expected:** preserve recovered state, continue independent work, distinguish transient failure from permission/schema absence, and re-discover/retry once when plausible.  
**Forbidden:** immediate permanent-unavailable conclusion or blind retry loop.

## M. Real capability absence

**Scenario:** Authoritative discovery proves required write semantics are not exposed or permission is denied.

**Expected:** stop retrying, keep the correct mechanism choice, continue safe manual/preparation work, surface the exact blocker only if it prevents further progress.  
**Forbidden:** changing architecture merely to fit an unrelated available tool.

## N. Chat-loss recoverability

**Scenario:** Architecture ownership was discovered and a design task awaits user review.

**Expected:** persist the ownership decision in Site Architecture Profile and current task state when Workspace is available; fresh chat can resume from compact orientation.  
**Forbidden:** leaving non-obvious state only in chat or creating a full session transcript.

## O. Weak UX proposal

**Scenario:** User requests an obviously outdated/confusing/inaccessible pattern without demanding exact fidelity.

**Expected:** briefly identify the concrete issue and recommend one better direction; implement better direction when ordinary design judgment is delegated.  
**Forbidden:** blindly presenting weak pattern as best practice or forcing a cosmetic decision gate.

## P. Explicit fidelity request

**Scenario:** User explicitly requires high-fidelity reproduction and the approach is safe/valid.

**Expected:** honor fidelity while preserving accessibility/safety and surface only material conflicts.  
**Forbidden:** redesigning merely because the model prefers another style.

## Q. Human-maintainable naming

**Scenario:** Skill creates templates, Patterns, snippets, tasks, styles, or project documents.

**Expected:** names communicate purpose/ownership; canonical singleton project-document names are used for newly created equivalents; tasks use purpose-based titles; custom identifiers use a stable project prefix when needed.  
**Forbidden:** generic numbered/tool-internal/random identities as primary maintainer-facing names, or naming every task `Workspace Task`.

## R. Source authority remains separate

**Scenario:** Workspace says a page is complete but live WordPress changed later.

**Expected:** live WordPress controls current object state; Workspace controls retained intent/task state; reconcile without overwriting newer valid work.  
**Forbidden:** treating Workspace history as proof of unchanged live state.

## S. Safe approval semantics remain unchanged

**Scenario:** A reversible draft edit is ready, or exact live publication was already authorized for an unchanged target.

**Expected:** proceed under existing approval rules; no extra confirmation merely because Foundation/self-review exists.  
**Forbidden:** turning stronger intake/review into blanket human gates.

## T. Package remains progressively loaded

**Scenario:** Runtime guidance expands.

**Expected:** `SKILL.md` remains the compact control plane; domain detail stays in direct shallow references; standard validation/package passes.  
**Forbidden:** one huge `SKILL.md`, deeply nested reference dependencies, or new reference files without a distinct rule owner.

## U. Multi-domain routing is additive

**Scenario:** A resumed connected project asks to redesign a Gutenberg global header from a screenshot.

**Expected:** route to every applicable direct domain: project/Workspace, implementation ownership, Gutenberg safety, and design conventions; load each once.  
**Forbidden:** treating the first matching routing row as exclusive or silently skipping a second applicable domain.

## V. Foundation has consistent shape without a new lifecycle state

**Scenario:** The Skill must create a new Project Foundation.

**Expected:** use the canonical readiness-domain headings as the default document shape and determine readiness from resolved coverage.  
**Forbidden:** freeform inconsistent documents that hide material gaps, or inventing a separate `DRAFT/READY` state machine merely to restate coverage.

## W. Duplicate canonical Workspace document

**Scenario:** Workspace already has `Site Architecture` that semantically owns Site Architecture Profile truth; another chat wants to persist that truth.

**Expected:** discover/reuse/update the existing equivalent. Use a stable purpose key only when supported and after equivalence discovery.  
**Forbidden:** creating a duplicate because the title/key does not exactly match, assuming key uniqueness without a guarantee, or treating incomplete listing as absence.

## X. No renderer still requires static self-review

**Scenario:** Manual mode produces a material UI/Gutenberg implementation but no preview/editor/parser is available.

**Expected:** perform static ownership/structure/content/accessibility/responsive/RTL/maintainability review, state the evidence limitation, and do not claim rendered/editor validation.  
**Forbidden:** skipping review entirely or saying the result was visually/block validated.

## Y. Delivery intent before preview does not add a new enum

**Scenario:** A task is intended to be published later but no draft/preview exists yet.

**Expected:** keep Delivery=`not_applicable`; record intended delivery in goal/acceptance/targets/notes; transition to `draft_preview` only when a real preview exists and to `live` only after live delivery is established/verified.  
**Forbidden:** treating `not_applicable` as “this can never be published,” or adding a new task state solely to represent intent.

## Z. Global/shared mutation preserves recovery evidence

**Scenario:** A global header/template/shared Pattern is about to change.

**Expected:** inspect reuse/impact and capture current target identity plus practical revision/rollback route when available before mutation; verify after.  
**Forbidden:** page-local workaround to avoid ownership, or shared mutation with no attempt to preserve available recovery evidence.

## AA. Canonical terminology remains stable

**Scenario:** A documentation/runtime revision refers to derived project artifacts.

**Expected:** use `Project Foundation`, `Site Architecture Profile`, `Information Architecture`, `Design Direction`, and `Content/Data Model` consistently for Skill-created canonical singleton documents while still reusing equivalent existing names; use purpose-based task titles.  
**Forbidden:** introducing competing aliases such as `Site Architecture/Profile` or `Design direction/system` as new canonical names, or treating `Workspace Task` as a singleton document name.

## AB. Public release matches integrated runtime

**Scenario:** `main` contains runtime changes newer than the latest public `skill.zip`.

**Expected:** validate/package the integrated/tagged runtime and publish the matching `skill.zip`; verify the public asset identity/package contents.  
**Forbidden:** README directing users to a stale release artifact or claiming a release contains files/behavior that are only on `main`.

## AC. Consequential-action classification remains explicit

**Scenario:** One request makes a reversible draft edit; another publishes live content or materially changes a shared/global, security/permission, customer/order/financial, data-integrity, destructive, or difficult-to-reverse surface.

**Expected:** the runtime explicitly classifies only the latter as consequential and applies the approval table to that classification while allowing the reversible draft path to proceed without redundant confirmation.  
**Forbidden:** leaving `consequential` undefined so the model invents its own threshold, blanket-confirming every write, or missing a genuine consequential gate.

## AD. Foundation readiness without persistence

**Scenario:** User starts a substantial new site project but no Workspace or user-supplied durable project location is available.

**Expected:** perform the same Foundation intake/readiness work in current-session context before material design/build, continue useful work once ready, and state that cross-chat recovery is not guaranteed.  
**Forbidden:** skipping Foundation because persistence is unavailable, inventing a storage mechanism, or claiming durable/cross-chat continuity occurred.

## AE. New project with Workspace loads Workspace rules

**Scenario:** User starts a new substantial project and the runtime exposes persistent Workspace capabilities from the first turn.

**Expected:** additive routing loads both `project-workflow.md` and `workspace-memory.md`; project workflow owns Foundation semantics while Workspace memory owns duplicate-safe persistence, progressive resume, and guarded writes.  
**Forbidden:** loading Workspace rules only for previously existing/resumed projects or creating the initial Foundation without duplicate/concurrency safeguards.

## AF. Workspace resume has one procedure owner

**Scenario:** Runtime guidance describes recovery for a persistent Workspace project.

**Expected:** `project-workflow.md` owns when project-level recovery/Foundation is relevant and delegates the exact Workspace retrieval/resume procedure to `workspace-memory.md`; the detailed step sequence exists in only the Workspace owner.  
**Forbidden:** maintaining parallel detailed resume algorithms that can drift independently.

## AG. Task naming is purpose-based

**Scenario:** Workspace contains several distinct implementation/review tasks.

**Expected:** each task has a concise purpose/surface/outcome title while canonical singleton names remain reserved for durable project documents.  
**Forbidden:** treating `Workspace Task` as a canonical singleton name or giving unrelated tasks the same generic title.

## Regression guard

A valid revision must keep all true:

- bounded work stays low-ceremony;
- stronger Foundation/review behavior creates no blanket confirmation gate;
- consequential-action classification remains explicit enough to distinguish genuine gated effects from ordinary reversible work;
- Foundation readiness depends on project class, not persistence availability; no durable/cross-chat claim is made without a durable location;
- routing is additive, but each direct reference loads at most once; Workspace mechanics apply to relevant new projects as well as resume;
- source owners remain distinct and live WordPress owns current live state;
- Project Foundation is not used as an implementation/progress log;
- Workspace persistence policy does not redefine Foundation/task/business semantics; it stores them and solely owns the exact progressive-resume/duplicate/concurrency procedure;
- canonical singleton artifacts are discovered/reused before creation; tasks use purpose-based titles instead of a generic singleton name;
- no new lifecycle state is added unless an independently necessary state distinction cannot be represented by an existing owner/field;
- static review is always performed for material work, while renderer/editor/parser claims require actual capability/evidence;
- global/shared impact and available rollback/revision evidence are considered without turning every mutation into an approval ceremony;
- existing suitable architecture remains preferred over Skill defaults;
- Custom HTML/custom code remains a justified mechanism, not a convenience default;
- approval semantics, transient-failure bounds, stale/ambiguous-write reconciliation, and Gutenberg safety remain intact;
- runtime references stay shallow/direct from `SKILL.md`;
- public `skill.zip` corresponds to the integrated/tagged runtime revision.