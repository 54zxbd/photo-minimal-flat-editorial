# Photo Minimal Flat Editorial Prompt (English)

> Purpose: turn one photograph into a **vertical 1366×2048** editorial piece = *original-photo area + minimal flat-vector illustration + title*.
> Recommended **two-step workflow**: first let the model draw **only the illustration** (Step 1), then composite locally (Step 2). This keeps the photo pixels untouched, sets the title in a real typeface, and guarantees the exact canvas size.

---

## Step 1 · Let the model draw *only the illustration*

Send the block below as an **image-to-image / image-edit** instruction together with the source photo. Replace `{...}` with the actual content.

```
Redraw this photograph as a minimal flat-vector illustration.

[Illustration only] The whole frame is one single illustration that fills the canvas. No photograph, no diptych, no top/bottom split, no dividing line, no frame, no text of any kind.

[Background · faithful to the photo] The background must follow the source photo's spatial proportions and colours — it is NOT negative space by default:
- Whatever share of the frame the sky / mountains / sea of clouds / mist / meadow takes in the photo, it takes in the illustration too — the photo is a full landscape, so the illustration is a full landscape; no scene element may be dropped.
- The sky must be a continuous background: sky, cloud sea, sunset glow and mist are drawn as a large, continuously spread flat colour plane. A few stacked bands of tone are fine, but they must meet and fill the region. NEVER shrink a large sky into "a few isolated little clouds on a light background".
- Colour faithful: if the photo is colour-rich, keep it colour-rich — do not reduce it to a few blocks and never replace what is in the photo with blank ivory.
- Ivory #F3F0E8 is NOT the default background: use a clean flat block only where the photo itself is blank / solid / out of focus. Empty space is allowed, but it must not dominate the frame nor intrude on the subject and scene.
- No frame, no picture-in-picture, no rectangular inset — the background should run naturally to all four canvas edges.

[Content · faithful to the photo] {...subject form / pose / facing, colour and pattern traits, surrounding elements (sky / cloud sea / mountains / mist / flower branch / rock / ground / foliage), and "fully visible, never cropped"...}

[Framing · mandatory] The subject and key elements must sit fully inside the canvas, never cut by any of the four edges (peak, head of the subject, key branches). But the background (sky, mountains, cloud sea, mist, ground) must spread naturally to all four edges — never shrink it to a patch in the middle just to leave blank space.

[Texture · fur & fabric · mandatory] This is where the style most often fails:
- A fur / hair covered subject (cat, dog, wolf, sheep, bird…) must NEVER be a single solid flat colour. Build volume with **2–4 tonal steps of one colour family**: light on the lit side, a mid tone for transition, deep tones in shadow and folds; indicate the lie of the fur with a few **blunt, rounded divisions** on the silhouette and body (NOT jagged individual hairs, NOT realistic strands).
- The subject's own markings must be drawn: tiger stripes, spots, light/dark boundaries, contrast between muzzle / chest / belly, dark ear-tips and limbs — these are the key cues that say "this is a furry animal", never flatten them into one colour. Eyes, nose, inner ear and mouth must stay clearly readable.
- Fabric (blanket / fleece / rug / clothing) must NOT become a few harsh big blocks (it reads as a rag). Use **tonal steps within one colour family** along the folds — light receiving, mid-grey recesses, deep shadows — soft adjoining planes that still read as one continuous soft surface.

[Detail · fine textures · mandatory] Wherever the photo has a structure made of **many tiny units**, draw the texture with layered small blocks / short strokes / thin lines — never a single flat circle/shape:
- Flower centre / pistil / disc (sunflower, daisy, lotus pod…): the disc is not a plain circle — suggest the tiny tubular florets / seeds with dense dot groups or short radial strokes (2–3 tonal steps); the yellow centre of a daisy also needs fine dots or short ring strokes, not one plain yellow dot.
- Insect wings & body (butterfly, bee, dragonfly…): wings must show **veins / partitioned colour areas / margin markings** (eye-spot, dark margin band, cell divisions) — never one flat shape; a bee's body needs stripes plus fur shading to separate thorax and abdomen.
- Feathers / leaf veins / anthers / scales: same idea — layered small blocks or grouped short strokes showing direction and structure.
- ⚠️ Restraint rule (important): more density is NOT better. A dense dark dot-grid reads as a sesame biscuit / honeycomb and looks dirty. Dots / lines must be **in the same colour family as the base and lighter** (e.g. daisy centre = pale orange-yellow dots, never dark brown or black); keep density **sparse and grouped**; prefer **two concentric tonal steps (bright inner disc + slightly deeper warm outer ring) plus a sparse ring of short radial strokes**. From a distance the structure must still read as **one clean block of the base colour**.

[Style · key] Minimal flat-vector illustration: summarise with flat colour blocks; shapes moderately geometric; clean crisp edges; clear layering; editorial feel; restrained and condensed, but NOT a reduction of elements — the photo's layering, colour and scene must all be drawn. The subject and scene are recognisable at first glance; only on second glance does one notice how much was simplified. All colours are taken from the source photo (never invent colours that are not there). Note: "flat colour blocks" here means no gradients and clean edges — it NEVER means "one whole animal in one colour"; the interior must keep the tonal and marking layers required by the [Texture] rule above.
```

