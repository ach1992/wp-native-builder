# WP Native Builder architecture

This is the concise runtime and rule-ownership overview. Stable product requirements live in [`MASTER-SPEC.md`](../MASTER-SPEC.md); persistent Workspace architecture lives in [`PROJECT-WORKSPACE-ARCHITECTURE.md`](PROJECT-WORKSPACE-ARCHITECTURE.md); regression scenarios live in [`BEHAVIOR-EVALS.md`](BEHAVIOR-EVALS.md).

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

`SKILL.md` is the control plane. Request routing is additive rather than mutually exclusive; every applicable direct reference may be loaded once.

## Rule ownership

| Runtime source | Owns |
|---|---|
| `SKILL.md` | trigger/routing, universal control loop, source authority, universal review/approval/safety invariants |
| `references/project-workflow.md` | Project Foundation, canonical project artifacts, task semantics, multi-step progression, and project-level recovery triggers |
| `references/implementation-decisions.md` | WordPress owner/mechanism selection, native-vs-custom decisions, placement/naming, shared/global impact and rollback awareness |
| `references/gutenberg-safety.md` | Gutenberg serialization contract, invalid-block diagnosis, block-specific validation |
| `references/design-conventions.md` | UI/UX/design judgment, responsive/RTL/accessibility/performance and rendered visual review |
| `references/workspace-memory.md` | Workspace persistence, exact progressive-resume procedure, duplicate avoidance, optimistic concurrency, transient Workspace failure |
| `agents/openai.yaml` | ChatGPT-facing metadata |

References may state that another domain also applies, but they do not become a second owner of that domain's policy.

## Project truth model

```text
Project Foundation
  -> Site Architecture Profile
  -> Information Architecture / Design Direction / Content/Data Model when useful
  -> Workspace Tasks for unresolved execution/review/delivery state
  -> Live WordPress remains authoritative for current site state
```

Project Foundation is required only for substantial project classes. Readiness comes from resolved material coverage, not from a separate Foundation lifecycle enum, and does not depend on persistence availability; persistence only determines whether that context survives across chats. Once ready, Foundation leaves the normal hot path.

## Mechanism-first architecture

Every implementation makes two independent decisions:

1. **Owner/mechanism** — WordPress Core, Site Editor/template part, theme, builder, plugin, Pattern, form/commerce/data model, scoped frontend code, or custom extension.
2. **Transport** — an actually exposed connected capability that can safely operate the selected owner.

A connector does not become the architecture merely because it exposes an operation.

## Review architecture

Pre-user review has two levels:

- **Static review — always:** content/structure, ownership, semantics, obvious accessibility/responsive/RTL/performance/maintainability risks.
- **Runtime/rendered review — when available:** preview/editor/parser/live checks, Gutenberg invalid/recovery warnings, visual/functional verification and write-result verification.

Static review must not be described as rendered validation.

## Shared/global changes

Global/template/shared work inspects reuse/impact before mutation and captures current target identity plus a practical revision/rollback route when the runtime exposes one. This is evidence for safe recovery, not a new approval ceremony.

## Workspace architecture

Workspace is optional and capability-driven. When it is relevant to substantial/multi-step work, including a new project, it stores future-useful durable context, resumes progressively, reuses canonical singleton documents before create, guards overwrite-sensitive writes with Workspace-owned expected identity, and never replaces live WordPress as current-state authority. The exact Workspace resume/retrieval procedure is owned only by `references/workspace-memory.md`.

Task delivery retains the current Bridge-compatible enum: `not_applicable`, `draft_preview`, `live`. `not_applicable` means no draft/live state is currently established; intended later publication is represented by task goal/acceptance/targets/notes rather than a new lifecycle value.

## Packaging boundary

Only the seven runtime files under `SKILL.md`, `agents/`, and `references/` are packaged as `skill.zip`. Repository docs remain outside the Skill package. The public release asset must correspond to the tagged/integrated runtime revision.