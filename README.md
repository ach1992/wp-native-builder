# WP Native Builder

**WP Native Builder** is a ChatGPT Skill for professional WordPress site design, implementation, review, troubleshooting, and lightweight project continuity.

It is **stack-adaptive** and **WordPress-native-first**: it works with the site you actually have instead of forcing every project toward one theme, builder, or plugin stack.

## What it does

WP Native Builder helps ChatGPT:

- understand the relevant current WordPress architecture before changing it;
- choose the mechanism that should own a feature before choosing the execution tool;
- reuse suitable Gutenberg, Site Editor, theme, builder, plugin, WooCommerce, CPT/ACF, form, and public WordPress capabilities;
- design and refine responsive, accessible, maintainable interfaces, including RTL sites;
- use scoped HTML/CSS/JS or a small custom extension only when the existing stack does not provide a better supported path;
- continue multi-step site work with lightweight persistent Workspace context when the connected runtime supports it;
- keep consequential publication, security, destructive, customer/order, and financial actions behind the appropriate approval boundary.

## Install

Download the latest GitHub Release asset named **`skill.zip`**, then open ChatGPT Skills at **`/skills`** and upload the ZIP as a new Skill.

The packaged Skill contains only the runtime files ChatGPT needs:

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

## Use

Ask naturally. Examples:

- `Design a Persian RTL landing page for this WordPress site.`
- `Improve this Gutenberg page without changing the site's existing visual language.`
- `This site uses Kadence + WooCommerce + ACF. Improve the product/category presentation using the current stack.`
- `Review this page and implement the highest-value safe improvements.`
- `Build this section from the reference screenshot while keeping the existing site architecture.`
- `Resume the WordPress project and continue the next useful task.`

The Skill asks only for material information that cannot be safely inferred or discovered.

## How it chooses an implementation

The Skill separates **site mechanism** from **execution transport**.

```text
REQUEST
  -> understand relevant current site state
  -> identify the owner of the target behavior
  -> reuse a suitable native/theme/builder/plugin/data mechanism
  -> prefer supported public extension surfaces
  -> compare a focused capability/plugin with scoped custom code only when a real gap remains
  -> in connected mode, use an actually exposed ability that safely operates the selected mechanism
```

Preferred defaults such as Astra/Astra Pro, Gutenberg, Gravity Forms, and Code Snippets Pro are fallbacks for unspecified/new projects. They are never migration targets for an existing site.

## Manual mode

The Skill works without a WordPress connector. It can provide exact, stack-aware implementation guidance and code for the architecture supplied in the conversation, including Gutenberg, block themes/Site Editor, existing page builders, WooCommerce, forms, CPT/ACF content models, scoped frontend code, and small WordPress PHP/plugin changes.

## Connected mode

For direct WordPress execution, use the companion [wp-native-builder-bridge](https://github.com/ach1992/wp-native-builder-bridge) with the supported WordPress MCP/Abilities path.

In connected mode the Skill:

1. inspects only state and capabilities relevant to the request;
2. preserves suitable current site ownership and architecture;
3. prefers narrow, reversible, draft/preview changes while iterating;
4. uses current object/version identity for overwrite-sensitive writes;
5. re-reads and reconciles stale or ambiguous state instead of blindly retrying;
6. verifies writes when practical;
7. falls back to useful manual guidance when no safe connected capability exists.

The Skill is not limited to Bridge-owned abilities. Native WordPress, theme, or plugin abilities can be preferred when they are the better supported route.

## Persistent project Workspace

When the connected runtime exposes Workspace abilities, WP Native Builder can keep compact project context in WordPress so a later ChatGPT conversation can recover useful state without depending on the previous conversation.

- **Documents** hold durable project intent, decisions, and reusable project context.
- **Tasks** hold only work that materially benefits from explicit state, dependencies, review, or later continuation.
- **`workspace-resume`** returns compact orientation first; ChatGPT then fetches only relevant document/task details.
- Workspace updates use Workspace-owned optimistic-concurrency identity such as `version + state_hash`.
- Stale writes are rejected; ChatGPT must re-read and reconcile before retrying.
- WordPress Revisions are not required for Workspace continuity or concurrency.
- Live WordPress content/configuration remains authoritative for the current site itself.

Small one-off edits remain lightweight and do not require project-management ceremony.

## Approval and safety model

A technical capability is not the same as user approval, but routine safe writes do not require repetitive confirmation.

The Skill can proceed through safe reads, drafts, previews, reversible edits, validation, and preparation. It asks for approval only at a genuine consequential boundary, such as live publication or a material change to shared/global behavior, security/permissions, customer/order/financial state, data integrity, or difficult-to-reverse state.

An explicit current instruction that already authorizes the exact consequential action and target is not redundantly reconfirmed unless the target, scope, effect, or decision-relevant state materially changes.

## Runtime files

- **`SKILL.md`** — compact runtime control plane and routing rules.
- **`references/design-conventions.md`** — visual, responsive, RTL, accessibility, and presentation guidance.
- **`references/implementation-decisions.md`** — architecture/mechanism guidance across WordPress/theme/builder/plugin/custom-code surfaces.
- **`references/project-workflow.md`** — lightweight workflow for genuinely multi-step WordPress projects.
- **`references/workspace-memory.md`** — persistent Workspace recovery, retention, and optimistic-concurrency rules.
- **`agents/openai.yaml`** — ChatGPT UI metadata.

## Project documentation

Repository documentation is kept separate from the installable Skill runtime:

- [`MASTER-SPEC.md`](MASTER-SPEC.md) — canonical durable product/project specification.
- [`docs/architecture.md`](docs/architecture.md) — concise maintained implementation architecture.
- [`docs/PROJECT-WORKSPACE-ARCHITECTURE.md`](docs/PROJECT-WORKSPACE-ARCHITECTURE.md) — detailed persistent Workspace and cross-chat project architecture.

Implementation and release history belongs to Git/GitHub Issues, Pull Requests, Actions, and Releases rather than being duplicated in these documents.

## Validation and packaging

Releases are produced with OpenAI's standard Skill validation/package workflow. The distributable is named exactly **`skill.zip`** and contains only the six runtime files shown above. Repository documentation and development history are not bundled into the Skill package.

## License

MIT. See [`LICENSE`](LICENSE).