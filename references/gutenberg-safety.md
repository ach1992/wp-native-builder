# Gutenberg Serialization and Block Safety

Load this reference whenever work creates or modifies Gutenberg/Core blocks, Patterns, template block markup, raw `post_content`, serialized block comments, or investigates “This block contains unexpected or invalid content.”

## Why invalid blocks happen

For static/hybrid blocks, the Block Editor parses attributes from stored content and regenerates the block's expected saved markup. If regenerated markup does not match the stored markup, WordPress can mark the block invalid. External/manual HTML edits inside a block are a common cause.

Treat block markup as a serialization contract, not generic HTML with decorative comments.

## 1. Preferred write paths

Use this order:

1. block-aware/native editor or connected block operation that creates/updates block attributes/content using the registered block model;
2. supported WordPress/theme/builder Pattern/template operation;
3. carefully generated serialized block markup only when no safer block-aware route exists and the exact current block format is known;
4. `core/html`/Custom HTML for intentionally freeform markup when Custom HTML is actually the correct mechanism.

Do not hand-edit the saved HTML of a static Core/plugin block as though it were arbitrary HTML.

## 2. Native mechanism before raw serialization

Before emitting raw Gutenberg markup:

- confirm the target is genuinely Gutenberg-owned;
- confirm the intended block type is registered/available in the current site/runtime when that can be inspected;
- prefer Core block settings/supports and nested Core blocks over injecting unsupported wrapper attributes/children;
- use Pattern/Synced Pattern/template mechanisms for reuse/global concerns;
- choose another mechanism if the desired structure requires HTML that the block's serialization does not support.

## 3. Raw block markup rules

If raw serialized markup is unavoidable:

- use valid `<!-- wp:block-name ... -->` / closing delimiter structure for the current block;
- keep attributes and inner HTML consistent with the registered/current block format;
- do not add/remove wrapper elements/classes/attributes that the block's saved output would not reproduce;
- preserve required `wp-block-*` wrapper classes and support-generated classes when applicable;
- keep nested block delimiters structurally balanced;
- do not mix unrelated arbitrary HTML into a Core block's saved markup unless that block's schema/save output supports it;
- treat third-party/custom block serialization as version-sensitive; inspect current block behavior/docs rather than guessing.

Dynamic blocks that store only delimiters/attributes have different serialization behavior; do not invent front-end HTML in their stored placeholder unless the current block contract requires it.

## 4. Safe modification strategy

When existing content is already valid:

- mutate the smallest target block/attribute set;
- avoid reserializing unrelated blocks from scratch;
- preserve existing unknown/plugin block content unless the task requires changing it;
- re-read current `post_content` before overwrite-sensitive raw-content writes;
- on concurrent/stale change, reconcile instead of overwriting.

## 5. Mandatory pre-user self-review for block changes

Before telling the user a Gutenberg block change is ready, perform every available relevant check:

1. **Ownership check:** confirm Gutenberg/raw serialization was actually the right mechanism.
2. **Structure check:** block comments are balanced/nested and expected block types are available.
3. **Serialization check:** when the runtime exposes a block-aware parse/serialize/validation/editor-preview route, use it and resolve any invalid-block warning before user review.
4. **Round-trip check:** if a supported parser/serializer is available, parse and reserialize and compare the affected block structure; investigate material drift rather than accepting it blindly.
5. **Editor check:** when visual/editor preview is available, open/render the edited content and look specifically for invalid/recovery prompts or console-reported block validation differences.
6. **Re-read check:** verify stored content after write when practical.
7. **Visual/functional check:** confirm the intended result still works responsively and no unrelated blocks changed.

Do not claim “validated” if the runtime did not expose a meaningful validation path. In that case, minimize raw serialization and explicitly preserve a safer native/editor route for final application.

## 6. If an invalid-block symptom appears

Diagnose before rewriting everything:

1. identify the exact invalid block type and affected saved markup;
2. inspect browser/editor validation output when available for expected-versus-actual difference;
3. determine whether the cause is manual/external markup change, stale block/plugin version, attribute type/source mismatch, unsupported wrapper/class/style change, or changed block save behavior;
4. preserve user content;
5. restore the smallest valid representation using the current block contract, a supported recovery/conversion path, or a more suitable mechanism;
6. re-open/revalidate the block before user handoff.

Do not “fix” invalid blocks by flattening an entire page to Custom HTML unless the user explicitly wants that ownership change and it is the better long-term mechanism.

## 7. Custom HTML boundary

`core/html` is appropriate for intentionally freeform markup, not as an escape hatch from understanding Gutenberg ownership.

Use it only when:

- the design/behavior cannot be represented cleanly with existing native/theme/builder/plugin blocks;
- page-local freeform markup is maintainable for the actual project;
- the section is properly scoped, accessible, responsive, and does not duplicate a global/reusable owner.

For reusable or lifecycle-heavy behavior, prefer a Pattern, supported block/plugin, or small purpose-built extension instead.
