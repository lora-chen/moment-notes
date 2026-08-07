---
name: moment-notes
description: Create or edit photos by overlaying warm Chinese handwritten annotations, doodles, arrows, and emotional notes while preserving the original image. Use for 给照片加手写注释, 照片涂鸦, 情绪小记, 朋友圈/小红书配图, zhaopian shouxie zhushi, zhaopian tuya, photo annotation, doodle overlay, moment notes, and social sharing images across daily life, food, pets, portraits, travel, hiking, climbing, diving, gear flat lays, tabletop objects, and professional scenes.
---

# Moment Notes

Generate warm handwritten photo notes by editing the uploaded image itself. The result should feel like a gentle emotional note written on the original photo, not a recreated image or an objective diagram.

Current official prompt: V6.3, scaffolded references and QA reflection. It keeps the V6.2 subject-priority, adaptive-density, readability, professional-scene, doodle-symbol, and same-image copy de-duplication rules, then adds a clearer photo diagnosis -> annotation strategy -> prompt assembly -> single generation -> QA reflection -> issue meta workflow.

This skill is image-first. When image input is present, the first output should be the generated annotated image result, not a clarification round or a text-only draft.

## Required Capabilities And Data Use

- Required input: user-selected photos. Access only the images the user explicitly provides for the current task.
- Required capability: an image-editing tool that can preserve the uploaded photo while adding an annotation layer. Pure text-to-image generation is not sufficient for the default workflow.
- Optional capability: local file saving when the user asks to keep the generated result.
- Optional capability: GitHub issue drafting only when the user explicitly says `report to issue:`. Never publish an issue or attach an image until the user has reviewed the public-safe draft and explicitly confirmed submission.
- No background access is required. Do not request contacts, location, account data, browser cookies, credentials, unrelated files, or persistent access.
- Do not upload or reuse the user's photos outside the requested image-editing task. Treat photos and generated outputs as private unless the user explicitly approves public sharing.

## Reference Routing

Read only what the task needs; do not load every file by default:

- Image input present: read `references/photo-diagnosis.md`, then `references/annotation-patterns.md`, `references/style-dna.md`, and `references/prompt-template.md`.
- After generation: read `references/qa-checklist.md` and `references/bad-cases.md`.
- User says `report to issue:`: read `references/issue-report-template.md`.
- User asks for rule review, V6.2/V6.3 comparison, test acceptance, or "收敛规则": read `references/v6.3-rule-map.md`.
- Calibration needed or user asks about examples: optionally read `examples/positive-cases.md` and public-safe files in `assets/examples/`.
- Older installs looking for one prompt file may read `references/prompts.md`, but current behavior should use the modular files above.

Examples are optional calibration only. Never copy their exact objects, composition, annotation text, arrows, or doodles.

## Workflow

### 1. Photo Diagnosis

For each uploaded image, inspect the photo first and produce internal diagnosis meta:

- one gentle emotional line
- relationship summary, such as person-pet, person-object, object-accident, object-object, scene-person, or sky/wind/light-subject
- subject mode: single subject, clear hierarchy, collection subject, or professional collection
- key subjects and visible object groups
- high, medium, and low-priority objects or props
- scene state, especially whether emotion comes from an event, preparation, interaction, accident, openness, quietness, or recovery
- quiet/readability-safe areas where handwriting can sit

Use `references/photo-diagnosis.md` for the diagnosis rules.

Keep this meta internal unless the user explicitly asks for analysis. Pass it forward to annotation strategy, prompt assembly, QA, and issue reporting.

### 2. Annotation Strategy

Build a compact overlay strategy from the diagnosis meta:

- intended annotation density
- 2-10 local note intentions, adjusted by subject mode and available space
- objects that should stay silent or only support another subject
- structural marks, such as outlines, grouping frames, arrows, flight lines, motion lines, or soft circles
- optional decorative doodles that express the relationship rather than decorate randomly
- placement plan for readability and subject preservation

Use `references/annotation-patterns.md` and `references/style-dna.md`. Do not output this strategy unless the user explicitly asks for analysis or planning.

### 3. Prompt Assembly

Turn the diagnosis and annotation strategy into a single-image edit prompt.

The prompt must include:

- preserve the uploaded photo as the base image
- preserve the original visual proportion, crop feeling, composition, resolution feel, compression texture, and perceived sharpness
- one emotional line
- relationship summary and subject mode
- key subjects/object groups and low-priority props to avoid over-emphasizing
- annotation density and local note intentions
- structural marks and doodles
- readability strategy
- explicit requirement for organic handwritten strokes, not font-rendered text
- explicit ban on redrawing, restyling, copying examples, or merging images

