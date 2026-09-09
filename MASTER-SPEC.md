# WP Native Builder — Master Specification

Status: Canonical project specification
Repository: `ach1992/wp-native-builder`
Companion project: `ach1992/wp-native-builder-bridge`

## 1. Purpose

`wp-native-builder` is a compact, professional ChatGPT Skill for planning, designing, building, reviewing, and refining WordPress sites with a WordPress-native-first workflow.

The Skill exists to remove repeated briefing overhead while helping an AI model make good implementation decisions instead of blindly generating code. It should behave like an experienced WordPress designer/developer who understands the user's normal stack, asks only necessary questions, inspects an available connected site before asking for discoverable facts, chooses the simplest maintainable implementation, and produces polished results.

The Skill is not an autonomous CMS by itself. When `wp-native-builder-bridge` is connected, it may inspect and perform supported WordPress operations through the bridge. Without a connection, it provides exact block-by-block output and actionable WordPress/Astra/Gravity Forms instructions.

## 2. Primary user and default stack

These are defaults, not hard requirements. Current explicit instructions or the actual connected site always override them.

| Area | Default |
|---|---|
| CMS | WordPress |
| Theme | Astra + Astra Pro |
| Editor | Gutenberg / WordPress Block Editor |
| Custom code | Code Snippets Pro when centralized/reusable code is justified |
| Icons | Font Awesome 5 Free already available globally on the frontend |
| Fonts | Loaded/configured by the theme/site; custom components inherit typography |
| Forms | Gravity Forms |
| Header/footer/global insertion | Prefer Astra-native facilities/hooks when appropriate |
| New-site permalinks | Post name |
| Page construction | Native blocks first; Custom HTML blocks when they are the better implementation |
| Custom HTML output | Logical sections separated block-by-block |

Do not enqueue another Font Awesome build or external font by default.

## 3. Decision precedence

Resolve conflicts in this order:

1. Explicit instruction in the current request.
2. Current project/site profile supplied by the user.
3. Verified state of the connected WordPress site.
4. This Skill's defaults.

Never change an existing site's global configuration merely to make it match a Skill default.

## 4. Core operating principle

Choose the simplest maintainable implementation that achieves the requested result.

```text
Can WordPress Core/Gutenberg do it cleanly?
  -> yes: use Core/Gutenberg
  -> no: can Astra/Astra Pro do it cleanly?
       -> yes: use Astra
       -> no: can an already-installed suitable plugin do it cleanly?
            -> yes: use that plugin
            -> no: can bounded HTML/CSS/JS solve it cleanly?
                 -> yes: use custom code with minimal scope
                 -> no: propose the smallest justified plugin/custom extension
```

Do not use Custom HTML merely because it is available. Do not install another plugin merely because it can do something WordPress, Astra, Gravity Forms, or a small scoped implementation can already do well.

## 5. Interaction modes

| Mode | Expected behavior |
|---|---|
| Plan/design | Clarify only material unknowns, propose page/section structure, then produce the implementation path |
| Manual build | Give exact Gutenberg/Astra/plugin steps or complete block-by-block code, whichever is the better implementation |
| Connected build | Inspect first, implement supported reversible changes through the bridge, and summarize what changed |
| Modify | Read the current implementation when possible and make the smallest safe targeted change |
| Review | Evaluate visual quality, responsiveness, accessibility, performance, maintainability, security, and WordPress fit |
| Site-level feature | Prefer global/native mechanisms instead of duplicating page-level markup across the site |

## 6. Questions and site profile

Ask questions only when the answer can materially change the design or implementation and cannot be discovered from a connected site.

Typical project-specific inputs may include:

- site purpose and audience;
- language and RTL/LTR direction;
- visual direction and brand personality;
- colors and existing design tokens;
- full-width/boxed/container expectations;
- page goal, content, CTA, and required sections;
- reference sites or visual examples when relevant;
- project-specific plugin or compatibility constraints.

Do not repeatedly ask for defaults already defined here. Do not ask for connected-site facts that can be inspected safely.

## 7. Design-quality standard

The Skill should produce work that looks intentional and professionally designed, not template-like or mechanically generated.

For every applicable design, reason about:

| Dimension | Expected result |
|---|---|
| Visual hierarchy | Clear primary/secondary emphasis, useful whitespace, controlled density |
| Layout | Coherent grid, alignment, spacing rhythm, sensible container behavior |
| Typography | Theme-aware, readable, correct hierarchy, no unsupported font-weight assumptions |
| Color | Consistent palette, sufficient contrast, restrained accents |
| Responsiveness | Desktop/tablet/mobile behavior designed intentionally, not only patched at one breakpoint |
| Accessibility | Semantic elements, heading order, keyboard/focus states, meaningful alt text, appropriate ARIA, reduced motion |
| Performance | Avoid unnecessary assets/dependencies; treat hero/LCP imagery carefully; lazy-load only where appropriate |
| Maintainability | Independent logical sections, scoped code, reusable global rules only when genuinely shared |
| Security | No unsafe inline/server behavior; use WordPress/plugin APIs and safe defaults |
| Creativity | Fit the site's subject and audience; avoid repetitive generic AI layouts |

Do not turn this table into a ritual checklist in user-facing answers. Apply only the concerns that matter to the current work.

