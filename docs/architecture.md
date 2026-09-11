# WP Native Builder architecture

This document is the concise maintained architecture overview of the public Skill. It is implementation documentation, not a project log or release-history archive.

For durable product requirements, see [`MASTER-SPEC.md`](../MASTER-SPEC.md). For the detailed persistent Workspace/cross-chat contract, see [`PROJECT-WORKSPACE-ARCHITECTURE.md`](PROJECT-WORKSPACE-ARCHITECTURE.md).

## Runtime structure

The distributable is intentionally small and progressively loaded:

```text
wp-native-builder/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── design-conventions.md
    ├── implementation-decisions.md
    ├── project-workflow.md
    └── workspace-memory.md
```

`SKILL.md` is the control plane. It owns the core operating loop, source authority, question/inference behavior, mechanism selection, manual/connected routing, approval boundaries, and direct links to conditional references.

The files under `references/` are loaded only when the current task makes their domain relevant. This keeps routine WordPress requests from paying the context cost of unrelated guidance.

## Repository source responsibilities

| Source | Responsibility |
|---|---|
| `README.md` | User-facing installation, usage, capabilities, and operating model |
| `SKILL.md` | Runtime routing and model behavior that applies broadly |
| `references/design-conventions.md` | Material UI/design, visual references, responsive behavior, RTL, accessibility, presentation quality |
| `references/implementation-decisions.md` | Non-obvious mechanism and architecture selection across WordPress/theme/builder/plugin/custom-code surfaces |
| `references/project-workflow.md` | Proportional multi-step project progression and review/launch handling |
| `references/workspace-memory.md` | Persistent Workspace recovery, retention, write identity, stale/conflict handling |
| `agents/openai.yaml` | ChatGPT-facing Skill metadata |
| `MASTER-SPEC.md` | Canonical durable product/project requirements and non-goals |
| `docs/architecture.md` | Concise maintained implementation architecture overview |
| `docs/PROJECT-WORKSPACE-ARCHITECTURE.md` | Detailed persistent Workspace and cross-chat site-project architecture |

Git history, Issues, Pull Requests, Actions, and Releases own implementation and delivery history. Historical planning, transient recovery checkpoints, and release coordination do not belong in runtime instructions or permanent architecture documents.

## Mechanism-first design

The Skill keeps two decisions separate:

1. **Implementation mechanism** — which current WordPress/theme/builder/plugin/data surface should own the requested behavior?
2. **Execution transport** — when connected, which actually exposed Ability/tool can safely operate that mechanism?

This prevents the connector from becoming the architecture. A native or plugin-owned Ability can be preferable to a Bridge-owned operation if it exposes the better supported path.

## Stack adaptation

The Skill has preferred defaults for otherwise unspecified/new projects, but the current site's suitable architecture outranks those defaults. It must not convert an Elementor, Kadence, block-theme, WooCommerce, ACF, or other established site merely to match the preferred stack.

The runtime discovers or asks only for state that can materially change the implementation or approval decision.

## Connected execution contract

Connected work follows a narrow read/reconcile/write/verify model:

1. inspect relevant current architecture, object identity, and exposed abilities;
2. choose the existing suitable site mechanism;
3. prefer draft/preview/reversible changes during iteration;
4. include current identity on overwrite-sensitive writes when supported;
5. on stale/conflict state, re-read and reconcile rather than overwriting;
6. on ambiguous write outcome, re-read before any retry;
7. verify resulting state when practical;
8. never invent an ability, permission, object identity, or write result.

If no safe connected route exists, the Skill remains useful in manual mode.

## Persistent Workspace contract

Persistent project context is optional and capability-driven. The maintained companion Bridge provides the accepted Workspace surface for the supported direct connected setup; the Skill still discovers capabilities at runtime and falls back cleanly when that surface is unavailable.

When Workspace support is exposed:

- `workspace-resume` provides a compact orientation packet;
- document/task details are fetched progressively only when relevant;
- live WordPress content/configuration remains the source of truth for current site state;
- Workspace Documents and Tasks store durable project context only when later continuation benefits;
- overwrite-sensitive Workspace writes require Workspace-owned expected identity, such as `version + state_hash`;
- stale writes must fail closed, followed by re-read, reconciliation, and only then a retry;
- ambiguous write outcomes are re-read from authoritative state before retry;
- Workspace continuity/concurrency must not depend on WordPress Revision IDs;
- ordinary WordPress content can still use its normal object/revision/version mechanisms.

This supports cross-chat continuation without turning the Workspace into a transcript archive or second CMS. The complete behavioral/storage boundary is defined in [`PROJECT-WORKSPACE-ARCHITECTURE.md`](PROJECT-WORKSPACE-ARCHITECTURE.md).

## Approval model

Permission/capability and user approval are independent. The runtime does not stop for every write.

Non-consequential reversible edits, drafts, previews, reads, validation, and preparation may proceed within scope. Approval is required only at an actual consequential boundary. A current exact instruction can satisfy that boundary without duplicate confirmation while the target, scope, and material effect remain unchanged.

## Packaging boundary

Only the six runtime files shown above are packaged as `skill.zip`. Repository-facing files such as `README.md`, `LICENSE`, `MASTER-SPEC.md`, and `docs/` are intentionally excluded.

The package is validated with OpenAI's standard Skill validator and packager before release. The archive name remains exactly `skill.zip`.
