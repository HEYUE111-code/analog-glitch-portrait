# Analog Glitch Portrait Style System

This file is the canonical style specification. `SKILL.md` defines execution order; this file defines visual decisions and acceptance thresholds.

## 1. Target aesthetic

Aim for a portrait rebuilt as a damaged analog print collage:

- large structural regions: bands, plates, voids, crop windows, interrupted grids;
- material surface: offset/screenprint buildup, photocopy grit, abraded ink, halftone breakup, paper tooth, registration drift;
- subject treatment: roughened skin, hair, clothing, and objects; stylized shadows; reduced tonal continuity;
- facial legibility: identity remains recognizable and landmark geometry stays registered;
- editorial restraint: one or two strong interventions, not a pile of unrelated effects.

Avoid these false friends:

- clean photography plus a transparent texture overlay;
- generic retro poster, pop-art duotone, comic-book filter, neon cyberpunk, RGB split, VHS scanlines, HUD graphics;
- fixed red/blue color schemes unrelated to the source;
- beauty retouching, porcelain skin, smooth gradients, photoreal hair strands;
- uniformly distressed noise with no hierarchy;
- displaced, duplicated, mirrored, or redrawn facial features.

## 2. Reference roles

### Structural reference sheet

`assets/structural-reference-sheet.jpg` contains four original references in a single tool-efficient contact sheet. Read it for:

- grid and registration systems;
- eye-region rectangles that stay spatially aligned;
- broad collage plates and horizontal/vertical bands;
- sparse circular arcs;
- asymmetric negative space and interrupted framing.

Do not copy the contact-sheet gutters or panel layout into the output. It is style evidence, not a composition template.

### Subject-surface reference

`assets/style-reference-05-subject-grain-shadow-blocks.png` is the primary surface target. Read it for:

- fine, dense print grain on skin rather than large particles;
- hair compressed into ink-like directional masses;
- skin and clothing shadows converted into hard-edged color blocks;
- partial tonal retention around nose, lips, and jaw without restoring smooth photographic realism;
- dense subject stylization that still preserves identity.

## 3. Control model

Use three independent controls. Do not use one vague “glitch intensity” value.

| Control | Meaning | Default | Protected face |
|---|---|---:|---:|
| Structural fracture | plates, bands, voids, grids, arc, collage boundaries | 4/7 | may cross but must not move features |
| Surface wear | grain, halftone, abrasion, scratches, ink loss | 3/7 | fine-to-medium only |
| Subject abstraction | posterized shadow masses, tonal compression, hair/clothing simplification | 5/7 | max 2/7 for eyes/nose/lips geometry |

If the result is too photographic, raise **subject abstraction** first. If the composition is too clean, raise **structural fracture**. If the materials feel digital or smooth, raise **surface wear** without enlarging grain.

## 4. Exact canvas preservation

- Read source pixel dimensions before editing.
- Preserve the exact reduced aspect ratio and original orientation.
- Never satisfy a model limitation by cropping or padding the finished result.
- Validate with cross multiplication, not rounded decimals.
- If the image tool cannot emit the exact ratio, choose a mathematically equivalent supported size. Reject any non-equivalent result.

## 5. Subject construction

### Source-pixel master

Treat the source portrait as the only geometry master. All facial landmarks, hairline, pose, garment edges, hands, and major objects remain registered to it. A style pass may change color, contrast, texture, and edge quality; it may not invent new anatomy.

### Skin

- Replace smooth photographic microtexture with fine stipple/halftone/photocopy grain.
- Compress midtones into a limited number of printed value bands.
- Keep the nose, lips, jaw, and expression recognizable through value boundaries, not high-resolution skin detail.
- Permit controlled ink dropout and speckling, but no crater-like pores or chunky sand texture.

### Hair

- Preserve silhouette and parting.
- Consolidate visible hair into roughly 3–7 directional ink masses.
- Retain only enough strand information to describe flow; avoid glossy photoreal individual strands.
- Use dry-brush breakup and small registration accents at edges, not reshaped hair.

### Clothing and objects

- Apply the same print logic to clothing, instruments, and accessories.
- Simplify folds and cast shadows into broad graphic masses while preserving object geometry and functional details.
- Do not leave the torso as a clean photo beneath a stylized face.

### Coverage target

At least 65% of visible subject area should show one or more of: tonal posterization, fine grain, halftone breakup, ink abrasion, hard-edged shadow blocks, registration tinting, or print dropout. Decorative lines alone do not count.

## 6. Shadow stylization

Build a shadow map from the source before stylizing. Identify at minimum:

- eye socket/brow or hair-cast shadow;
- cheek/nose/jaw shadow;
- neck shadow;
- clothing fold, arm, or object shadow.

Convert at least three major source shadows into hard or lightly eroded print-color masses. Their shapes must follow the source lighting and anatomy. Use clipped, posterized, or screened transitions rather than smooth airbrushed gradients.

Do not place arbitrary color blocks on lit skin merely to increase glitch intensity.

## 7. Grain and material scale

Default subject grain is **fine-to-medium**:

