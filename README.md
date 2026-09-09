# WP Native Builder

A compact ChatGPT Skill for professional WordPress site design and implementation with a WordPress-native-first workflow.

The Skill is designed around a typical Astra Pro + Gutenberg workflow while remaining project-aware: explicit site requirements and verified connected-site state override defaults.

## Core approach

```text
WordPress Core / Gutenberg
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
- Font Awesome 5 Free already available globally
- theme-managed fonts
- Gravity Forms
- Astra-native header/footer/global mechanisms where appropriate

## Connected mode

The companion [`wp-native-builder-bridge`](https://github.com/ach1992/wp-native-builder-bridge) project provides a free self-hosted WordPress connection so the Skill can inspect and perform supported WordPress operations instead of requiring manual admin work.

Live publishing remains behind explicit user approval even when the bridge technically exposes the operation.

## Project map

| Source | Purpose |
|---|---|
| [`MASTER-SPEC.md`](./MASTER-SPEC.md) | Canonical project intent, defaults, decision model, quality requirements, and completion criteria |
| [Issue #1](https://github.com/ach1992/wp-native-builder/issues/1) | v0.1 program/outcome |
| [Issue #2](https://github.com/ach1992/wp-native-builder/issues/2) | Implement compact Skill core |
| [Issue #3](https://github.com/ach1992/wp-native-builder/issues/3) | Evaluate real workflows and remove model friction |
| [Issue #4](https://github.com/ach1992/wp-native-builder/issues/4) | Package, document, and release v0.1 |
| [`wp-native-builder-bridge`](https://github.com/ach1992/wp-native-builder-bridge) | Companion self-hosted WordPress MCP/Abilities bridge |

## Development path

```text
#2 Skill core
  -> #3 representative evaluation + refinement
  -> #4 validated skill.zip + documentation + release
```

The project intentionally avoids a large instruction corpus. `SKILL.md` should remain a high-signal control plane, with shallow references added only when they materially improve AI decision quality.

## Current state

Project specification and implementation backlog are established. The installable Skill has not been built yet.