**Negative prompt** (pass through if the model supports `negative_prompt`):

```
photograph, photorealistic, diptych, top/bottom split, dividing line, frame, picture-in-picture, rectangular inset background, any text, numbers, colour swatches, badge, logo, watermark, cropped subject, subject enlarged to fill frame, subject reduced to a flat single-colour blob, cartoon tiger stripes, fewer subjects than the photo, concentric rings, torch-like cone beam, bright yellow circular glow, scribbled lines, blurry, low resolution, left/right columns, magazine layout, subject leaving the frame, blank ivory field replacing the real sky/background, large sky reduced to a few isolated little clouds, furry animal rendered as one solid flat block with no shading or markings, blanket rendered as a few harsh big blocks (looks like a rag), animal face simplified beyond recognition, flower centre rendered as one plain flat circle, insect wing rendered as one plain flat shape, dense dark dot-grid (flower centre turned into dark dots on yellow)
```

> ⚠️ If the model has a `prompt_extend` (auto prompt-rewriting) switch, **turn it off** — in testing it silently turned "a page of an editorial album" into a two-column magazine layout.

> 💡 To change **one spot only** (e.g. just the background, just the flower centre): feed the **previous illustration layer** as the image-to-image input and open the prompt with "this is a finished illustration; apart from X, **keep everything else pixel-identical, do not repaint the whole frame**".

---

## Step 2 · Local compositing (photo + illustration + title → 1366×2048)

Layout ratios (measured from the reference output):

| Region | Position | Content |
|---|---|---|
| Photo area | y 0–962 (≈0–47%) | **Original photo pixels**, full width, subject never cropped |
| Illustration panel | y 962–1823 (≈47–89%) | **A complete illustration faithful to the photo** (its sky / cloud sea / mountains / mist / meadow at the photo's own proportions — not "a vignette on blank ivory") |
| Text band | y 1823–2048 (≈89–100%) | English serif headline (Title Case, ≈88px, colour `#432619`) + Chinese small-caption subtitle (≈44px) + (optional) photo-credit line |

- Optional `ORIGINAL PHOTO` badge at top-left; `#F3F0E8` swatch label at bottom-right.
- ⚠️ If the source is a 2:3 portrait being placed into a ≈1.42:1 landscape band, you **must bias the crop downward**; a centred crop will cut the subject in half.
- If the photo comes from a stock library (Pixabay / Unsplash / Pexels), add a credit line `Photo by <author> · <library> — <source link>` as the licence requires.
- **Full-illustration layout**: drop the photo area, let the illustration fill y 0–1823; the text band is unchanged.

---

## Choosing the layout

- **Standard diptych**: blurred bokeh background / a single building facade / subject taller than 70% of the frame / no clear small subject → the panel below holds **a complete illustration faithful to the photo** (not a vignette on blank ivory).
- **Through-composition**: the frame has a **natural horizontal carrier** (ground / water / roof / railing / meadow) plus a clear small subject → hide the seam inside that horizontal element and let elements continue across it; the seam must be a **soft transition of visible width**, never a hard straight cut.
- **Full illustration**: the frame is a **meaningful composite scene** (garden / heritage architecture / animal + artefact) → no diptych; the illustration fills the top, only the text band remains.

> Three hard gates for the layout: ① is there a horizontal element able to hide the seam; ② is there a small subject of moderate scale; ③ would the subject be broken and hard to repair. Fail any one → use the standard diptych.

---

## Core principles (in priority order)

1. **Background fidelity (highest)**: whatever share of the frame the photo's sky / mountains / cloud sea / mist / meadow takes, draw exactly that; large-scale background such as sky must be drawn as a **continuously spread flat colour plane**; **never replace what exists in the photo with blank space**, and blank space must not dominate the frame or intrude on the subject.
2. **Faithful to the photo**: no enlarging the subject, no reducing the number of subjects, no changing pose or facing; all colours come from the photo.
3. **Minimal ≠ stripped of meaning**: the subject reads at first glance and only later reveals its simplification; keep the subject **plus** its supporting elements (sky / light / ground / characteristic environment).
4. **Layer the materials**: fur = 2–4 tonal steps of one colour family + real markings; fabric = soft tonal steps of one colour family.
5. **Restrain fine textures**: draw the structure, but keep dots / lines in the base colour family, lighter and sparsely grouped — from afar it must still read as one clean block.
6. **Complete framing**: the subject is never cut by the edges, but the **background must spread naturally to all four edges**.
