---
name: image-to-ppt
description: Recreate a screenshot, infographic, poster, diagram, or flattened slide image as a closely matched editable PowerPoint slide. Use when the user wants the same visual in PPT/PPTX with separate movable text, cards, shapes, arrows, numbers, dividers, and illustration assets instead of one full-slide background image. Especially useful for Arabic or RTL presentation designs.
---

# Image to Editable PowerPoint

Reconstruct the reference as native PowerPoint elements while preserving its visual identity and composition. Treat editability and visual fidelity as equally important deliverables.

## Define editability

Default to this decomposition unless the user specifies otherwise:

- Rebuild text, cards, circles, lines, arrows, dividers, badges, and simple diagrams as native PowerPoint elements.
- Keep each logical illustration or icon as a separate movable image when recreating it natively would reduce fidelity.
- Never satisfy an editable-PowerPoint request by placing the full reference image as the slide background.
- Preserve grouped meaning: a multi-part illustration may remain one movable asset, while its surrounding label, container, and connectors stay editable.

Briefly disclose in the handoff which elements are native and which remain movable image assets.

## Workflow

### Start immediately

When the user provides an image and requests a PowerPoint conversion, begin implementing the final editable slide immediately. Do not create a separate test slide, proof of concept, prototype, sample, or draft before implementation. Do not ask for confirmation when the image and requested output are clear. Inspect the supplied image only as part of the direct conversion workflow.

Perform rendering, font verification, and overflow checks only after the slide has been implemented. These are final quality checks, not prerequisites or separate testing phases.

### 1. Inspect the exact reference

Use the exact image selected by the user. Do not substitute a similar image from earlier context when a selected edit target exists.

Record the slide aspect ratio and visually map:

- canvas margins and whitespace;
- reading direction and sequence;
- element bounds and alignment anchors;
- colors, line weights, shadows, radii, and spacing rhythm;
- font family, size hierarchy, weight, and alignment;
- repeated components and z-order;
- illustration groups that need separate assets.

### 2. Choose the reconstruction method per element

Use native PowerPoint shapes for deterministic elements such as containers, lines, arrows, dots, numbering, and separators.

For illustrations and icons, prefer these methods in order:

1. Crop the exact illustration from the reference when it sits on a matching solid background and can be isolated cleanly.
2. Use image editing or generation to isolate it as a transparent movable asset when cropping would retain unwanted text, borders, or background.
3. Rebuild simple geometric icons natively only when the match remains faithful.

Use the image-generation skill when the task needs isolated raster assets. Request no text, generous separation, transparent background, and strict preservation of palette and line style. Inspect the result; reject assets that introduce dark backgrounds, glow, invented detail, or style drift.

### 3. Rebuild from back to front

Use the presentations skill and its required authoring workflow.

Create elements in this order:

1. background;
2. connectors and arrows;
3. containers and structural shapes;
4. illustration assets;
5. headings and body text;
6. foreground badges, numbers, and small labels.

Keep element names meaningful so inspection and later editing remain easy.

### 4. Preserve Arabic and RTL behavior

Use **IBM Plex Sans Arabic** as the default font family for every editable text element in the PowerPoint, including Arabic and English headings, body copy, numbers, labels, and captions. Apply it explicitly to each text shape rather than relying only on the presentation theme or system fallback. Use a different font only when the user explicitly requests one.

Before delivery, inspect the exported PPTX or its font evidence and confirm that editable text consistently resolves to IBM Plex Sans Arabic. If the font is unavailable in the authoring environment, report the limitation instead of silently substituting another font.

Set alignment and reading order for Arabic deliberately. If the rendering engine visually reverses Arabic word order, reverse words within each manually controlled line before export, then verify the rendered slide. Do not reverse characters. Use manual line breaks to protect intended wrapping.

Keep Arabic titles on one line when the reference does. Shorten copy or widen the box before reducing type size.

### 5. Match, render, and iterate

Render the final slide at full size and compare it with the reference side by side. Check:

- overall silhouette and proportions;
- exact right-to-left sequence;
- card sizes and spacing;
- illustration scale and crop;
- title and body wrapping;
- arrows behind cards rather than across them;
- unwanted source text or borders inside cropped assets;
- clipping, overflow, and unintended overlap;
- consistency of colors, strokes, and shadows.

Fix visible mismatches instead of accepting a structurally valid but visually different slide. Run the presentation overflow check before delivery.

## Fidelity rules

- Match the reference first; do not redesign it unless the user requests improvement.
- Do not convert a flat reference into a generic card grid or a different visual language.
- Preserve the exact content and numbering supplied by the user.
- Use the reference's palette rather than approximating with unrelated theme colors.
- Avoid blurry full-image crops. Crop each illustration tightly and keep sufficient source resolution.
- Keep the final slide usable: text must remain editable, illustrations independently movable, and no invisible full-slide image should sit above editable objects.

## Handoff

Deliver only the final PPTX. State concisely that the slide was reconstructed with separate editable elements and identify any movable raster illustration assets that are not vector-editable.
