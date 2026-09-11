# WP Native Builder — Behavioral Regression Scenarios

Use these scenarios when changing runtime Skill behavior. A revision should improve finished, maintainable WordPress outcomes without forcing project ceremony onto bounded work or silently changing source-of-truth/approval rules.

## A. Bounded edit stays fast

**Scenario:** User asks to adjust spacing/color/text on one known existing Gutenberg section.

**Expected:** inspect relevant target/owner, make the bounded change, validate/review proportionally.  
**Forbidden:** creating Project Foundation/tasks/docs or running a broad site intake merely because Workspace exists.

## B. New site with novice user

**Scenario:** User says “build my company website” but cannot answer WordPress-specific terminology.

**Expected:** perform evidence-first discovery; ask plain-language staged questions covering all material Foundation domains; explain options where helpful; continue batches until each material domain is known/delegated/safely inferred/N/A; create/reuse one canonical Project Foundation before material design/build.  
**Forbidden:** stopping after an arbitrary 1–4 questions, making up business/brand requirements, or beginning a polished homepage while critical audience/scope/content/functional constraints remain unresolved.

## C. Existing Project Foundation is reused

**Scenario:** Workspace already contains a durable brief that owns accepted project-level intent.

**Expected:** reconcile/reuse it as Project Foundation and derive only missing specialized artifacts.  
**Forbidden:** creating a competing `MASTER`, `FOUNDATION`, or project-spec document solely for naming consistency.

## D. Foundation leaves the hot path

**Scenario:** Foundation is ready; user later asks to change one posts section.

**Expected:** use compact resume/current task + relevant Site Architecture/Profile/live WordPress. Load Foundation only if project-level intent becomes necessary.  
**Forbidden:** rereading/reconciling the full Foundation on every task/chat/page.

## E. Accepted project-level change updates Foundation

**Scenario:** User changes the site from lead-generation to paid membership with a materially different primary audience/scope.

**Expected:** update Project Foundation and affected derived architecture/tasks only; continue unaffected safe work.  
**Forbidden:** leaving Foundation stale or globally rewriting every project document.

## F. Implementation-only change does not churn Foundation

**Scenario:** A Query Loop implementation is replaced by an equivalent theme/plugin mechanism without changing accepted behavior/scope.

**Expected:** update architecture/task/code truth if useful; leave Foundation unchanged.  
**Forbidden:** using Foundation as a progress/implementation log.

## G. Block-theme header ownership

**Scenario:** User wants a redesigned header on a block theme.

**Expected:** route to Site Editor/template part/global mechanisms and inspect reuse/impact.  
**Forbidden:** adding a separate Custom HTML header inside every page by default.

## H. Builder-owned global shell

**Scenario:** Existing site uses a page builder's global header/footer system.

**Expected:** preserve builder global ownership unless migration is explicit.  
**Forbidden:** reimplementing header/footer in Gutenberg/HTML merely because the connected tool exposes page content writes.

## I. Native Gutenberg before Custom HTML

**Scenario:** User wants a standard hero, buttons, content grid, or reusable section that Core blocks/Patterns can represent cleanly.

**Expected:** choose suitable Core blocks/settings/Pattern semantics.  
**Forbidden:** selecting Custom HTML because HTML is easier for the model to generate.

## J. Gutenberg serialization validation

**Scenario:** Runtime must write raw serialized block markup.

**Expected:** verify ownership; preserve block delimiter/nesting/expected wrapper structure; use any available block-aware parser/serializer/validation/editor preview; re-read stored content; resolve invalid-block/recovery warnings before user handoff.  
**Forbidden:** claiming validation without a meaningful validator, modifying static Core-block saved HTML arbitrarily, or reserializing the whole page unnecessarily.

## K. Existing invalid block

**Scenario:** Editor says “This block contains unexpected or invalid content.”

**Expected:** identify exact block and expected-vs-actual difference; preserve content; repair smallest representation/current contract; revalidate.  
**Forbidden:** flattening the entire page to Custom HTML as the default fix.

## L. Transient connector failure

**Scenario:** A previously available WordPress route returns one timeout/temporary unavailable error.

**Expected:** preserve recovered state, continue independent work, distinguish transient route failure from permission/schema absence, and re-discover/retry once when recovery is plausible.  
**Forbidden:** immediately declaring WordPress unavailable, asking user to restart the project, or blind-looping identical retries.

## M. Real capability absence

**Scenario:** Authoritative discovery proves the required write semantic is not exposed or permission is denied.

**Expected:** stop retrying the route, keep correct mechanism choice, continue safe manual/preparation work, and surface the exact capability blocker only if it actually prevents further outcome progress.  
**Forbidden:** changing site architecture merely to match an unrelated available tool.

## N. Chat-loss recoverability

**Scenario:** A material project step ends after discovering architecture ownership and leaving a design task awaiting user review.

**Expected:** persist the ownership decision in Site Architecture/Profile and current task progress/review/delivery state; a fresh chat can resume from compact orientation.  
**Forbidden:** leaving non-obvious state only in chat or creating a full session transcript.

## O. Weak UX proposal

**Scenario:** User requests an obviously outdated/confusing/inaccessible pattern but has not demanded pixel-exact reproduction.

**Expected:** briefly explain the concrete issue and recommend one better direction; implement the better direction when ordinary design judgment is delegated.  
**Forbidden:** blindly presenting the weak pattern as best practice or forcing a cosmetic decision gate.

## P. Explicit fidelity request

**Scenario:** User explicitly requires high-fidelity reproduction of a reference and the approach is safe/valid.

**Expected:** honor fidelity while preserving accessibility/safety and mention only material conflicts.  
**Forbidden:** redesigning merely because the model prefers another contemporary style.

## Q. Human-maintainable naming

**Scenario:** Skill creates templates, Patterns, snippets, tasks, styles, and custom identifiers.

**Expected:** names communicate purpose/ownership; custom identifiers use a stable project prefix where needed; edit location is discoverable.  
**Forbidden:** `Section 1`, `Custom CSS 2`, `Untitled`, random hashes, or tool-internal names as primary maintainer-facing identity.

## R. Source authority remains separate

**Scenario:** Workspace says a page is complete, but live WordPress changed afterward.

**Expected:** live WordPress controls current object state; Workspace controls retained intent/task state; reconcile without overwriting newer valid work.  
**Forbidden:** treating Workspace history as proof of unchanged live state.

## S. Safe approval semantics remain unchanged

**Scenario:** A non-consequential reversible draft edit is ready, or a live publish was explicitly authorized for the exact unchanged target.

**Expected:** proceed under existing approval rules; no extra confirmation merely because Project Foundation/self-review exists.  
**Forbidden:** turning stronger intake/review into blanket human gates.

## T. Package remains progressively loaded

**Scenario:** Runtime changes add project/Gutenberg guidance.

**Expected:** `SKILL.md` remains compact control-plane/routing; details live in direct shallow references loaded only when relevant; standard Skill validation/package passes.  
**Forbidden:** moving all domain detail into one huge `SKILL.md` or creating deeply nested reference dependencies.
