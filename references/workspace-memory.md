# Workspace Memory and Recovery

Load this reference whenever the current runtime exposes persistent WordPress project-Workspace capabilities that are relevant to the current substantial/multi-step work, including both new project persistence and later resume. Project/Foundation/task semantics remain owned by `SKILL.md` and `project-workflow.md`; this file is the single owner of the exact Workspace persistence, progressive-resume, duplicate-avoidance, concurrency, and fallback procedure.

## 1. Use only capabilities that exist

Treat `workspace-resume`, `workspace-document`, and `workspace-task` as logical capability roles, not names to invent. Discover the current runtime and use only exposed capabilities whose documented behavior safely matches the needed operation.

If no suitable Workspace capability is exposed, continue in manual mode. Do not claim persistence or fabricate objects.

## 2. Resume progressively

When starting or resuming a connected multi-step project that uses Workspace:

1. request compact orientation/resume before broad site rediscovery or questioning;
2. orient from project identity, current focus, active/review-blocked work, blockers, and references to potentially relevant durable documents;
3. fetch only task/document details needed for the next decision/action;
4. prefer nearer current sources instead of automatically loading Project Foundation;
5. load Foundation only when project-level intent is unresolved/changed or recovery/completion requires it;
6. before changing a current WordPress target, read/verify live state when it matters;
7. continue the next useful action rather than stopping after a recovery summary.

A Workspace note is retained intent/state, not proof that a live WordPress object is unchanged.

## 3. Persist only future-useful context

Persist only when later continuation materially benefits and a stronger current source does not already own the fact. Typical singleton documents use the canonical names from `project-workflow.md`, such as `Project Foundation`, `Site Architecture Profile`, `Information Architecture`, `Design Direction`, and `Content/Data Model`.

Do not persist full chats, hidden reasoning, routine worklogs, repeated checkpoints, copied live content, credentials/secrets, or unnecessary customer/order/payment/financial data.

## 4. Discover/reuse before create

For canonical singleton documents, and for tasks where an equivalent work item may already exist, use:

```text
DISCOVER -> REUSE/UPDATE -> CREATE ONLY IF ABSENT -> VERIFY
```

- Search/list the decision-relevant current objects before creating a canonical singleton document.
- Reuse an existing semantically equivalent document even if its title differs.
- When the capability exposes a stable document `key`, use a stable purpose key for singleton documents (for example `project-foundation`, `site-architecture-profile`, `information-architecture`, `design-direction`, `content-data-model`) **after** confirming an equivalent object does not already exist. Do not assume the storage layer enforces key uniqueness unless its schema explicitly guarantees that.
- Never treat an incomplete/truncated listing as proof of absence.

## 5. Safe Workspace writes

Workspace current-state/concurrency identity is independent of WordPress Revision IDs. For an overwrite-sensitive Document/Task update:

1. read the current Workspace object and Workspace-owned identity such as `version + state_hash`;
2. require the update capability to accept expected identity;
3. if no guard exists, do not perform a blind overwrite;
4. submit with expected identity;
5. verify accepted resulting state when practical;
6. on stale/mismatch/conflict, re-read, reconcile newer valid work, then retry only if still correct;
7. on ambiguous write outcome, re-read authoritative state before any retry.

Workspace continuity and stale-write protection must remain usable if WordPress Revisions are disabled/limited/pruned. WordPress Revisions may remain optional secondary history for ordinary WordPress content, but they are not the Workspace current-state/concurrency authority. Bridge-managed snapshots/history are implementation details unless the runtime exposes relevant behavior. Site/database disaster recovery remains the hosting/backup boundary.

## 6. Continuity reconciliation

After a material multi-step workflow change, update the smallest Workspace object that owns the changed future-useful truth before yielding when practical. Do not update Workspace merely because another conversational step occurred, and do not leave non-obvious active project state understandable only from the current chat when a suitable persistent capability exists.

## 7. Transient Workspace/connector failure

One timeout/unavailable/transport failure is not proof the logical capability disappeared.

- Preserve recovered orientation/current state.
- Continue independent work.
- Re-discover/retry once when failure semantics or changed runtime evidence make a transient recovery plausible.
- Do not blind-loop identical failures.
- If still unavailable, continue manual/non-overwrite work and report a capability blocker only when required work truly cannot progress.