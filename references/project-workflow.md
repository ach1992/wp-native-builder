# Lightweight Site Project Workflow

Load this reference only for multi-surface or genuinely multi-step site work where sequencing, dependencies, staged review across deliverables, delivery state, or later continuation materially helps. Do not load it merely because one page is visually substantial; a coherent one-off task that can be completed and verified now stays on the normal fast path.

## Plan enough to act

Use a proportional control loop:

```text
RESUME / DISCOVER -> UNDERSTAND -> PLAN ENOUGH TO ACT -> BUILD -> VERIFY
  -> REVIEW WHEN MATERIAL -> REVISE / APPROVE -> PUBLISH WHEN AUTHORIZED
  -> VERIFY LIVE -> UPDATE USEFUL PROJECT STATE -> NEXT USEFUL WORK
```

Skip stages that do not apply. Do not turn a broad site request into weeks of speculative documentation before producing useful work. Resolve material unknowns with the core Ask / Infer / Defer rule, establish only enough structure/dependencies to avoid rework, then begin the next implementable part.

## Create project artifacts only when they pay for themselves

Create a persistent task/document only when it materially improves sequencing, acceptance clarity, dependency handling, review, cross-chat recovery, or completion. Small changes completed and verified in the current interaction need no permanent task.

Examples of useful project documents include a concise brief, site profile, sitemap/information architecture, design-system decisions, content/data model, lasting decisions, and unresolved QA notes. Do not create all of them by default and do not duplicate live WordPress content into them.

## Keep task state lightweight and unambiguous

When a task is useful, retain only fields that help future execution: concise title/goal, acceptance when ambiguity matters, dependencies/blocker, relevant WordPress target references, and short durable notes. Track these dimensions separately:

| Dimension | Values | Meaning |
|---|---|---|
| Progress | `todo` / `in_progress` / `blocked` / `done` | implementation progress |
| Review | `not_required` / `pending` / `changes_requested` / `approved` | human/visual review state |
| Delivery | `not_applicable` / `draft_preview` / `live` | where the requested result currently exists |

`done` does not mean `approved`; `approved` does not mean `live`; `live` should reflect actual publication/delivery, preferably after verification. Keep blockers/dependencies only when real.

## Visual review inside a project

For material visual work, combine the core approval rules with the design reference:

1. Build to a draft/preview when the mechanism supports it.
2. Inspect the rendered result and correct clear defects before user review when safe.
3. When user visual review is part of the workflow, mark review `pending` and show the current result.
4. Requested revisions -> `changes_requested`, revise, and preview again.
5. Clear approval of the current reviewed result -> `approved`; do not request a duplicate confirmation when the core approval condition already authorizes the next exact publish action.
6. Publication does not change delivery to `live` until the intended live result is established/verified.

Do not force this loop onto tiny reversible changes or work the user already explicitly authorized to apply live.

## Continue without reopening settled work

Reuse accepted project direction, stack ownership, content model, and design decisions on later tasks. Re-open a decision only when the current request overrides it, current WordPress state conflicts, or new evidence makes it materially relevant.

When persistent Workspace capabilities are available, use `workspace-memory.md` for resume/retention/concurrency. Without them, continue the same implementation workflow within current conversation/project artifacts and make no persistence claim.

For a complete-site request, do not infer overall project completion merely because individual build tasks are `done`; remaining launch-relevant site-building work may still need to be resolved before declaring the requested site outcome complete.

## Finish and launch proportionally

When the requested outcome is a complete or launch-ready site, synthesize remaining launch/QA work from the actual site and unresolved requirements rather than creating a fixed launch checklist by ritual. Inspect only applicable concerns such as navigation/content completeness, responsive/RTL behavior, accessibility, forms and submission paths, broken/missing links or media, performance introduced by the build, and important SEO/indexing-facing presentation/configuration that can prevent the intended site experience.

Do not mark the overall site outcome complete while a material launch-relevant defect remains merely because page/feature tasks are `done`. Conversely, do not block launch on generic checks that do not apply to the site's stack, content, audience, or requested scope.

Keep external business operations, fulfillment, payments, refunds, destructive order/customer actions, and unrelated operational readiness outside ordinary site-building launch QA unless the user explicitly requests that separate work.

After an authorized launch/publish step, verify the intended live surfaces when practical before treating delivery as `live` and close or update only the project state that materially changed.

After verified launch, when persistent Workspace capabilities exist, keep the default active resume focused on durable project/site context, still-relevant accepted architecture/design decisions, and unresolved or currently relevant work. Completed tasks and older decisions may remain recoverable when useful, but do not keep them prominent in the default packet or turn the Workspace into a session archive.

For later maintenance, reuse durable approved context without reopening settled intake, while re-reading live WordPress state when the current target matters. A current explicit redesign, rebrand, architecture change, or new requirement overrides conflicting stored conventions; update retained context when the new direction becomes durable.
