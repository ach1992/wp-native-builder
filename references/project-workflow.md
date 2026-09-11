# Project Foundation and Multi-step Site Workflow

Load this reference for a new site, substantial redesign, multi-page/multi-surface build, or any project where durable project-level decisions will materially drive later work or continuation.

## 1. Do not design before the project is foundation-ready

For this class of work, use:

```text
DISCOVER EXISTING STATE
  -> FOUNDATION INTAKE
  -> PROJECT FOUNDATION READY
  -> DERIVE SPECIALIZED PROJECT DOCS / TASKS
  -> PLAN ENOUGH TO ACT
  -> BUILD / VERIFY / REVIEW
  -> RECONCILE DURABLE STATE
  -> CONTINUE
```

Do not begin material design/build merely because enough information exists to make a visually plausible first page. First make the project-level intent sufficiently complete to avoid predictable rework.

Small bounded edits stay on the fast path and do not require this ceremony.

## 2. Canonical Project Foundation

Maintain one canonical durable **Project Foundation** for the site project when persistent project storage exists or the user has supplied another durable project location.

It owns only stable project-level truth:

- project/site purpose and primary outcomes;
- intended audiences/users and their important needs;
- scope and major deliverables/surfaces;
- required capabilities and critical interactions;
- brand/content/voice direction that materially constrains design;
- durable technical constraints and supported environments/languages;
- accessibility/RTL/LTR/localization requirements when material;
- important business/content/SEO/legal/privacy constraints that affect the build;
- explicit non-goals/out-of-scope boundaries;
- success/completion criteria;
- material owner decisions that would change the project if reversed.

It is **not** a worklog, page-content mirror, active backlog, plugin inventory, current live-site snapshot, or per-task implementation record.

Use one existing equivalent durable project brief/spec if it already owns these facts. Do not create a competing “master” document solely to satisfy naming.

## 3. Foundation-readiness coverage

Before declaring the Project Foundation ready, resolve every materially applicable domain below as **known**, **user delegated**, **safely inferred**, or **not applicable**:

| Domain | Examples of material questions |
|---|---|
| Purpose/outcomes | What is the site for? What must improve or become possible? |
| Audience | Who uses it? What do they need/trust/understand/do? |
| Scope | New site vs redesign; required pages/surfaces; launch boundary; excluded work |
| Content | Existing vs new content; content owners; key messages/CTA; multilingual/RTL needs |
| Brand/design | Existing identity; references; desired character; fidelity vs inspiration; prohibited styles |
| Functional needs | Forms, search, memberships, booking, ecommerce, filtering, accounts, integrations, interactions |
| Site architecture | Existing site vs new; theme/editing model/builder; reusable/global ownership; data models |
| Technical constraints | hosting/runtime constraints when relevant; plugin/license restrictions; browser/device requirements |
| Quality constraints | accessibility target/needs; responsive behavior; performance-sensitive surfaces; SEO/indexing-facing needs |
| Governance/delivery | who reviews content/design; draft vs live workflow; launch/publish constraints; future maintainability expectations |
| Success | observable acceptance/completion criteria |

Do not ask every example literally. Discover what is already knowable from the live site/project context first, then ask only unresolved material items.

### Novice-user intake

A novice must not need to understand terms such as FSE, template part, CPT, taxonomy, or Synced Pattern.

- Ask in plain language first, optionally explain the technical interpretation after the answer.
- Offer sensible examples/options when that makes the question answerable.
- Use compact staged batches rather than a giant questionnaire.
- Keep asking across batches until material coverage is complete; do not stop after an arbitrary question quota.
- Record delegated choices explicitly, e.g. “visual details delegated to builder,” rather than pretending the user supplied them.

## 4. Foundation stability and change control

After acceptance/readiness, Project Foundation leaves the routine hot path.

Do **not** reread or rewrite it for every page, block, task, chat, or implementation change. Routine work uses the nearest current authoritative source: derived docs, active tasks, live WordPress, code/config, preview/review state.

Reopen/update Project Foundation only when:

- the user accepts a material change to project purpose, audience, scope, durable constraint, non-goal, or success criteria;
- current authoritative evidence materially contradicts project-level intent and cannot be reconciled from a nearer source;
- recovery/completion cannot be resolved safely without it.

