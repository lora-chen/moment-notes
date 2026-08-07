# QA Checklist

Run this after each generated image. QA decides whether the image can be delivered, needs one local edit/regeneration, or should be rejected as a bad result.

Rules are numbered for review and iteration. When commenting, refer to IDs such as `QA-01` or `QA-12`.

## QA-01 Original Photo Preservation

Must pass:

- The uploaded photo is still the base image.
- The original filter, color mood, exposure, composition, crop ratio, object positions, and atmosphere are preserved.
- Output keeps the same visual proportion, aspect ratio, crop feeling, and subject positions. Tiny pixel-dimension differences are acceptable if the image still reads as the same photo and quality is preserved.
- People, faces, bodies, pets, food, gear, desk objects, kites, skyline, background details, visible text, and watermarks did not change identity or location.
- Shadows, highlights, sky, water, road, storefront color, window reflections, film grain, blur, and low-light mood did not get "cleaned up" or beautified.
- The base photo did not become softer, more pixelated, more posterized, more compressed, over-denoised, over-sharpened, or lower-detail than the input.
- Only handwritten notes, doodles, arrows, circles, outlines, dotted lines, or tiny readability protection were added.

Failure signals:

- The source photo was redrawn, heavily beautified, restyled, visibly cropped, stretched, padded, recomposed, or significantly changed.
- Aspect ratio, crop, padding, subject position, or visual proportion changes noticeably.
- A person, pet, object, dish, gear item, kite, spill shape, or background detail changed identity.
- The photo becomes sharper, smoother, brighter, darker, more saturated, more cinematic, or more polished in a way that changes the user's original moment or makes it feel like an AI-remade photo.
- The photo becomes blurry, pixelated, posterized, blocky, visibly recompressed, or loses original fine detail.
- The image-generation model invents cleaner textures, changes signage, removes noise, changes shadows, or redraws atmosphere carriers.
- The output looks like a new AI image rather than the original photo with handwritten notes.

Retry:

- Regenerate from the original uploaded image and explicitly preserve it. Do not continue from the altered image.

## QA-02 Emotional Line And Relationship

Must pass:

- The whole image has one coherent emotional line.
- The important relationship from diagnosis is still visible: person + pet, object + accident, gear collection, sky/wind + kites, food + comfort, or scene + people.
- Local notes support the same emotional direction.

Failure signals:

- The notes feel like separate object labels instead of one emotional story.
- The image identifies objects but misses the relationship between them.
- The mood becomes cold, sarcastic, blaming, or too objective.

Retry:

- Keep the strongest emotional line and rewrite notes around the relationship, not around isolated objects.

## QA-03 Subject Priority

Must pass:

- The main subject receives the main attention.
- High-priority subjects are annotated or visually connected when needed.
- Low-priority props do not become independent jokes, protagonists, or visual anchors.

Failure signals:

- A spoon, mat, wall, ordinary device, edge prop, tiny accessory, or generic background item steals focus.
- The foreground person, pet, food, spill, gear collection, or kite scene loses attention.
- Too many visible objects receive notes just because they are visible.

Retry:

- Remove low-priority prop notes and re-center the true subject or emotional relationship.

## QA-04 Density And Breath

Must pass:

- Annotation count matches image intent and available space.
- Simple images stay light.
- Intentional collections, gear flat lays, or rich scenes can be denser if still readable.
- The final image still breathes.

Failure signals:

- The image feels like a full-page worksheet.
- Notes cover the main subject or visual path.
- A simple image has too many annotations.
- A collection image is too sparse and fails to show the intended roll-call or preparation feeling.

Retry:

- If cluttered, reduce notes to the strongest set and remove weak doodles.
- If an intentional collection is under-read, add or rebalance notes around key item groups while staying readable.

## QA-05 Readability

Must pass:

- Chinese notes are readable at social-media size.
- White or warm-white text does not disappear into highlights, white objects, bright lamps, or busy texture.
- Sparse atmosphere notes are still clearly readable; they are not tiny, transparent, or fading into sky, water, haze, or pale walls.
- Readability protection is subtle and does not become UI.

Failure signals:

- Text sits on lights, highlights, white areas, dense gear detail, faces, pet eyes, food centers, or important object edges.
- Atmosphere-subject text becomes so faint that it reads as background texture instead of handwriting.
- Text is too small, too tilted, too dense, or too regular.
- Shadows, backing, or outlines become heavy labels or cards.

Retry:

- Move text to quieter areas, use arrows back to the subject, or add only subtle readability protection.

## QA-06 Structural Marks And Doodles

Must pass:

- Structural marks clarify relationships, movement, object groups, preparation, or recovery.
- Decorative doodles are sparse and emotionally relevant.
- Frames and outlines feel hand-drawn and light.

Failure signals:

- Frames look like cutout stickers, heavy halos, precise masks, or pasted white borders.
- Doodles feel random, loud, or like sticker rewards.
- Structural marks turn into a dense diagram or flowchart.
- The marks cover the subject instead of helping it.

