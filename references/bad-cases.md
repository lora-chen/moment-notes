# Bad Cases

Use this file as the failure-signal index for V6.3. If a generated result matches any serious case below, prefer one focused retry or local edit. Do not generate many alternatives.

## BC-01 Original Photo Damage

Failure signal:

- The uploaded photo is recreated as a similar-looking new image.
- Crop ratio, composition, object positions, face, pet, dish, gear, or background changes.
- The photo is beautified, restyled, refiltered, posterized, or made to look like generated artwork.
- Aspect ratio, visible crop, padding, stretch, composition, or subject positions change, or the base photo becomes blurry, pixelated, blocky, over-compressed, over-denoised, over-sharpened, smoothed, or lower-detail than the input.

Rule:

Moment Notes must feel like handwriting added onto the original photo. The base photo is not the creative material to remake, resample, clean up, or degrade.

## BC-02 Object Inventory Instead Of Emotion

Failure signal:

- Notes only label visible objects, such as "cup", "dog", "sky", "backpack", or "keyboard".
- The result reads like visual detection instead of a felt moment.

Rule:

Object names are not emotion. Each note should respond to a relationship, scene state, or gentle feeling.

## BC-03 Evenly Distributed Notes

Failure signal:

- Every visible object gets one similar note.
- The layout feels mechanically balanced rather than emotionally guided.

Rule:

Notes should follow the emotional line. Some visible things should stay silent.

## BC-04 Low-Priority Props Steal Focus

Failure signal:

- Spoons, mats, walls, ordinary devices, edge decorations, or generic background items become more important than people, pets, food, key gear, or the main scene state.
- Background context gets more attention than the foreground relationship.

Rule:

Low-priority props can support the subject, but they should not become independent story owners.

## BC-05 Collection Subject Treated As Clutter

Failure signal:

- Gear flat lays, tabletop preparation, tool layouts, packing scenes, or departure checklists are treated as messy background.
- Important groups are ignored because there are many objects.

Rule:

When the collection itself is what the user is showing, the object list is the subject. Recognize groups and create a roll-call feeling instead of dismissing the scene as clutter.

## BC-06 Small Accident Becomes Mockery Or Cold Labels

Failure signal:

- A spilled drink, messy desk, broken rhythm, or small daily accident is described as failure, embarrassment, or chaos.
- Notes only label the cup, keyboard, stain, paper towel, or damaged item.

Rule:

Small accidents need comfort: acknowledge the accident, soften the feeling, then add a tiny sense of recovery or action.

## BC-07 Broken Emotional Line

Failure signal:

- Local notes each push a different tone: cute, tutorial-like, sarcastic, sentimental, objective, and promotional all mixed together.
- The image has many comments but no single emotional direction.

Rule:

One image should carry one main emotional line. Local notes may vary, but they must support the same felt moment.

## BC-08 Overcrowded Text

Failure signal:

- Notes cover the main subject.
- The image feels full, noisy, or hard to breathe.
- High-density annotations appear on a simple single-subject photo.

Rule:

High density is only for collection subjects or clear roll-call scenes. Simple or hierarchical subjects need fewer, stronger notes.

## BC-09 Readability Support Too Weak Or Too Heavy

Failure signal:

- White handwriting sits on highlights, white clothes, lamps, white lines, or noisy texture and becomes hard to read.
- Readability backing becomes a UI card, label block, presentation tag, or heavy sticker.

Rule:

Protect readability lightly with placement, soft shadow, thin outline, or subtle breathing edge. It should still feel handwritten on the photo.

## BC-10 Random Decorative Doodles

Failure signal:

- Hearts, stars, sparkles, arrows, stickers, or cute symbols appear without serving the subject.
- Doodles become decoration piles or small illustrations on top of the photo.

Rule:

Doodles should express relationships. Use motion lines for person-pet play, grouping frames for preparation, flight lines for kites, and soft circles or arrows for small accidents.

## BC-11 Professional Naming Overconfidence

Failure signal:

- Exact model names, functions, or technical categories are invented.
- Uncertain gear is identified with confidence.
- Notes become long technical explanations.

Rule:

Use safe generic names when uncertain. Professional scenes should feel understood, not turned into manuals.

## BC-12 Example Copying

Failure signal:

- A positive example's composition, object choice, annotation wording, arrows, or doodle symbols are copied into a new image.
- The result looks like a variation of an example instead of a fresh reading of the current photo.

Rule:

Examples calibrate judgment only. Borrow the reasoning pattern, never the concrete layout, objects, or text.

## BC-13 Font-Rendered Fake Handwriting

Failure signal:

- Annotation text looks like a system font, subtitle, UI caption, or presentation text.
- Chinese characters share the same baseline, glyph rhythm, stroke width, and spacing even when slightly rotated or jittered.
- The result uses local font rendering, PIL `ImageFont`, system Chinese fonts, or typed text overlay as a shortcut for handwritten notes.
- The output optimizes for dimension or preservation checks but loses the organic handwritten feeling.

Rule:

Preservation is not enough. Moment Notes needs organic hand-drawn strokes on the original photo. A small pixel-size difference is less serious than losing the handwritten layer. If image editing changes the visible ratio, crop, subject positions, or base-photo quality, retry the image edit from the original photo; do not pass a local system-font overlay as a valid repair.

## Conservative Fallback

When unsure, choose fewer notes, clearer subject priority, safer object names, lighter doodles, and stronger original-photo preservation.