## 8. Gutenberg and Custom HTML conventions

### Native blocks

Prefer native Gutenberg structures when they remain easy to edit and accurately achieve the design. When manual execution is needed, provide the exact block hierarchy and the important settings to apply.

### Custom HTML

When Custom HTML is justified:

- one logical page section should normally be one Gutenberg Custom HTML block;
- keep sections independently editable;
- use a unique section ID and site/project prefix;
- scope CSS to that section;
- use semantic HTML;
- keep JavaScript out unless it is truly needed;
- prefer native HTML behavior before JavaScript;
- centralize genuinely shared/reusable styles or scripts instead of duplicating them across many blocks;
- avoid global selectors and unnecessary `!important`;
- inherit site typography unless the project explicitly requires otherwise;
- use only Font Awesome 5 Free icons when relying on the default globally available icon set;
- include responsive and reduced-motion behavior when applicable.

Self-contained is the default for one-off sections, not a requirement to duplicate common code everywhere.

## 9. WordPress-native feature rules

- Use Gravity Forms for forms by default when available instead of hand-building forms.
- Prefer Astra facilities for suitable header/footer/global placement work.
- Prefer WordPress Media Library for site media.
- Prefer WordPress revisions and normal content APIs for content changes.
- Do not edit WordPress core, Astra, or third-party plugin files directly.
- Do not place routine custom PHP in a theme's `functions.php` when Code Snippets Pro or a small purpose-built plugin is the safer maintainable location.
- Do not change permalink structure on an existing site without explicit instruction and impact review.

## 10. Connected-site behavior

The companion `wp-native-builder-bridge` project provides machine-readable WordPress abilities through the WordPress Abilities API and official MCP Adapter.

When connected:

1. inspect relevant site state before proposing or applying a change;
2. reuse the current stack and conventions where they remain fit;
3. make narrow reversible edits instead of replacing unrelated content;
4. use current revision/identity data for overwrite-sensitive updates;
5. prefer draft/preview/reversible work while iterating;
6. summarize the exact objects/sections changed and any remaining manual or approval step.

### Publishing and consequential changes

The user requires explicit approval before publishing live changes.

Before live publishing or another materially consequential/global/destructive action, stop at the approval boundary and state the exact pending action and its material impact. Do not treat permission exposed by the bridge as user approval.

## 11. Skill implementation requirements

The Skill itself must remain small and high-signal.

- Keep `SKILL.md` as the control plane, not a knowledge dump.
- Use short decision tables/trees only when they materially improve model choice or precision.
- Move detailed conventions/reference material into shallow `references/` files only when needed.
- Avoid duplicated instructions and repeated generic web-design advice.
- Prefer imperative, decision-oriented language.
- Preserve model autonomy for ordinary reversible choices; do not force unnecessary questions or ceremony.
- Do not encode one site's colors, URLs, content, IDs, or brand values as global defaults.
- Do not depend on WPVibe or another paid/SaaS WordPress bridge.
- When current external API/plugin behavior matters, verify authoritative current documentation rather than relying on stale assumptions.

Expected initial layout:

```text
wp-native-builder/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── site-profile.md
    ├── implementation-decisions.md
    └── design-conventions.md
```

Only retain reference files that prove useful during implementation/evaluation.

## 12. Representative use cases

The Skill must handle at least these patterns well:

1. "Design this landing page in Persian/RTL using my normal WordPress setup."
2. "Create a professional hero and three feature sections; use native blocks where that is cleaner."
3. "Here is the content; return the custom parts block-by-block for Gutenberg."
4. "Connect to the site, inspect this page, and improve the section without changing unrelated blocks."
5. "Build a contact/application form" -> prefer Gravity Forms when available.
6. "Add a site-wide announcement/header/footer element" -> prefer the appropriate global/native mechanism.
7. "Review this page" -> provide prioritized, implementation-aware design/UX/accessibility/performance findings.
8. "Publish the changes" -> require explicit approval immediately before the live action.

## 13. Non-goals

- Becoming a general-purpose WordPress administration Skill unrelated to site building.
- Requiring Astra when a project explicitly uses another compatible theme.
- Forcing Custom HTML for every section.
- Recreating functionality already provided cleanly by WordPress or installed plugins.
- Depending on proprietary WordPress AI services.
- Creating excessive process, output boilerplate, or repeated checklists that slow the model.

## 14. Success criteria

The project is complete for the first usable release when:

- a valid packaged ChatGPT Skill exists and can be installed;
- common Astra/Gutenberg design requests require materially less repeated briefing;
- the Skill consistently chooses native vs Astra vs installed-plugin vs custom-code paths sensibly;
- manual code output is clean, scoped, responsive, accessible, and block-by-block when custom blocks are appropriate;
- connected mode can correctly use the bridge's supported abilities without embedding bridge implementation details in every prompt;
- publish/live changes remain behind explicit user approval;
- representative evaluation scenarios pass without unnecessary questions, excessive verbosity, or decision friction;
- installation/use documentation is concise and reproducible.

## 15. Delivery

Initial delivery target: a validated `skill.zip` generated from this repository, with the repository itself remaining the source of truth for future revisions.

The implementation should move quickly: build the smallest correct Skill, evaluate it on representative tasks, remove friction, package it, and iterate from real usage rather than pre-building a large framework.
