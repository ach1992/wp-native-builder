# WP Native Builder

A compact ChatGPT Skill for professional WordPress site design and implementation with a WordPress-native-first workflow.

The Skill is designed around a typical Astra Pro + Gutenberg workflow while remaining project-aware: explicit site requirements and verified connected-site state override defaults.

## Core approach

```text
WordPress Core / Gutenberg, including Patterns / Synced Patterns when they fit
  -> Astra / Astra Pro
  -> suitable already-installed plugin
  -> scoped custom HTML/CSS/JS
  -> new plugin/custom extension only when justified
```

Custom HTML is supported but is not the default answer. When it is appropriate, logical page sections are returned block-by-block with scoped, maintainable code.

## Default stack

- WordPress
- Astra + Astra Pro
- Gutenberg / Block Editor
- Code Snippets Pro for justified centralized custom code
- Font Awesome 5 Free in the normal stack when established by the project/site profile
- theme-managed fonts
- Gravity Forms
- Astra-native header/footer/global mechanisms where appropriate

These are preferred defaults, not requirements. Explicit project instructions and verified site state take precedence. On an unrelated or unknown site, the Skill does not install or rely on optional stack components merely because they appear in the defaults.

## Install in ChatGPT

On a ChatGPT workspace where Skills and Skill uploads are available:

1. Download the release asset named `skill.zip`.
2. In ChatGPT, open **Plugins -> Skills**.
3. Select **Create -> Upload from your computer** and choose `skill.zip`.
4. Complete ChatGPT's scan/install flow.

After installation, ChatGPT can invoke the Skill automatically for relevant WordPress work, or you can select it explicitly with `@WP Native Builder`.

Current OpenAI installation guidance: [Skills in ChatGPT](https://help.openai.com/en/articles/20001066).

## Use

Ask naturally for WordPress design or implementation work, for example:

- `Design a Persian RTL landing page using my normal Astra/Gutenberg setup.`
- `Build this page with native Gutenberg blocks where possible.`
- `Reuse this CTA across the site and keep every instance synchronized.`
- `Return the custom sections block-by-block for Gutenberg.`
- `Review this page and prioritize the changes I should make.`

The Skill asks only for material context that is missing and cannot be discovered from a connected site.

## Manual and connected modes

**Manual mode requires no bridge.** The Skill can provide exact Gutenberg block structures, native Pattern/Synced Pattern choices, Astra/plugin configuration, and complete scoped Custom HTML/CSS/JS sections when custom code is justified.

For connected work, use the companion [`wp-native-builder-bridge`](https://github.com/ach1992/wp-native-builder-bridge) project. A working bridge connection lets the Skill inspect current site state and use the abilities actually exposed by that site. See the companion repository for its current implementation and setup status.

Bridge permission is not user approval, but ordinary safe reversible writes do not require repeated confirmation. The Skill advances read/draft/preview/reversible work first and asks only at an actual consequential boundary. A current explicit instruction to perform the exact consequential action and target counts as approval, so it is not reconfirmed unless the target, scope, effect, or relevant state materially changes.

## Project map

| Source | Purpose |
|---|---|
| [`MASTER-SPEC.md`](./MASTER-SPEC.md) | Canonical project intent, defaults, decision model, quality requirements, and approval semantics |
| [`SKILL.md`](./SKILL.md) | Compact runtime control plane |
| [`references/`](./references/) | Shallow conditional guidance loaded only when useful |
| [Release v0.1](https://github.com/ach1992/wp-native-builder/releases/tag/v0.1) | First validated public Skill release and `skill.zip` asset |
| [Issue #1](https://github.com/ach1992/wp-native-builder/issues/1) | v0.1 program/outcome |
| [Issue #4](https://github.com/ach1992/wp-native-builder/issues/4) | Packaging and first-release status |
| [`wp-native-builder-bridge`](https://github.com/ach1992/wp-native-builder-bridge) | Optional self-hosted WordPress MCP/Abilities bridge |

## Release model

The distributable Skill contains only `SKILL.md`, `agents/`, and `references/`. Repository-only project documentation such as this README and `MASTER-SPEC.md` is not bundled into `skill.zip`.

For a release, stage those distributable paths under a directory named `wp-native-builder`, run the standard ChatGPT Skill validation/package flow on that directory, and publish the resulting artifact as `skill.zip`. Generated ZIP files are not committed to the source tree.

The project intentionally keeps `SKILL.md` high-signal and uses only shallow references that materially improve model decisions.

## License

This project is licensed under the MIT License. See [`LICENSE`](./LICENSE).

## Current state

`v0.1` remains the latest public release with its validated `skill.zip` artifact and MIT License. The current source includes post-v0.1 runtime refinements for native reuse, connected-write safety, custom-code hardening, stack portability, and lower-friction approval behavior. Manual mode remains independently usable; connected-mode runtime validation remains dependent on the companion bridge implementation.
