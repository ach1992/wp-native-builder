# WP Native Builder architecture

This is the concise maintained runtime architecture overview. Durable product requirements live in [`MASTER-SPEC.md`](../MASTER-SPEC.md); detailed persistent Workspace behavior lives in [`PROJECT-WORKSPACE-ARCHITECTURE.md`](PROJECT-WORKSPACE-ARCHITECTURE.md); behavioral regression scenarios live in [`BEHAVIOR-EVALS.md`](BEHAVIOR-EVALS.md).

## Runtime structure

```text
wp-native-builder/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── design-conventions.md
    ├── gutenberg-safety.md
    ├── implementation-decisions.md
    ├── project-workflow.md
    └── workspace-memory.md
```

`SKILL.md` is the compact control plane. It routes request class, source authority, question behavior, Project Foundation requirements, mechanism selection, manual/connected execution, transient-failure behavior, continuity reconciliation, and approval boundaries.

References are shallow and conditionally loaded:

| Source | Responsibility |
|---|---|
| `references/project-workflow.md` | Project Foundation intake/readiness/stability, derived docs/tasks, multi-step progression, recovery and continuity reconciliation |
| `references/implementation-decisions.md` | WordPress surface ownership, native-vs-custom mechanism selection, header/footer/global routing, maintainable placement/naming |
| `references/gutenberg-safety.md` | Gutenberg serialization contract, native-first block writes, invalid-block diagnosis, mandatory pre-user block self-review |
| `references/design-conventions.md` | UI/UX design judgment, visual quality, responsive/RTL/accessibility/performance, pre-user visual review |
| `references/workspace-memory.md` | Persistent Workspace Foundation/docs/tasks, progressive recovery, retention, concurrency, transient Workspace failure |
| `agents/openai.yaml` | ChatGPT-facing Skill metadata |

Repository-only files are not bundled into the Skill.

## Project state architecture

The project model deliberately separates stable project truth from current work/live state:

```text
Project Foundation
  -> Site Architecture/Profile
  -> IA / Design / Content-Data docs when useful
  -> Tasks / review / delivery state
  -> Live WordPress objects remain authoritative for current site state
```

Project Foundation is required only for substantial project classes. Once ready, it leaves the normal hot path. Routine work uses the nearest current authoritative source and reopens Foundation only for material project-level change, contradiction, or recovery/completion need.

## Mechanism-first architecture

Every implementation has two separate decisions:

1. **Owner/mechanism** — WordPress Core, Site Editor/template part, theme, page builder, plugin, Pattern, form/commerce/data model, scoped frontend code, or custom extension.
2. **Transport** — which actually exposed connected capability safely operates that owner.

A connector never becomes the architecture merely because it exposes an operation.

Global shell/header/footer/template/navigation/reusable surfaces must resolve ownership before page-local markup is considered. Gutenberg surfaces check Core blocks/settings/Patterns/template ownership before Custom HTML.

## Gutenberg safety architecture

Raw serialized Gutenberg content is version/registration-sensitive and may become invalid when stored markup differs from the block's expected saved representation.

The runtime therefore prefers block-aware writes and requires proportional pre-user validation when raw serialization is used. It avoids reserializing unrelated blocks and repairs invalid blocks at the smallest affected representation.

## Connected execution

Connected mutation follows a narrow read/reconcile/write/verify model:

1. inspect relevant architecture/target/capabilities;
2. choose owner/mechanism;
3. prefer reversible draft/preview writes;
4. use current identity for overwrite-sensitive writes when supported;
5. reconcile stale/conflicted state;
6. re-read ambiguous write outcomes before retry;
7. verify resulting state when practical.

One plausible transport/runtime failure does not erase the recovered plan. The runtime continues independent work and performs one bounded re-discovery/retry when transient recovery is plausible before concluding that required semantics are genuinely unavailable.

## Pre-user quality gate

Material visual/block work follows:

```text
BUILD -> PREVIEW/VALIDATE -> AI SELF-REVIEW -> FIX CLEAR DEFECTS
      -> USER REVIEW WHEN NEEDED -> PUBLISH WHEN AUTHORIZED -> VERIFY
```

This is a quality loop, not an approval ceremony. Tiny reversible changes may skip irrelevant stages.

## Maintainability

Human-facing page/template/Pattern/snippet/doc/task names are semantic and purpose-based. Custom identifiers use a stable project prefix when appropriate. Edit ownership should be discoverable from durable project state for non-obvious custom/global work.

## Packaging boundary

Only the seven runtime files under `SKILL.md`, `agents/`, and `references/` are packaged as `skill.zip`. `README.md`, `LICENSE`, `MASTER-SPEC.md`, and `docs/` remain repository documentation.
