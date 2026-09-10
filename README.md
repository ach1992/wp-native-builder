# WP Native Builder

A compact ChatGPT Skill for professional, stack-adaptive WordPress site design and implementation with a WordPress-native-first workflow.

The owner's common Astra Pro + Gutenberg + Gravity Forms environment remains a preferred default, but **default stack does not mean only supported stack**. The Skill adapts to the actual site's theme, editor/builder, plugins, content/data model, WooCommerce workload, and capabilities when those are known or discoverable.

## Core approach

```text
REQUEST
  -> understand the relevant current site architecture/capabilities
  -> reuse the site's existing suitable mechanism
  -> prefer WordPress-native/public/supported surfaces
  -> prefer suitable current theme/builder/plugin capabilities
  -> in connected mode, use an exposed ability that safely operates the chosen mechanism
  -> use scoped custom HTML/CSS/JS for genuine gaps
  -> add a custom extension/plugin only when justified
```

The Skill does not convert an Elementor/Kadence/block-theme/WooCommerce/ACF/etc. site toward Astra/Gutenberg/Gravity Forms merely because those are preferred defaults.

## Preferred default stack

- WordPress
- Astra + Astra Pro
- Gutenberg / Block Editor
- Code Snippets Pro for justified centralized custom code
- Font Awesome 5 Free when established by the current project/site profile
- theme-managed fonts
- Gravity Forms
- Astra-native header/footer/global mechanisms when appropriate

These are fallback/preferred defaults, not requirements. Explicit project instructions, supplied site architecture, and verified connected state take precedence.

## Supported architecture model

The core Skill stays general rather than bundling a large plugin/theme encyclopedia. It can adapt to, for example:

- block themes / Site Editor;
- other themes and existing page builders;
- WooCommerce;
- forms, ACF/custom post types, multilingual/SEO/performance plugins;
- current/future WordPress, theme, and plugin public APIs/Abilities.

Plugin/theme-specific references are added only if real repeated workflows prove they improve reliability enough to justify their context and maintenance cost.

## Install in ChatGPT

On a ChatGPT workspace where Skills and Skill uploads are available:

1. Download a release asset named `skill.zip` or use a validated package generated from current source.
2. In ChatGPT, open **Plugins -> Skills**.
3. Select **Create -> Upload from your computer** and choose `skill.zip`.
4. Complete ChatGPT's scan/install flow.

After installation, ChatGPT can invoke the Skill automatically for relevant WordPress work, or you can select it explicitly with `@WP Native Builder`.

