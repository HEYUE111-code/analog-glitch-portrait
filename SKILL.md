---
name: analog-glitch-portrait
description: Restyle a supplied portrait as an analog damaged-print glitch collage while preserving identity, facial geometry, eye position, mouth structure, and the exact source aspect ratio. Use for portrait edits featuring fine print grain, posterized shadow blocks, source-adaptive collision colors, aligned eye-region panels, grids, scratches, registration marks, and restrained circular arcs.
---

# Analog Glitch Portrait

Transform an existing portrait; do not invent a new person. The result should feel materially reprinted, abraded, misregistered, and editorially reconstructed—not like a clean photo with a filter.

The user does **not** need to provide a prompt beyond the image. Infer the treatment from this skill unless the user specifies overrides.

## Required reading

Before every generation or edit, read [references/style-system.md](references/style-system.md). It is the single source of truth for palette, texture, subject treatment, composition, controls, and QA.

If an eye-region rectangle is requested or selected, also read [references/eye-panel-workflow.md](references/eye-panel-workflow.md). Do not improvise eye-panel geometry.

## Inputs and references

Identify image roles before editing:

- **Source portrait:** identity, pose, expression, crop, clothing, objects, and canvas geometry to preserve.
- **User style reference:** style evidence only; never borrow its identity or composition unless explicitly requested.
- **Bundled structural reference:** [assets/structural-reference-sheet.jpg](assets/structural-reference-sheet.jpg), a four-panel sheet showing collage architecture, grid lines, registration arcs, eye-region framing, layered bands, and spatial rhythm.
- **Bundled surface reference:** [assets/style-reference-05-subject-grain-shadow-blocks.png](assets/style-reference-05-subject-grain-shadow-blocks.png), showing the desired fine print grain, roughened hair/skin/clothing, and posterized shadow masses.

Use the source portrait plus the two bundled reference assets when no adequate user style reference is supplied. If a user supplies better style references, prioritize them and use bundled assets only to fill missing evidence. When tool input limits apply, the bundled contact sheet counts as one reference.

If reference images cannot be passed to the image tool, continue in text-only mode but disclose reduced reference fidelity.

## Non-negotiable invariants

1. **Exact canvas ratio:** preserve source width:height and orientation. Do not crop, pad, stretch, rotate, or convert landscape to portrait. Validate by cross multiplication: `output_width × source_height == output_height × source_width`.
2. **Identity and pose:** preserve head shape, facial proportions, expression, gaze, hairstyle silhouette, body pose, clothing silhouette, and major objects.
3. **Facial source-pixel master:** eyes, eyelids, pupils, irises, brows, nose, lips, jaw, and hairline derive from one spatially aligned source master. Texture and color may change; geometry may not.
4. **Eye core is a strict no-op zone:** no translation, scaling, rotation, mirroring, duplication, repainting, or regeneration of eye anatomy. Eye-panel styling changes only material/color/contrast inside an aligned mask.
5. **Mouth remains integrated:** never isolate, duplicate, panelize, or structurally deconstruct the mouth.
6. **Whole-subject stylization:** skin, hair, clothing, and subject shadows must be visibly transformed. Target at least 65% treated subject area while keeping anatomy legible.
7. **Source-adaptive color:** derive the palette from the source image. Use a controlled collision color related to the source palette; never default to fixed red/blue.
8. **Fine-to-medium print grain:** avoid both clean photographic skin and large chunky particles. Grain diameter should read at roughly `1/20–1/10` of visible iris diameter.

Reject any candidate that violates an invariant, even if its overall style is attractive.

## Workflow

1. Inspect the source at sufficient detail. Record pixel dimensions, exact reduced ratio, orientation, pose, facial landmarks, lighting, dominant colors, shadow regions, and major objects.
2. Read `style-system.md`; read `eye-panel-workflow.md` when relevant.
3. Choose controls from the style system. Default baseline: structural fracture `4/7`, surface wear `3/7`, abstraction `5/7` outside protected features, protected-feature abstraction at most `2/7`.
4. Build a source-derived palette and a pre-edit shadow map. Convert existing face/body/clothing shadows into hard-edged print masses rather than inventing unrelated lighting.
5. Choose eye treatment:
   - use one aligned eye-region frame/panel when a distinctive eye is clearly visible and validation is feasible;
   - otherwise use a frame-only or omitted mode;
   - when exact feature preservation is explicitly required, prefer deterministic source-pixel compositing over generative approximation.
6. Generate or edit with the source portrait and selected style references. Preserve all invariants while applying coarse collage architecture and fine surface damage.
7. Validate in this order: ratio → identity/pose → facial geometry → eye-panel alignment → mouth integration → subject coverage → shadow blocking → grain scale → palette derivation → reference fidelity.
8. If a candidate fails, revise only the first failing layer using the revision ladder in `style-system.md`. Maximum two generative eye-panel attempts; after that switch to deterministic compositing, frame-only, or omitted mode.
9. Save the validated result to an accessible path and report the actual settings used.

## Prompt contract

When composing the image-tool instruction, state these items explicitly:

- identity-preserving edit of the supplied portrait;
- exact original aspect ratio and unchanged composition;
- whole-subject damaged-print treatment with fine-to-medium grain;
- posterized color-block shadows derived from source lighting;
- source-adaptive base, collision, and ghost palettes;
- protected facial geometry and strict eye-core no-op;
- one thin incomplete circular registration arc unless it harms the composition;
- no mouth deconstruction;
- rejection criteria for displaced/duplicated eyes and altered facial features.

Do not ask the generator for generic “glitch art” alone. Describe the materials and structure: damaged offset print, screenprint/risograph buildup, photocopy noise, scraped ink, halftone breakup, hard collage bands, registration lines, and source-derived collision accents.

## Delivery report

Return the selected image and briefly report:

- source and output dimensions plus ratio check;
- references actually used;
- structural-fracture, surface-wear, abstraction, and grain settings;
- palette anchors and derived collision/ghost accents;
- estimated treated-subject coverage and count of major shadow blocks;
- eye-panel mode, attempt count, alignment result, and fallback if used;
- confirmation that eyes, mouth, identity, pose, and facial geometry remained structurally unchanged;
- confirmation that the circular arc was retained or intentionally omitted.

Do not claim success if validation is uncertain. Name the uncertainty and use the safest fallback.
