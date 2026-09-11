# Workspace Memory and Recovery

Load this reference only when the current runtime exposes persistent WordPress project-Workspace capabilities or when resuming a project expected to use them.

## 1. Use only capabilities that exist

Treat `workspace-resume`, `workspace-document`, and `workspace-task` as logical capability roles, not names to invent. Discover the current runtime and use only exposed capabilities whose documented behavior safely matches the needed operation.

If no suitable Workspace capability is exposed, continue in manual mode. Do not claim persistence or fabricate objects.

## 2. Canonical Project Foundation in Workspace

For a project class that requires Project Foundation, persist exactly one canonical durable Project Foundation document when Workspace provides a suitable document capability.

- Reuse an existing equivalent foundation/project brief when it already owns accepted project-level truth.
- Do not create competing master/project-spec documents.
- Keep specialized architecture/design/content/task state in derived documents/tasks, not duplicated into the Foundation.
- Do not rewrite Foundation for implementation progress.
- Update it only under the project-level change rules in `project-workflow.md`.

The Project Foundation is discoverable durable context, not the default document loaded on every resume.

## 3. Resume progressively

On a fresh/resumed connected project:

1. Request compact orientation/resume before broad site rediscovery or questioning.
2. Orient from project identity, current focus, active/review-blocked work, blockers, relevant durable decisions, and references to potentially relevant documents.
3. Fetch only task/document details needed for the next decision/action.
4. Prefer nearer current sources over automatically loading Project Foundation.
5. Load Foundation only when project-level intent is unresolved/changed or recovery/completion requires it.
6. Reuse settled project intent and design constraints instead of asking the user to repeat them.
7. Before changing a current WordPress target, read/verify live state when it matters.
8. Continue the next useful action rather than stopping after a recovery summary.

## 4. Keep intent and live reality separate

- Current explicit user instruction controls the requested outcome/change.
- Project Foundation controls accepted durable project-level intent.
- Derived Workspace docs/tasks control their specialized durable intent/current execution state.
- Live WordPress controls actual current site objects/configuration.

A Workspace note that says a page/task is complete is not proof that the live object is unchanged.

## 5. Persist only future-useful context

Persist when later continuation materially benefits and a stronger current source does not already own the fact.

Useful examples:

- Project Foundation;
- Site Architecture/Profile;
- sitemap/IA decision;
- accepted design direction/system;
- content/data model;
- lasting decision;
- unresolved QA finding;
- active task/review/delivery state.

Do not persist full chats, hidden reasoning, routine worklogs, repeated checkpoints, copied live content, credentials/secrets, or unnecessary customer/order/payment/financial data.

## 6. Continuity reconciliation

After a material multi-step workflow change, update the smallest Workspace object that owns the changed future-useful truth before yielding when practical.

Do not update Workspace merely because another conversational step occurred. Do not leave non-obvious active project state understandable only from the current chat when a suitable persistent capability exists.

## 7. Safe Workspace writes

Workspace current-state/concurrency identity is independent of WordPress Revision IDs. For an overwrite-sensitive Document/Task update:

1. read the current Workspace object and current Workspace-owned identity such as `version + state_hash`;
2. require the update capability to accept expected identity;
3. if no guard exists, do not perform a blind overwrite;
4. submit with expected identity;
5. verify accepted resulting state when practical;
6. on stale/mismatch/conflict, re-read, reconcile newer valid work, then retry only if still correct;
7. on ambiguous write outcome, re-read authoritative state before any retry.

Workspace continuity and stale-write protection must remain usable even if WordPress Revisions are disabled/limited/pruned. WordPress Revisions may remain optional secondary history for ordinary WordPress content or inspection, but they are not the Workspace current-state/concurrency authority. Any Bridge-managed Workspace snapshots/history are implementation details; use them only when the runtime actually exposes relevant behavior. Site/database disaster recovery remains the normal hosting/backup boundary, not a Workspace responsibility.

## 8. Transient Workspace/connector failure

One timeout/unavailable/transport failure is not proof the logical capability has disappeared.

- Preserve recovered orientation/current state.
- Continue independent work.
- Re-discover/retry once when failure semantics or changed runtime evidence make a transient recovery plausible.
- Do not blind-loop identical failures.
- If still unavailable, continue manual/non-overwrite work and report a capability blocker only when required work truly cannot progress.