Current OpenAI installation guidance: [Skills in ChatGPT](https://help.openai.com/en/articles/20001066).

## Use

Ask naturally, for example:

- `Design a Persian RTL landing page using my normal Astra/Gutenberg setup.`
- `This site uses a block theme; improve the global header without rebuilding the architecture.`
- `This WooCommerce + Kadence + ACF site needs a better product/category presentation.`
- `This page is built with Elementor; improve the section without converting it to Gutenberg.`
- `Reuse the site's existing form plugin for this application form.`
- `Review this page and prioritize the changes I should make.`

The Skill asks only for material context that is missing and cannot be discovered safely.

## Manual and connected modes

**Manual mode requires no bridge.** The Skill provides stack-aware instructions/output for the actual editor/theme/plugins supplied in context, with the preferred defaults used only when applicable.

For connected work, use the companion [`wp-native-builder-bridge`](https://github.com/ach1992/wp-native-builder-bridge). Connected mode inspects relevant architecture and uses capabilities actually exposed by the current runtime. It is not limited to custom Bridge-owned abilities: suitable native/plugin/theme Abilities may be preferred when they expose a better supported route.

Bridge/plugin permission is not user approval, but safe reversible work does not require repeated confirmation. The Skill advances read/draft/preview/reversible work first and asks only at an actual consequential boundary. Exact current instructions for the same consequential action/target count as approval unless material state/scope/effect changes.

WooCommerce design/content/presentation is normal supported site-building work when present. Refunds, payment operations, destructive order actions, and consequential customer/order mutations are not silently inferred from ordinary design requests and remain permission/approval-sensitive when applicable.

## Accepted persistent Workspace direction

Post-v0.1 development now has an accepted architecture for **cross-chat site-project continuity** and a lightweight end-to-end site workflow. This is a development target, not a claim about the currently released `v0.1` package.

When the companion WordPress runtime later exposes the accepted Workspace contract, WP Native Builder should be able to recover a compact project orientation from WordPress, load only relevant durable documents/tasks, verify current live site state, and continue the next useful action without requiring the previous chat history.

The Workspace is intentionally not a chat log or second CMS. It is for durable project intent, accepted decisions, unresolved progress, and only the tasks/documents that materially improve continuation. Live WordPress remains authoritative for current site content/configuration.

For material visual work, the accepted workflow supports draft/preview -> AI self-review -> user visual review -> revision/approval -> publication -> live verification when appropriate. Small one-off edits remain lightweight and should not create unnecessary project-management ceremony.

See [`docs/PROJECT-WORKSPACE-ARCHITECTURE.md`](./docs/PROJECT-WORKSPACE-ARCHITECTURE.md) for the complete accepted architecture and [Issue #13](https://github.com/ach1992/wp-native-builder/issues/13) for the active post-v0.1 program.

## Project map

| Source | Purpose |
|---|---|
| [`MASTER-SPEC.md`](./MASTER-SPEC.md) | Canonical project intent, stack-adaptive architecture, defaults, decision/approval behavior, and durable Workspace/project-lifecycle requirements |
| [`docs/PROJECT-WORKSPACE-ARCHITECTURE.md`](./docs/PROJECT-WORKSPACE-ARCHITECTURE.md) | Detailed accepted architecture for persistent Workspace memory, recovery, lightweight tasks/documents, visual review, launch flow, and the logical companion-Bridge contract |
| [`SKILL.md`](./SKILL.md) | Compact runtime control plane for behavior already implemented in current source |
| [`references/`](./references/) | Shallow conditional runtime guidance loaded only when useful |
| [Post-v0.1 Workspace program #13](https://github.com/ach1992/wp-native-builder/issues/13) | Current durable work/dependency/evaluation plan for implementing the accepted Workspace and full-site workflow |
| [Release v0.1](https://github.com/ach1992/wp-native-builder/releases/tag/v0.1) | First validated public Skill release |
| [`wp-native-builder-bridge`](https://github.com/ach1992/wp-native-builder-bridge) | Optional self-hosted WordPress MCP/Abilities bridge; its concrete Workspace implementation remains owned by that repository |

## Release model

The distributable Skill contains only `SKILL.md`, `agents/`, and `references/`. Repository-only project documentation such as this README, `MASTER-SPEC.md`, and `docs/` architecture files is not bundled into `skill.zip` unless a future accepted runtime design explicitly moves needed guidance into `references/`.

For a package/release, stage distributable paths under a directory named `wp-native-builder`, run the standard ChatGPT Skill validation/package flow, and use the resulting file named exactly `skill.zip`. Generated ZIP files are not committed to the source tree.

## License

This project is licensed under the MIT License. See [`LICENSE`](./LICENSE).

## Current state

`v0.1` remains the latest public release. Current source already includes post-v0.1 refinements for lower-friction approval behavior, native reuse, connected-write safety, custom-code hardening, stack-adaptive architecture, and stronger design-intent/question behavior.

The persistent Workspace, cross-chat recovery, lightweight project-task/document workflow, visual owner-review lifecycle, and complete-site continuation model are now **accepted and documented development requirements** under Issue #13, but are not yet claimed as implemented runtime functionality. Connected end-to-end Workspace validation additionally depends on the companion `wp-native-builder-bridge` later implementing the accepted Workspace capability contract in its own repository.