A change to Project Foundation is a material project-level change. Explain the impact and consult the user when the change is not already explicitly directed by the user. Implementation-only changes do not churn the foundation.

## 5. Derive specialized documents instead of overloading the foundation

Create only artifacts that pay for themselves. Typical derived artifacts may include:

### Site Architecture/Profile

Record durable ownership/mechanism facts needed repeatedly, such as:

- active theme and editing model;
- page builder ownership, if any;
- global header/footer/navigation/template ownership;
- page-content ownership;
- reusable-section mechanism;
- forms/commerce/data-model ownership;
- approved custom-code placement/prefix conventions;
- major plugin/theme capabilities intentionally relied on.

Do not use it as a complete plugin inventory or a replacement for live discovery. Reverify live state when current configuration matters.

### Information architecture / sitemap

Create when page hierarchy/navigation/content relationships matter across multiple tasks.

### Design direction/system

Create when recurring visual decisions materially affect multiple surfaces: typography, tokens, spacing/layout language, imagery, interaction/motion, responsive/RTL principles.

### Content/data model

Create when CPT/taxonomy/ACF/product/content relationships affect implementation repeatedly.

### Tasks

Create only work that benefits from acceptance clarity, sequencing, dependency, review/delivery state, or later continuation.

## 6. Task state

Keep task state compact and independent:

| Dimension | Values |
|---|---|
| Progress | `todo` / `in_progress` / `blocked` / `done` |
| Review | `not_required` / `pending` / `changes_requested` / `approved` |
| Delivery | `not_applicable` / `draft_preview` / `live` |

`done` does not imply `approved`; `approved` does not imply `live`; `live` requires actual intended delivery, preferably verified.

Useful task fields: title, concise goal, acceptance when needed, dependencies/blocker, target references, and short durable notes.

## 7. Plan enough to act

After Foundation readiness, derive only enough sequencing/architecture to prevent rework, then begin the highest-value implementable work.

```text
FOUNDATION READY
  -> DERIVE/REFRESH RELEVANT ARCHITECTURE + TASK
  -> CHOOSE OWNER/MECHANISM
  -> BUILD
  -> VERIFY
  -> REVIEW WHEN MATERIAL
  -> REVISE/APPROVE
  -> PUBLISH WHEN AUTHORIZED
  -> VERIFY LIVE
  -> RECONCILE DURABLE STATE
  -> NEXT USEFUL WORK
```

Do not turn project setup into weeks of speculative documentation.

## 8. Resume and recovery

On a fresh chat with persistent Workspace:

1. Request compact resume/orientation.
2. Identify project identity/current focus, active or review-blocked work, blockers, and references to relevant durable docs.
3. Fetch only the task/document details needed for the next decision/action.
4. Do **not** automatically load Project Foundation if a nearer current source is sufficient.
5. Load Project Foundation only under the stability/change triggers above.
6. Re-read live WordPress targets before overwrite-sensitive/current-state-dependent work.
7. Continue the next useful action; do not stop at a recovery summary.

## 9. Continuity reconciliation before yielding

After a material project step, before yielding control, ask internally:

> Could a fresh chat continue correctly from durable sources without this conversation?

If no and persistent capability exists, update the smallest authoritative artifact that owns the changed truth.

Examples:

- project-level scope changed -> Project Foundation;
- header/footer ownership discovered/changed -> Site Architecture/Profile;
- design system choice accepted -> design doc;
- task implemented but awaiting user visual review -> task Progress=`done`, Review=`pending`, Delivery=`draft_preview` as applicable;
- user approved and live publish verified -> update Review/Delivery accordingly;
- blocker discovered -> task blocker/dependency.

Do not create a session log or duplicate live WordPress content.

## 10. Complete-site launch

For a complete/launch-ready site, task completion alone is not project completion. Synthesize only launch concerns that materially apply to the actual project, such as navigation/content completeness, responsive/RTL behavior, accessibility of key flows, forms/interactions, links/media, material performance impact introduced by the build, important indexing-facing configuration/presentation, publication, and live verification.

Do not impose an unrelated giant launch checklist or pull external business/refund/payment/order operations into ordinary site-building scope.
