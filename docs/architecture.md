# WP Native Builder architecture

This document describes the maintained architecture of the public Skill. It is implementation documentation, not a project log or release-history archive.

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

## Source responsibilities

| Source | Responsibility |
|---|---|
| `SKILL.md` | Runtime routing and model behavior that applies broadly |
| `references/design-conventions.md` | Material UI/design, visual references, responsive behavior, RTL, accessibility, presentation quality |
| `references/implementation-decisions.md` | Non-obvious mechanism and architecture selection across WordPress/theme/builder/plugin/custom-code surfaces |
| `references/project-workflow.md` | Proportional multi-step project progression and review/launch handling |
| `references/workspace-memory.md` | Persistent Workspace recovery, retention, write identity, stale/conflict handling |
| `agents/openai.yaml` | ChatGPT-facing Skill metadata |
| `README.md` | User installation, usage, capabilities, and operating model |
| `docs/architecture.md` | Repository-level architecture for maintainers/contributors |

Historical project planning, transient recovery checkpoints, and release coordination belong in Git/GitHub history and Issues/PRs, not in runtime instructions or permanent manager-state documents.

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

Persistent project context is optional and capability-driven. When the connected runtime exposes Workspace support:

- `workspace-resume` provides a compact orientation packet;
- document/task details are fetched progressively only when relevant;
- live WordPress content/configuration remains the source of truth for current site state;
- Workspace Documents and Tasks store durable project context only when later continuation benefits;
- overwrite-sensitive Workspace writes require Workspace-owned expected identity, such as `version + state_hash`;
- stale writes must fail closed, followed by re-read, reconciliation, and only then a retry;
- Workspace continuity/concurrency must not depend on WordPress Revision IDs;
- ordinary WordPress content can still use its normal object/revision/version mechanisms.

This supports cross-chat continuation without turning the Workspace into a transcript archive or second CMS.

## Approval model

Permission/capability and user approval are independent. The runtime does not stop for every write.

Non-consequential reversible edits, drafts, previews, reads, validation, and preparation may proceed within scope. Approval is required only at an actual consequential boundary. A current exact instruction can satisfy that boundary without duplicate confirmation while the target, scope, and material effect remain unchanged.

## Packaging boundary

Only the runtime directory is packaged as `skill.zip`. Repository-facing files such as `README.md`, `LICENSE`, and `docs/architecture.md` are intentionally excluded.

The package is validated with OpenAI's standard Skill validator and packager before release. The archive name remains exactly `skill.zip`.
