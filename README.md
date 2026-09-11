# WP Native Builder

**WP Native Builder** is a ChatGPT Skill for professional WordPress planning, design, implementation, review, troubleshooting, and lightweight project continuity.

It is **stack-adaptive** and **WordPress-native-first**: it works with the site you actually have, establishes enough project truth before substantial builds, and decides which WordPress/theme/builder/plugin/data mechanism should own a change before falling back to custom markup/code.

## What it does

WP Native Builder helps ChatGPT:

- keep small bounded edits fast while establishing one Project Foundation for substantial multi-step site work;
- ask novice-friendly staged questions until material project gaps are actually resolved;
- reuse canonical project artifacts instead of creating duplicate “master” documents;
- understand the relevant current WordPress architecture before changing it;
- route headers, footers, templates, navigation, and reusable/global surfaces to their real Site Editor/theme/builder owner;
- prefer suitable Core blocks, Patterns, theme/builder/plugin features, WooCommerce presentation, forms, CPT/ACF, and public WordPress capabilities before Custom HTML/custom code;
- treat Gutenberg markup as a serialization contract and repair invalid blocks narrowly;
- review material UI for hierarchy, responsive behavior, RTL/LTR, accessibility, performance, and maintainability;
- perform static self-review even without a renderer, then add preview/editor/parser/live checks when available;
- preserve human-readable names and discoverable edit ownership;
- resume multi-step work from persistent Workspace context when the runtime supports it;
- avoid duplicate Workspace canonical documents through discover/reuse-before-create behavior;
- reconcile stale/ambiguous Workspace writes instead of overwriting newer state;
- tolerate one plausibly transient connector/runtime failure without immediately abandoning the workflow;
- keep genuine consequential publication/security/destructive/customer/order/financial actions behind the applicable approval boundary.

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

A new/substantial multi-step project resolves durable project-level facts before material design. Small bounded edits stay lightweight.

## Runtime model

Routing is additive: one request may need project-workflow, ownership, Gutenberg, design, and Workspace rules at the same time. `SKILL.md` routes those domains while the direct references own their detailed policy.

```text
REQUEST
  -> recover/discover relevant truth
  -> establish Project Foundation when required
  -> choose owner/mechanism
  -> choose an actually exposed execution transport
  -> build narrowly
  -> static self-review
  -> add preview/editor/parser/live review when available
  -> user review/publish only when applicable and authorized
  -> verify
  -> reconcile future-useful project state
```

Preferred defaults such as Astra/Astra Pro, Gutenberg, Gravity Forms, and Code Snippets Pro are fallbacks for unspecified/new projects, never migration targets for an existing suitable stack.

## Project Foundation and canonical artifacts

A foundation-required project keeps one canonical Project Foundation containing stable project-level intent. When the Skill creates related artifacts, the canonical default names are:

- `Project Foundation`
- `Site Architecture Profile`
- `Information Architecture`
- `Design Direction`
- `Content/Data Model`

Existing equivalent artifacts are reused rather than duplicated merely to match those names.

Once ready, Project Foundation leaves the routine hot path. Current work normally uses the nearest authoritative task/document/live WordPress state.

## Gutenberg safety

For Gutenberg work, block-aware/native operations and supported Core block/Pattern/template mechanisms are preferred. Raw serialized block markup is treated as a serialization contract, not arbitrary HTML.

When raw serialization is unavoidable, the Skill performs every meaningful available structure/parse/serialize/editor/re-read check before claiming validation and fixes invalid-block symptoms at the smallest affected representation.

## Manual mode

The Skill works without a WordPress connector and provides exact stack-aware implementation guidance. Without a persistent Workspace or another durable project location, it does not claim cross-chat persistence.

## Connected mode

For direct WordPress execution, use a compatible WordPress MCP/Abilities path. The companion [wp-native-builder-bridge](https://github.com/ach1992/wp-native-builder-bridge) can provide the current Builder/Workspace surfaces.

Connected work:

1. inspects only relevant current architecture, targets, and capabilities;
2. chooses site mechanism before execution transport;
3. prefers narrow reversible/draft/preview changes while iterating;
4. guards overwrite-sensitive writes with current identity when supported;
5. re-reads/reconciles stale or ambiguous state;
6. verifies writes when practical;
7. treats one plausible transport failure as transient until bounded evidence says otherwise;
8. falls back to useful manual/preparation work when no safe connected route exists.

The Skill is not limited to Bridge-owned abilities. Native WordPress/theme/plugin abilities may be better transports for the selected mechanism.

## Persistent Workspace

When suitable Workspace abilities are exposed:

- compact orientation comes before broad reload;
- canonical singleton documents are discovered/reused before create;
- stable purpose keys may be used when the capability supports them, without assuming storage-level uniqueness;
- Tasks keep independent progress/review/delivery dimensions;
- Workspace writes use Workspace-owned optimistic-concurrency identity such as `version + state_hash`;
- stale writes are rejected and reconciled before retry;
- live WordPress remains authoritative for current site state.

## Approval and safety

The Skill proceeds through safe reads, drafts, previews, reversible edits, validation, and preparation without repetitive confirmation. Genuine consequential actions are authorized only by the applicable current user instruction/approval boundary.

A current exact instruction is not redundantly reconfirmed while target/scope/material effect remain unchanged.

## Repository documentation

- [`MASTER-SPEC.md`](MASTER-SPEC.md) — canonical product requirements for the Skill itself.
- [`docs/architecture.md`](docs/architecture.md) — concise runtime/rule ownership architecture.
- [`docs/PROJECT-WORKSPACE-ARCHITECTURE.md`](docs/PROJECT-WORKSPACE-ARCHITECTURE.md) — persistent Workspace/cross-chat architecture.
- [`docs/BEHAVIOR-EVALS.md`](docs/BEHAVIOR-EVALS.md) — behavioral regression scenarios.

Implementation/release history belongs to Git/GitHub Issues, Pull Requests, and Releases.

## Validation and packaging

Releases use OpenAI's standard Skill validation/package workflow. The public archive is named exactly **`skill.zip`** and must correspond to the tagged/integrated runtime revision.

## License

MIT. See [`LICENSE`](LICENSE).
