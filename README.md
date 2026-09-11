# WP Native Builder

**WP Native Builder** is a ChatGPT Skill for professional WordPress planning, design, implementation, review, troubleshooting, and durable lightweight project continuity.

It is **stack-adaptive** and **WordPress-native-first**: it works with the site you actually have, establishes enough project truth before substantial builds, and chooses the WordPress/theme/builder/plugin mechanism that should own a change before falling back to custom markup/code.

## What it does

WP Native Builder helps ChatGPT:

- establish one durable Project Foundation before new/substantial multi-step site work, without imposing that ceremony on small edits;
- ask enough material questions even when the user is a WordPress novice, using plain-language staged intake;
- derive architecture/design/content/task artifacts from the foundation and keep the foundation off the routine hot path afterward;
- understand the relevant current WordPress architecture before changing it;
- route global concerns such as headers, footers, templates, navigation, and reusable sections to Site Editor/theme/builder mechanisms when they own them;
- prefer suitable Core blocks, Patterns, theme/builder/plugin features, WooCommerce, CPT/ACF, forms, and public WordPress capabilities before Custom HTML/custom code;
- validate/self-review Gutenberg serialization so block changes are less likely to produce “unexpected or invalid content”;
- design/refine responsive, accessible, maintainable interfaces, including RTL sites, and recommend a better UX/UI path when a requested approach is clearly weak;
- preserve human-readable names and discoverable edit ownership for pages, templates, Patterns, snippets, styles, documents, and tasks;
- continue multi-step site work from durable Workspace context rather than old chat history when the connected runtime supports it;
- tolerate a bounded plausibly transient connector/runtime failure without immediately abandoning the workflow;
- keep consequential publication/security/destructive/customer/order/financial actions behind the applicable approval boundary.

## Install

Download the latest GitHub Release asset named **`skill.zip`**, then open ChatGPT Skills at **`/skills`** and upload the ZIP.

The packaged Skill contains only runtime files:

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

## Use

Ask naturally, for example:

- `Start a new Persian RTL company website and guide me through everything you need before design.`
- `Improve this Gutenberg page without changing the existing visual language.`
- `This site uses Kadence + WooCommerce + ACF. Improve the product/category presentation using the current stack.`
- `Build this section from the reference screenshot, but tell me if the UX should be improved.`
- `Fix this Gutenberg block that says it contains unexpected or invalid content.`
- `Resume the WordPress project and continue the next useful task.`

For a new/substantial multi-step project, the Skill does not begin material design merely because it has enough information to improvise one page. It first resolves the project-level facts that would otherwise cause rework, then derives the architecture/tasks needed to build.

Small bounded edits stay lightweight.

## How it chooses an implementation

```text
REQUEST
  -> recover/discover relevant truth
  -> establish Project Foundation when the project class requires it
  -> identify the current owner of the target behavior
  -> reuse a suitable Core/theme/builder/plugin/data mechanism
  -> prefer supported public/native extension surfaces
  -> compare a focused capability with scoped custom code only when a real gap remains
  -> in connected mode, use an actually exposed ability that safely operates the selected mechanism
  -> self-review/verify before user handoff
```

Preferred defaults such as Astra/Astra Pro, Gutenberg, Gravity Forms, and Code Snippets Pro are fallbacks for unspecified/new projects, never migration targets for an existing suitable stack.

## Project Foundation and continuity

A foundation-required project keeps one canonical durable Project Foundation containing stable project-level intent: purpose, audiences, scope, capabilities, durable constraints, non-goals, and success criteria.

Derived sources own specialized truth such as Site Architecture/Profile, sitemap/IA, design system, content/data model, and active tasks. Once ready, the Foundation is not reread or rewritten for every page/task/chat. A resumed project normally starts from compact current orientation and the nearest current authoritative task/document/live WordPress state.

## Gutenberg safety

For Gutenberg work, the Skill prefers block-aware/native operations and supported Core block/Pattern/template mechanisms. Raw serialized block markup is treated as a serialization contract, not arbitrary HTML.

When raw serialization is unavoidable, the Skill performs every meaningful available structure/parse/serialize/editor/re-read check before user handoff and fixes invalid-block symptoms narrowly rather than flattening a page to Custom HTML by default.

## Manual mode

The Skill works without a WordPress connector. It can provide exact stack-aware implementation guidance for Gutenberg, Site Editor/block themes, existing page builders, WooCommerce, forms, CPT/ACF models, scoped frontend code, and small WordPress PHP/plugin changes.

Without a persistent Workspace, it does not pretend that cross-chat persistence occurred.

## Connected mode

For direct WordPress execution, use the companion [wp-native-builder-bridge](https://github.com/ach1992/wp-native-builder-bridge) with the supported WordPress MCP/Abilities path.

Connected work:

1. inspects only state/capabilities relevant to the request;
2. chooses the site mechanism before the execution transport;
3. prefers narrow reversible/draft/preview changes;
4. uses current object/version identity for overwrite-sensitive writes when supported;
5. re-reads/reconciles stale or ambiguous state;
6. verifies writes when practical;
7. treats one plausible transport failure as a transient route failure until bounded re-discovery/retry evidence says otherwise;
8. falls back to useful manual/preparation work when no safe connected route exists.

The Skill is not limited to Bridge-owned abilities. Native WordPress/theme/plugin abilities may be better transports for the selected mechanism.

## Persistent Workspace

When suitable Workspace abilities are exposed:

- one canonical Project Foundation may hold durable project-level intent;
- derived Documents hold architecture/design/content/other future-useful context;
- Tasks hold only work that benefits from explicit progress/dependency/review/delivery state;
- `workspace-resume` returns compact orientation first;
- ChatGPT fetches only relevant document/task details;
- Workspace writes use Workspace-owned optimistic-concurrency identity such as `version + state_hash`;
- stale writes are rejected and reconciled before retry;
- live WordPress remains authoritative for current site state.

## Approval and safety

The Skill can proceed through safe reads, drafts, previews, reversible edits, validation, and preparation. It asks for approval only at a genuine consequential boundary such as live publication or material shared/global, security, destructive, customer/order/financial, data-integrity, or difficult-to-reverse change.

A current explicit instruction that already authorizes the exact consequential action is not redundantly reconfirmed unless target/scope/effect materially changes.

## Repository documentation

- [`MASTER-SPEC.md`](MASTER-SPEC.md) — canonical durable Skill/product requirements.
- [`docs/architecture.md`](docs/architecture.md) — concise runtime architecture.
- [`docs/PROJECT-WORKSPACE-ARCHITECTURE.md`](docs/PROJECT-WORKSPACE-ARCHITECTURE.md) — persistent Workspace/cross-chat architecture.
- [`docs/BEHAVIOR-EVALS.md`](docs/BEHAVIOR-EVALS.md) — behavioral regression scenarios.

Implementation/release history belongs to Git/GitHub Issues, Pull Requests, Actions, and Releases.

## Validation and packaging

Releases use OpenAI's standard Skill validation/package workflow. The distributable archive is named exactly **`skill.zip`** and contains only the runtime files shown above.

## License

MIT. See [`LICENSE`](LICENSE).