Retry:

- Remove decorative doodles that do not serve the emotional line.
- Thin or reduce outlines and frames.
- Keep only structural marks that guide the eye or clarify the relationship.

## QA-07 Copy Quality

Must pass:

- Notes are short, Chinese-first, warm, and conversational.
- Wording is diverse within the same image.
- The copy sounds like emotional response, not objective labeling.
- Text visually reads as organic handwriting, not a system font or subtitle layer.

Failure signals:

- Repeated verbs, adjectives, or sentence templates.
- Long explanations, ad copy, tutorials, or caption-like text.
- Notes only say object names such as "狗", "杯子", "风筝", "山", or "天空".
- Chinese characters have uniform font glyphs, consistent baseline, even stroke width, subtitle-like spacing, UI-text polish, or artificial per-character jitter that still looks typed.
- The output was repaired with local font rendering instead of regenerated as a handwritten layer.

Retry:

- Rewrite from different angles: temperature, rhythm, relationship, light, state, preparation, recovery, or care.
- Keep only the notes closest to the emotional line.
- If the visual problem is font-rendered text, regenerate from the original photo with a true handwritten annotation layer. Do not use local system-font overlay as the repair.

## QA-08 Professional And Collection Accuracy

Must pass:

- Professional objects are recognized carefully.
- Uncertain objects use safe generic names.
- Important item groups in intentional collections are noticed.
- Gear flat lays and pre-departure layouts can create a clear roll-call feeling.

Failure signals:

- Professional gear is confidently misnamed.
- The image explains equipment too much and loses emotional warmth.
- Important gear groups are ignored while small accessories steal attention.
- The collection looks like clutter instead of preparation.

Retry:

- Replace risky exact names with generic names.
- Rebalance notes around key groups: warmth, rain protection, safety, storage, electronics, hygiene, recovery, food, or navigation.

## QA-09 Small Accident Comfort

Must pass:

- A small accident is acknowledged without blame.
- The notes comfort the viewer and suggest gentle recovery.
- Nearby objects support the comfort line instead of becoming isolated jokes.

Failure signals:

- The main emotion becomes disaster, failure, embarrassment, or mockery.
- The annotations become a cleanup tutorial.
- Jokes overpower comfort.
- Every desk object gets a standalone note.

Retry:

- Rewrite around: acknowledge accident -> comfort viewer -> light recovery.
- Remove jokes or object labels that do not help reassurance.

## QA-10 Example Calibration

Must pass:

- If the scene resembles a positive example, the result reuses the judgment pattern, not the exact composition or wording.
- The image learns from examples such as outdoor person + pet, spilled drink comfort, hiking gear roll-call, or park kites uplift.

Failure signals:

- The result copies example notes, object choices, layout, doodle placement, or composition too directly.
- The result ignores the relevant positive-case lesson.

Retry:

- Keep the judgment, change the expression. Use the current image's own subjects, relationships, and mood.

## QA-11 Atmosphere Subject

Must pass:

- If the diagnosis says atmosphere is the subject, the final notes preserve quietness and space.
- Notes point to mood carriers such as light, shadow, air, distance, road, water, sky, window, sign, awning, or horizon.
- The image uses fewer notes, usually 2-4, unless the scene has a clear secondary subject that needs one extra anchor.
- Empty areas still feel intentional, not unused because the model forgot to annotate.
- Low-saturation indoor daily scenes keep a quiet, sparse, home-mood reading instead of becoming a tabletop object showcase. Usually 2-3 notes is enough.

Failure signals:

- The output labels storefront objects, boats, poles, mountains, signs, or railings as isolated facts.
- The output turns a quiet home scene into object lifestyle captions, giving coffee, perfume, cup, glasses, keyboard, book, or screen separate decorative meanings that do not serve the same mood.
- The scene turns into travel-guide copy, store promotion, postcard caption, or generic landscape praise.
- The quiet space is filled with too many small notes, stars, arrows, or decorative marks.
- The notes miss the main atmosphere and only describe visible objects.

Retry:

- Remove object labels and rewrite around the strongest atmosphere carriers.
- Keep one main emotional note and 1-3 small supporting notes.

## QA-12 Retry Decision

Use a retry only for serious failures.

Retry or locally edit at most once when:

- original photo changed
- aspect ratio, crop, padding, subject position, or visual proportion changed noticeably
- emotional relationship was missed
- main subject priority failed
- text is unreadable
- image is too cluttered or badly under-read
- structural marks became stickers or diagrams
- copy became labels, repeated, or cold
- annotation text looked like system-font, subtitle, UI, or font-rendered fake handwriting
- professional objects were misnamed
- small accident became blame or disaster
- atmosphere-subject photos became object labels or over-annotated travel postcards

Do not keep generating candidates. One default generation plus at most one QA retry is the rule.
