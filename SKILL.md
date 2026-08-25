---
name: fashion-lookbook-collage
description: Transform a seller-supplied apparel product or outfit reference into a vertical multi-view fashion lookbook collage with a central hero outfit, styling vignettes, palette chips, and restrained editorial annotations. Use for shoppable outfit inspiration, fashion product storytelling, and apparel social assets; do not use for isolated product packshots or material boards.
---

# Fashion Lookbook Collage

Create a vertical, social-first fashion lookbook collage that makes one outfit immediately understandable and desirable while preserving the source garment faithfully. The visual language is warm, editorial, tactile, and personal—not a catalogue grid or a generic moodboard.

## Require reference imagery

This workflow is reference-led. Require at least one clear seller-supplied apparel product image, outfit image, or model image before generating.

- If no image is provided, ask: `请先上传至少一张清晰的服饰商品图或穿搭图。`
- Use the supplied garment and its visible details as source of truth. Written style direction supplements the reference; it never authorizes changing the product.
- Inspect garment category, silhouette, colour, print, texture, closures, accessories, and visible styling before composing the collage.

## Protect product and identity fidelity

Treat the source image as product evidence, not loose inspiration.

- Preserve the garment's category, silhouette, proportions, neckline, sleeves, length, construction, print, colour, material appearance, logos, buttons, hardware, and visible styling.
- Preserve bags, footwear, jewellery, and other accessories when the user asks to keep the outfit intact. Do not invent product features, extra pieces, discounts, claims, or logos.
- When a person is visible, preserve face, hair, body proportions, skin tone, pose, and identity in any reused editorial frame. Do not beautify, face-swap, or alter their body.
- Use image editing/reference-image generation. Do not generate a visually similar but different SKU.
- A full-body source can support three generated complementary editorial poses when the user asks for them. Lock the same person, complete outfit, product colours, construction, footwear, and accessories across every view; vary only pose, camera distance, and supported everyday setting.
- A cropped or single-angle source must retain its original crop unless the user explicitly asks for generated lookbook views. Even with that permission, never invent unseen construction, a false back detail, alternate colourway, or extra product.

## Build the collage

1. Choose a vertical 3:4 or 4:5 composition. Create a central, headless product cutout assembled from the complete outfit. Separate only groups that remain visually coherent when isolated: normally the complete upper look, lower garment, footwear, and relevant bag/accessory. Give it a thin off-white outline or torn-paper border.
2. Use exactly four photo slots by default, plus the central cutout: slot 1 is the supplied main image retained as an unchanged physical print; slots 2–4 are newly generated editorial vignettes. Use a seated look, a relaxed standing look, and a walking/three-quarter look. Every panel must show the exact same outfit and person.
3. Choose one restrained setting that matches the look: warm sunlit interior, quiet European street, riverside walk, garden path, or similarly understated everyday setting.
4. Add a compact 3–5 chip colour palette taken from the actual outfit. Add small paper, tape, clips, miniature notes, or hand-drawn marks only when they support the collage.
5. Keep annotations sparse, handwritten, and truthful to visible features. Do not use prominent marketing copy or invented product claims.

### Layered upper-look rule

Do not mechanically cut out every visible garment as a separate product. First decide whether each layer remains a credible, understandable fashion item when isolated.

- Keep an **outer layer plus dependent inner layer** together as one complete upper-look cutout when the inner layer is styled beneath, partly obscured by, visually anchored by, or aesthetically incomplete without the outer layer.
- Common cases include a camisole under a jacket, a blouse under a cardigan, a slip-style top under a knit, a bodysuit under a blazer, or a visible lining/underlayer.
- In these cases, show the outer layer worn over the inner layer exactly as in the source. Do not extract the inner layer as a standalone floating top.
- Separate the upper garment only when it is a complete, independently readable hero item and the user explicitly wants product-level separation.
- Lower garments, footwear, bags, eyewear, and jewellery may be isolated only when visible construction remains faithful and the upper outfit stays complete.

## Fixed quadrant layout — default and required

Use this layout unless the user explicitly asks for another template. It is based on a 735 × 1105 reference canvas. Treat the four photo panels as a full-bleed 2 × 2 photo base, not four floating cards.

Scale every coordinate by `sx = output_width / 735` and `sy = output_height / 1105`. Round only when the compositor requires integer pixels.

