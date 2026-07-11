# Single-Image Edit Prompt Template

Use this file after `photo-diagnosis.md`, `annotation-patterns.md`, and `style-dna.md`. It turns the diagnosis and overlay plan into the final image-editing prompt.

Rules are numbered for review and iteration. When commenting, refer to IDs such as `PT-01` or `PT-07`.

## PT-01 Main Edit Template

Use this template for each uploaded image. Replace bracketed content from the photo diagnosis and overlay strategy.

```text
Edit the uploaded photo itself. Do not recreate, redraw, replace, restyle, beautify, crop, recompose, or change the original photo.

Preserve visually:
- original filter, color mood, exposure, saturation, contrast, sharpness, grain, and atmosphere
- original aspect ratio, crop feeling, visual proportion, resolution feel, compression texture, motion blur, focus softness, low-light grain, and fine detail level
- composition, crop ratio, camera angle, object positions, people, faces, bodies, gestures, clothes, pets, food, gear, tools, desk objects, skyline, kites, background details, visible text, watermarks, and all visible items

Subtle natural light/color drift is acceptable if it helps the final image feel coherent and still clearly reads as the same user photo. Do not turn the photo into a new filter, a beautified remake, or an AI-polished scene.

Add only a warm Chinese handwritten annotation layer on top of the original photo.

Photo diagnosis:
- Emotional line: {one gentle emotional line from scene state, not object names}
- Relationship summary: {important relationship, such as person + pet, object + accident, gear collection, sky/wind + kites}
- Subject mode: {single subject / clear hierarchy / collection subject / professional collection}
- Key subjects and object groups: {compact object list or grouped collection list}
- Low-priority props to avoid emphasizing: {low-priority object list}
- Readability-safe areas: {quiet areas or placement notes}

Overlay plan:
- Annotation count: {number, chosen from image intent and available space}
- Local notes: {short Chinese notes, each tied to a subject, relationship, object group, or quiet area}
- Structural marks: {arrows, curved motion paths, dotted routes, subject outlines, group frames, soft circles, or check marks}
- Decorative doodles: {few strongly related hearts/stars/steam/paw marks/sun/sparkles, or "none"}

Style:
White or warm-white thin handwritten Chinese notes, slightly loose one-stroke handwriting, small natural variation in line thickness and curve, like a friend gently wrote on the photo. The text must look like organic raster handwriting with irregular pressure, imperfect stroke starts and ends, natural character rhythm, and small human unevenness. Do not use system-font text, font-rendered handwriting, subtitle-like text, UI text, or typed Chinese with artificial jitter. Use light one-stroke arrows, soft curved lines, dotted lines, small circles, and tiny symbols only when useful. Keep the mood warm, affirmative, emotionally supportive, and specific. Keep all notes short and readable. Leave some emotional silence; not every feeling needs to be written out.

Frames and outlines:
Thin white or warm-white frames, outlines, or dotted borders are allowed only when they clarify the main subject, relationship, movement, object group, preparation, or recovery. They should feel like hand-drawn "圈重点", not cutout stickers, heavy halos, UI labels, or precise masks.

Readability:
Place text in quiet background areas when possible. If the background is dark, bright, noisy, or high-contrast, use subtle readability protection such as warm-white text, tiny soft shadow, very light outline, subtle blank edge, or small translucent backing. Do not make cards, blocks, bubbles, heavy labels, slides, or poster panels.

Constraints:
Do not annotate every visible object. Do not distribute notes evenly. Do not let low-priority props become main characters. Do not write long explanations. Do not repeat the same words or sentence templates. Do not invent exact professional gear names when uncertain; use safe generic names. Do not cover faces, pets, food centers, key gear, action lines, or the main subject. Do not visibly crop, stretch, pad, downsample, upscale, pixelate, posterize, blur, denoise, over-sharpen, smooth, or recompress the base photo. Small pixel-dimension differences and subtle natural light/color drift are acceptable if the final image keeps the same visual proportion, crop feeling, subject positions, and quality. Do not satisfy preservation checks by drawing typed local-font Chinese text on top of the source photo. The result must look like real handwritten notes added to the original photo, not a new image and not a font-rendered overlay.
```

## PT-02 Relationship-Driven Prompt Fill