- typical visible particle diameter: about `1/20–1/10` of visible iris diameter;
- mostly dense micro-speckle with sparse slightly larger abrasion marks;
- grain follows print density: darker ink masses may be more solid; midtones show stipple; highlights may show paper tooth/dropout;
- facial grain must not erase eye contours, nostrils, lip boundary, or jaw registration.

Reject oversized pebble, sand, gravel, foam, crystalline, or chunky confetti textures. Large marks may appear only as isolated scratches or plate losses away from facial landmarks.

## 8. Source-adaptive palette

Never start from named fixed colors. Sample the source first.

### Derivation

1. Choose 2–4 **anchors** from dominant source hues and important subject colors.
2. Create darker and lighter **endpoints** from those anchors by shifting value and saturation, not by introducing unrelated hues.
3. Derive one **collision accent** from the dominant source hue:
   - start near the opposite side of the hue wheel (`+150° to +210°`);
   - then bias it `20°–45°` away from a mathematically exact complement so it feels print-like rather than digitally perfect;
   - tune saturation/value for separation from skin and clothing.
4. Derive a weaker **ghost accent** from an anchor or collision hue, shifted about `25°–60°`, used for registration echoes and small marks.

### Proportions

- source-family anchors and neutrals: dominant field;
- collision accent: about 8–18% of image area;
- ghost accent: about 1–5%;
- black/paper tones may structure the image but must respond to source luminance.

The collision accent must differ clearly from the source while still being derived from it. Blue sources need not produce red; warm sources need not produce blue. Judge relationship, not a fixed pair.

Apply strong collision color mainly to shadow blocks, background plates, registration errors, and non-feature accents. On protected facial features use only aligned tint/value transforms.

## 9. Collage architecture

Select one primary architecture and one secondary device.

### Primary architectures

- **Plate field:** one dominant printed field plus a contrasting plate or void.
- **Band fracture:** one or two broad horizontal/vertical bands reorganize the frame without moving the subject.
- **Windowed face:** an aligned eye-region window changes material while the face remains continuous.
- **Offset ground:** background planes shift or collide around a stable subject.

### Secondary devices

- thin grid or crop marks;
- one incomplete circular registration arc;
- sparse microtype or measurement ticks;
- small edge abrasions and registration ghosts.

Default to one thin incomplete circle/arc. It may intersect hair, background, or the aligned eye frame, but should not become a target symbol, halo, or HUD. Omit it only when it competes with the face or composition.

Keep negative space. Do not fill every region with texture.

## 10. Eye-region rectangle

Use the eye rectangle as a material window, not a displaced collage fragment. Its boundary may be crisp, abraded, or outlined; its interior may change tint, print density, halftone, or contrast. The eye anatomy under it must remain on the source coordinates.

All mode selection, deterministic compositing, validation, and fallbacks are defined in `eye-panel-workflow.md`.

Never create a mouth rectangle.

## 11. Prompt language

Prefer concrete material and structural terms:

- “damaged offset print,” “screenprint/risograph buildup,” “photocopy grit,” “abraded ink,” “paper tooth,” “halftone breakup,” “hard-edged shadow plates,” “registration arc,” “aligned eye-region material window.”

Always pair style language with preservation language:

- “identity-preserving edit,” “source-pixel facial master,” “strict eye-core no-op,” “same pose/crop,” “exact source ratio,” “no feature displacement.”

Avoid prompts that invite geometry changes: “surreal face fragmentation,” “dislocated eyes,” “cubist face,” “melting portrait,” “double exposure face,” or “random glitch distortion.”

## 12. QA and rejection gates

Validate in order and stop at the first failure:

1. **Canvas:** exact ratio and orientation match.
2. **Identity/pose:** same person, expression, gaze, hairstyle silhouette, posture, garment and object geometry.
3. **Face:** no altered eye, brow, nose, lip, jaw, or hairline geometry.
4. **Eye panel:** passes the workflow’s seam-continuity and overlay checks; otherwise fallback.
5. **Mouth:** integrated, unpanelized, unduplicated.
6. **Coverage:** at least 65% subject treatment.
7. **Shadows:** at least three source-derived hard-edged masses.
8. **Grain:** fine-to-medium, dense, non-chunky, facial landmarks legible.
9. **Palette:** anchors visibly source-derived; collision accent contrasting but not fixed or arbitrary.
10. **Reference fidelity:** architecture and material hierarchy resemble the references without copying their subject.

Hard reject if any eye is displaced, duplicated, mirrored, resized, repainted, or regenerated; if mouth structure changes; or if aspect ratio changes.

## 13. Revision ladder

Change one layer at a time:

1. Repair canvas ratio/orientation.
2. Restore source facial geometry and pose.
3. Repair or remove eye panel.
4. Increase subject abstraction and shadow blocking if too photographic.
5. Adjust grain scale/density if too smooth or too chunky.
6. Re-derive collision/ghost colors if palette feels fixed or unrelated.
7. Strengthen primary collage architecture.
8. Reduce decorative clutter and preserve negative space.

Never compensate for weak style by increasing facial deformation.