| Layer | Reference rectangle `(x, y, width, height)` | Normalized rectangle `(x/W, y/H, w/W, h/H)` | Required content |
| --- | --- | --- | --- |
| Photo slot 1 | `(0, 0, 365, 551)` | `(0, 0, 0.4966, 0.4986)` | Original source image, unchanged |
| Photo slot 2 | `(370, 0, 365, 551)` | `(0.5034, 0, 0.4966, 0.4986)` | Generated standing / three-quarter look |
| Photo slot 3 | `(0, 554, 365, 551)` | `(0, 0.5014, 0.4966, 0.4986)` | Generated seated look |
| Photo slot 4 | `(370, 554, 365, 551)` | `(0.5034, 0.5014, 0.4966, 0.4986)` | Generated walking / relaxed look |
| Central product group | `(294, 293, 181, 481)` | `(0.4000, 0.2652, 0.2463, 0.4353)` | Headless complete upper look, lower outfit, footwear, and relevant bag/accessory |

- Leave a **5 px vertical gutter** (`x=365–369`) and a **3 px horizontal gutter** (`y=551–553`). Both are solid off-white; photos never overlap them.
- Every photo panel is a hard rectangular `object-fit: cover` crop. Do not rotate it, round corners, or change the rectangles.
- The central product group is above all four photo panels. It may overlap each panel but never goes behind one.
- Keep the product group vertically centred on the seam. Do not exchange slot positions.

### Fixed secondary elements

| Element | Reference placement | Rule |
| --- | --- | --- |
| Colour chips | bounding box `(173, 527, 137, 38)` | Five overlapping 36 px circles, centred on the horizontal seam; derive colours only from the outfit |
| Top-left annotation | `(28, 73, 145, 112)` | Small light handwritten/serif copy in photo slot 1 upper-left safe area |
| Top-right doodle | `(674, 77, 52, 48)` | One small heart/doodle in photo slot 2 upper-right safe area |
| Middle-right torn note | `(488, 512, 150, 114)` | Torn warm-paper note to the right of the product group |
| Bottom-left tape | `(23, 587, 58, 31)` | One short diagonal masking-tape strip |
| Bottom-left note | `(83, 995, 190, 105)` | Small torn note, possibly partly cropped by the canvas edge |
| Bottom-right doodle/text | doodle `(674, 621, 49, 59)`; copy `(651, 918, 66, 132)` | Keep both in photo slot 4's right-side negative space |

For deterministic output, generate the three new photo panels and the central product cutout separately, then composite them at these coordinates. Use a single all-in-one image-generation request only for a visual draft, never as the layout-stable production path.

## Visual language

- Use a near-editorial scrapbook composition with tactile paper texture, soft daylight, gentle shadows, and a disciplined palette from the product.
- Make the central look visually dominant. Keep the result casual-chic, personal, and polished enough for a fashion social or shop-story asset.
- Text is optional and subordinate. Never rely on generated text for required product information, prices, sizes, or legal claims.

## Prompt recipe

Use this structure for image editing:

```text
Edit the supplied apparel reference into a vertical fashion lookbook collage. Preserve the exact garment category, silhouette, colours, print, fabric appearance, visible accessories, and model identity. Use exactly four photo slots: place the supplied source image, unchanged, in slot 1; generate slots 2–4 as three new lifestyle poses of the same person wearing the exact same outfit—seated, relaxed standing, and walking/three-quarter. Do not substitute a crop or repeat of the source for any generated slot. Place a central headless product cutout made from the complete outfit: keep an outer layer and any dependent inner layer together as one complete upper look; isolate only visually coherent groups such as the complete upper look, lower garment, footwear, and relevant bag/accessory. Arrange panels with a compact palette taken from the garment, warm paper/tape details, and sparse tiny handwritten feature notes. Do not change, redesign, recolour, extend, or invent garment details, accessories, logos, text claims, or identity.
```

## Quality checks

Before delivering, verify:

- The centre outfit remains recognizably the seller's original SKU.
- All vignettes show the same garment, colours, prints, and accessories.
- There are exactly four photo panels: slot 1 is visibly the unchanged source, and slots 2–4 are distinct generated poses.
- The central cutout is fully readable and keeps any outer layer plus dependent inner layer together.
- Palette chips match the product, and text is small, sparse, and nonessential.

## Avoid

- Dense grids, glossy magazine covers, store catalogues, UI mockups, large slogans, price tags, or watermarks.
- Changed SKU details, invented branding, unsupported back construction, or a different person's identity.
- More than one focal outfit unless the user explicitly asks for a comparison.
- Excessive stickers, props, decorative typography, or clutter that lowers product legibility.
