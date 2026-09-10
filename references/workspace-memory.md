# Workspace Memory and Recovery

Load this reference only when the current runtime exposes persistent WordPress project-Workspace capabilities or when resuming a project that is expected to use them.

## Use capabilities that actually exist

Treat `workspace-resume`, `workspace-document`, and `workspace-task` as logical capability roles from the product contract, not names to invent. Discover the current runtime surface and use only exposed capabilities whose documented behavior safely matches the needed resume/document/task operation.

If no suitable Workspace capability is exposed, fall back to normal manual continuity. Do not claim persistence, fabricate an object, or require the Bridge merely to continue useful WordPress work.

## Resume progressively

On a fresh or resumed connected project:

1. Request a compact orientation/resume packet before broad site rediscovery or project questioning.
2. Orient from only what is useful now: project identity/goal, current focus, active or review-blocked work, blockers, relevant durable decisions, and a small index/reference to potentially relevant documents.
3. Fetch only the task/document details needed for the current decision or next action. Do not load the full Workspace merely because it exists.
4. Reuse settled project intent and design constraints instead of asking the user to repeat them, unless current instruction or evidence materially conflicts.
5. Before changing an existing WordPress target, read/verify its current live state when that state matters.
6. Continue the next useful project action rather than stopping after producing a recovery summary.

## Keep intent and live reality separate

Use the sources for different questions:

- **Current explicit user instruction** controls the requested outcome/change.
- **Workspace** preserves durable project intent, accepted decisions, unresolved progress, and useful references.
- **Live WordPress** controls what content/configuration/objects actually exist now.

A Workspace note that says a page, design, or task was completed is not proof that the live object is unchanged. When Workspace and live state disagree, reconcile the actual target before mutation and update durable context only when useful. A clear current redesign or architecture instruction can supersede older stored conventions.

## Persist only future-useful context

Persist something only when all applicable conditions make it worthwhile: a future session materially needs it; it is not better recovered from current WordPress/source state; retaining it reduces repeated briefing, ambiguity, or lost progress; and it is safe to store.

Useful examples can include a concise project brief, durable site/stack profile, sitemap/IA decision, accepted design system/direction, content/data model, lasting decision, unresolved QA finding, or active task. Create only the artifacts the actual project needs.

Do not persist:

- full chats, hidden reasoning/chain-of-thought, routine worklogs, or repeated handoff/checkpoint prose;
- copied live page/product content merely to mirror WordPress;
- credentials, application passwords, tokens, auth headers, salts, private keys, or secrets;
- unnecessary customer/order/payment/financial payloads or broad plugin/database dumps.

## Safe Workspace writes

Keep Workspace writes as narrow as live-site writes, but do not use WordPress Revision IDs as the authority for Workspace continuity or optimistic concurrency. For an overwrite-sensitive Workspace Document/Task update, read the capability's current **Workspace-owned identity** (for example `version + state_hash`), send that expected identity with the update when supported, and treat an identity mismatch as a stale/conflict result. Re-read current Workspace state, reconcile newer valid work, and only then retry.

`workspace-resume`, current Workspace state, and stale-write protection must remain usable when WordPress Revisions are disabled, limited, or pruned. WordPress Revisions may be useful optional secondary history for ordinary WordPress content or for Workspace inspection when available, but they are not the Workspace's current-state or concurrency dependency. Any Bridge-managed durable snapshot/history mechanism is an implementation detail; use it only if the connected runtime actually exposes relevant behavior.

If a Workspace write outcome is ambiguous, re-read first; never retry blindly in a way that can duplicate or erase newer context. Update durable context when a meaningful project decision, task state, blocker, review state, or delivery fact changes and future continuation benefits. Do not update memory merely to record that another conversational step occurred.
