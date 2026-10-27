# Eye-Panel Workflow

Use this workflow whenever a rectangular eye-region treatment is requested or chosen. The rectangle is a **spatially aligned material window**, never a displaced fragment.

## Protected eye core

The following geometry is immutable:

- eye position, angle, scale, spacing, and perspective;
- eyelid contour, iris/pupil placement, catchlights, brow relationship, and gaze;
- hair strands crossing the eye region;
- surrounding nose bridge and orbital contour.

Allowed operations inside the rectangle: source-aligned tint/value remap, halftone, fine grain, print-density change, abrasion, contrast compression, and an optional border. These operations must not redraw anatomy.

## Mode selection

Choose the safest available mode before generating.

### Mode A — Deterministic source-pixel composite

Preferred when the user explicitly requires unchanged eyes or when delivery reliability matters.

1. Duplicate the unwarped source portrait at identical dimensions.
2. Define a rectangle around one distinctive visible eye; include enough surrounding brow/hair/skin to make seam continuity testable.
3. Copy the exact same-coordinate source pixels into the panel layer. Never resample, rotate, mirror, translate, or perspective-warp them.
4. Apply only material/color transforms to the panel layer.
5. Add the frame/border on a separate layer.
6. Confirm the panel’s geometric transform is the identity matrix.

### Mode B — Generative aligned panel

Use only when the image tool must create the panel in one pass and exact source pixels cannot be composited.

The prompt must explicitly require a source-aligned material window, strict eye-core no-op, unchanged hair crossings, and no feature duplication. Generate at most two candidates/attempts, validating each before acceptance.

### Mode C — Frame-only fallback

Draw a rectangle around the original eye region while leaving its interior unmodified or applying only a uniform source-aligned tint. Use when a stronger material change cannot pass validation.

### Mode D — Omitted

Omit the eye rectangle when the eye is too small, occluded, motion-blurred, cropped, heavily foreshortened, or impossible to validate. Strengthen background plates, grids, grain, shadow blocks, and the circular registration arc instead.

## Candidate policy

- Maximum two generative eye-panel attempts.
- A second candidate exists only to test visual continuity; it may not use shifted geometry as an aesthetic alternative.
- If both fail, switch to Mode A, C, or D. Never keep regenerating in hope of accidental alignment.

## Validation

### Seam-continuity test

Inspect the rectangle’s left, right, top, and bottom seams. Hair strands, eyelid edges, brow contours, skin gradients, and nose-bridge contours must continue across each seam without a positional jump.

### Overlay/difference test

When image tools permit:

1. Align output and source at identical dimensions.
2. Compare the protected eye core using a difference blend or high-opacity overlay.
3. Ignore intended color/texture changes.
4. Reject if anatomical edges split into doubled contours or shift relative to the source.

### Visual labels

- **Pass:** geometry matches; only color, value, print density, grain, or abrasion differs.
- **Uncertain:** insufficient resolution or occlusion prevents proof. Do not claim exact preservation; use Mode C or D.
- **Fail:** any translated, scaled, rotated, mirrored, duplicated, repainted, or regenerated eye/brow/hair geometry.

## Panel placement

- Prefer one panel over both eyes unless a single wide band can remain perfectly registered.
- The panel may be larger than the eye and may cross hair, brow, or nose bridge.
- Keep rectangle edges orthogonal to the canvas unless the source itself is deliberately rotated.
- Do not use the panel to cover a facial error.
- Never apply this workflow to the mouth.

## Report

Record: chosen mode, target eye, attempt count, seam-continuity result, overlay/difference result when available, and fallback used. “Looks close” is not a pass.