Build the edit prompt from `references/prompt-template.md`.

### 4. Single Generation

When the user provides one or more images, generate directly. Use image editing, inpainting, reference-image editing, or overlay behavior so the uploaded photo remains the base image.

- Generate exactly one result for each input image by default.
- The generated image should keep the same visual proportion, aspect ratio, crop feeling, composition, and subject positions as the input image. Small pixel-dimension differences are acceptable if the result still looks like the same photo and does not feel cropped, stretched, padded, upscaled, downsampled, blurred, or recompressed.
- Do not satisfy preservation checks by replacing the generated handwritten layer with local system-font text, font-rendered handwriting, subtitle-like text, or typed Chinese with artificial jitter.
- Process multiple images separately; do not merge them into one output unless the user explicitly asks.
- Never use pure text-to-image generation to recreate a similar photo unless the user explicitly asks for a remake.

### 5. QA Reflection

After generation, check the result with `references/qa-checklist.md` and `references/bad-cases.md`.

If a serious failure appears, regenerate or locally edit at most once. Serious failures include: the source photo was recreated, aspect ratio/crop/composition/subject positions visibly changed, the base photo became visibly blurry or degraded, the main subject changed, annotations are unreadable, the annotations look like system-font text or subtitle text instead of real handwritten strokes, low-priority props stole focus, the image is overcrowded, wording repeats badly, or professional objects were confidently misnamed.

If the first generation has the right emotion but only a tiny pixel-size difference, do not treat that alone as failure. If it changes visual proportion, crop, subject positions, or base-photo quality, retry image editing from the original photo. Do not "fix" the result by drawing Chinese text with local fonts on top of the source photo; that is a style failure, not a valid QA repair.

Do not generate multiple candidates just to offer options. One image per input is the default; one retry is only for QA failure.

Track internal QA meta:

- pass, minor issue, or serious failure
- failed QA IDs and bad-case IDs when relevant
- retry decision and whether the one retry has already been used
- residual risk after retry

### 6. Issue Meta

If the user later says `report to issue:`, use the stored workflow meta when available:

- photo diagnosis meta
- annotation strategy meta
- prompt assembly meta
- QA meta
- example calibration meta, if examples influenced judgment
- user complaint, expected behavior, and actual failure

Use `references/issue-report-template.md`. If a field was not captured, write `not captured` rather than inventing it.

### 7. Deliver

After image generation, optionally add:

- one short emotional summary
- three practical follow-up directions, such as fewer words, more lively notes, stronger readability, or more careful gear recognition

Keep the post-generation text short. Let the image do the work.

## Feedback Issue Behavior

- Repository issue tracker: `https://github.com/foxbitcoo/moment-notes/issues`
- If the user explicitly says `report to issue:` followed by feedback, organize the current request, the generated result summary, and the user's complaint into an issue-ready report.
- If the host environment supports GitHub issue creation, show the public-safe draft first and submit it only after the user explicitly confirms.
- If the host environment does not support direct issue creation, give the user the issue URL and a compact issue draft they can submit manually.
- Use `references/issue-report-template.md` to include V6.3 workflow metadata when available: photo diagnosis, relationship summary, subject mode, object priority, annotation strategy, prompt template path, QA failures, retry decision, version used, and any shareable screenshot or description.
- If some metadata was not captured in the current host environment, write `not captured` instead of inventing it.

## Hard Rules

- Do not ask for confirmation before the first generation when image input is present, unless the user explicitly requests a planning round.
- Do not replace the first-generation step with a txt file, note file, or text-only response.
- Preserve the source image filter, color mood, composition, object positions, crop ratio, and overall visual character.
- Preserve the source image aspect ratio, crop feeling, composition, object positions, resolution feel, compression texture, and perceived sharpness. Small pixel-dimension differences and subtle natural light/color drift are acceptable when the result still looks like the same photo and feels better as a Moment Notes output.
- Do not visibly crop, stretch, pad, upscale, downsample, pixelate, blur, denoise, over-sharpen, smooth, recompress, or otherwise degrade the base photo.
- Keep annotations emotionally warm, Chinese-first, short, and handwritten.
- Handwriting must look like organic hand-drawn strokes. System-font text, font-rendered handwriting, subtitle-like text, or typed Chinese with artificial jitter is a serious failure even if the output size is correct.
- Do not annotate every visible object by default. Annotate what carries the user's likely feeling.
- In professional scenes, identify important tools and gear when confident. Use safer generic names when uncertain, and do not invent exact models or functions.