Use when the photo is about an interaction or scene relationship.

Fill these variables carefully:

- `Relationship summary`: describe the relationship before objects, such as "person and dog sharing one playful action" or "sky, wind, city edge, and kites lifting the mood".
- `Local notes`: write notes that support the relationship, not isolated object labels.
- `Structural marks`: use motion curves, attention lines, flight paths, or gentle arrows to connect the subjects.

Avoid:

- Do not turn the image into a list of object labels.
- Do not make each object tell a separate story.

## PT-03 Collection Roll-Call Prompt Fill

Use when the image is an intentional collection, gear flat lay, packing scene, table spread, toolkit, or pre-departure layout.

Fill these variables carefully:

- `Subject mode`: collection subject or professional collection.
- `Key subjects and object groups`: group items by role, such as warmth, rain protection, safety, storage, electronics, hygiene, recovery, food, or navigation.
- `Annotation count`: higher density is allowed if the frame has room and the collection is meant to be inspected.
- `Structural marks`: use thin group frames, dotted borders, check marks, and small route or mountain symbols when useful.

Avoid:

- Do not treat the collection as clutter.
- Do not invent exact gear names or functions.
- Do not let tiny accessories steal focus from key groups.

## PT-04 Small Accident Prompt Fill

Use when the photo shows a spill, mess, breakage, failure, or small life accident.

Fill these variables carefully:

- `Emotional line`: acknowledge the accident, comfort the viewer, and keep the day moving.
- `Key subjects and object groups`: include the accident and what needs protection or recovery.
- `Local notes`: use gentle reassurance, not blame.
- `Structural marks`: use soft circles, gentle arrows, small sparkles, protective outlines, or light hearts.

Avoid:

- Do not make the emotion "disaster", "failure", or "you messed up".
- Do not write a cleanup tutorial.
- Do not overuse jokes if comfort is needed first.

## PT-05 Background-Specific Prompt Fill

Use background-specific placement to keep the result readable and light.

- Green foliage or grass: place notes in quiet gaps, use light outlines around people/pets, and add gentle motion curves only where useful.
- Gear flat lay or busy tabletop: place notes near groups; do not write on important labels or tiny details.
- Desk accident or spill: use soft containment marks; avoid alarm symbols.
- Open sky or park: keep sky breathable; use sparse notes, flight lines, or cloud-like bubbles.
- Food or cafe scenes: use steam, small curves, and quiet warmth; avoid ad-like layout.
- Portrait or pet close-up: keep faces and eyes clean; place notes around posture, gaze, light, or quiet surrounding space.

## PT-06 Retry Prompt For QA Failure

Use only when the first generated image has a serious QA failure. Retry at most once.

```text
Edit the previous result or regenerate from the original uploaded photo with the same emotional line, but fix this QA failure: {specific failure}.

If the original photo was changed, recreated, heavily beautified, restyled, visibly cropped, stretched, padded, blurred, pixelated, posterized, recompressed, or objects moved, restart from the original uploaded photo and preserve it visually.

If the issue is readability, keep the same notes but move them to quieter areas or add only subtle readability protection.

If the issue is clutter, reduce annotation count, remove weak doodles, and keep only the strongest notes tied to the main subject or relationship.

If low-priority props stole focus, remove their standalone annotations and re-center the true subject or emotional relationship.

If professional objects were misnamed, replace exact names with safer generic names.

If the notes look like system-font text, subtitle text, UI text, or typed Chinese with artificial jitter, regenerate the handwritten annotation layer from the original photo. Do not repair by using local fonts.

Preserve original visual proportion, aspect ratio, composition, crop feeling, objects, people, pets, background, filter, color mood, sharpness, grain, compression texture, and atmosphere. Add only a clearer, lighter organic handwritten annotation layer. Do not create extra candidate images.
```

## PT-07 Prompt Hygiene

Before generating, check:

- The prompt says edit the uploaded photo itself.
- The prompt contains the emotional line, relationship summary, subject mode, object groups, low-priority props, and readability-safe areas.
- The prompt separates structural marks from decorative doodles.
- The prompt states one image only for this input.
- The prompt does not ask for multiple candidates.
- The prompt does not copy example compositions, exact notes, or object choices.
