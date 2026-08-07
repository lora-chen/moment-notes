# Style DNA

Use this file to control the visual result after diagnosis and annotation planning. The output must feel like handwritten notes added to the original photo, not a redesigned poster or a remade image.

Rules are numbered for review and iteration. When commenting, refer to IDs such as `SD-01` or `SD-06`.

## SD-01 Preserve The Original Photo

Rule:

- The uploaded photo is the base. Do not redraw, replace, beautify, restyle, crop, recompose, or generate a similar new image.

Must preserve:

- filter, color mood, exposure, saturation, contrast, sharpness, grain, crop ratio, and atmosphere
- original visual proportion, resolution feel, perceived sharpness, compression texture, motion blur, focus softness, and low-light grain
- people, faces, bodies, gestures, clothes, pets, food, gear, tools, desk objects, skyline, kites, background details, and object positions
- existing watermarks, visible text, signs, labels, and natural image imperfections

Avoid:

- Do not change faces, pet pose, gear type, tabletop object layout, kite shape, drink spill shape, or background location.
- Do not visibly crop, stretch, pad, downsample, upscale, pixelate, posterize, over-compress, blur, denoise, sharpen, or smooth the base photo.
- Small pixel-dimension differences or subtle natural light/color drift are acceptable if the result still feels like the same photo with handwriting added.
- Do not significantly restyle the photo into a cleaner, prettier, more cinematic, more illustrated, or more poster-like image that no longer feels like the user's original capture.
- Do not use pure text-to-image remake behavior unless the user explicitly asks for a remake.

## SD-02 Handwritten Overlay Layer

Rule:

- Add only a warm handwritten annotation layer on top of the original photo.

Use:

- white or warm-white thin handwritten Chinese notes
- slightly loose one-stroke handwriting, like a friend gently wrote on the photo
- organic handwritten strokes with irregular pressure, imperfect stroke starts/ends, and natural character rhythm
- small natural variation in line thickness, spacing, and curve; not mechanical or perfectly typeset
- light one-stroke arrows, curves, dotted lines, circles, and small doodles
- short, conversational, emotionally supportive text
- visual marks that feel hand-drawn and slightly casual
- a few tiny pauses, curves, or soft endings that make the annotation feel relaxed

Avoid:

- Do not use heavy stickers, UI labels, big title blocks, poster typography, infographic panels, or commercial callouts.
- Do not make the handwriting look like printed subtitles, app UI, or presentation text.
- Do not make the handwriting too sharp, too regular, too bold, or too cleanly vectorized.
- Do not use system-font text, font-rendered handwriting, subtitle-like text, or typed Chinese with artificial jitter as a substitute for real handwritten strokes.
- Do not cover the main subject with text.

## SD-03 Readability Without Cards

Rule:

- Handwriting must stay readable at social-media size, but readability protection should be quiet.

Use:

- warm white instead of pure white when the background is harsh
- very light dark outline, soft shadow, subtle blank edge, or tiny translucent backing
- quiet background areas plus arrows or curved lines pointing back to subjects
- for sparse atmosphere-subject images, use fewer notes but make each note clearly legible; sparse should not mean tiny, transparent, or fading into sky/water/highlights

Avoid:

- Do not place white text directly over bright lights, white highlights, white clothes, white lines, or dense texture.
- Do not make atmosphere notes so faint that they become decorative texture.
- Do not create heavy cards, blocks, bubbles, labels, slides, or poster panels just to make text readable.
- Do not let readability backing become more visible than the handwriting.

Tone:

- Readability support should feel like part of the handwritten layer, not a separate UI component.
- If a backing is needed, it should be barely there: just enough to help the words breathe.

## SD-04 Frames And Outlines Are Structural

Rule:

- Thin frames, outlines, and dotted borders are allowed when they clarify the subject relationship or object grouping.

Use:

- thin white or warm-white outlines around key subjects when the background is visually busy
- light contour lines around a person, pet, important gear, or flying object
- dotted group frames for gear roll-call, tabletop collections, and small accident recovery areas
- soft circles or partial outlines to protect what matters in a messy scene
- hand-drawn imperfect borders that feel like "圈重点", not precise masks

Avoid:

- Do not make outlines look like cutout stickers.
- Do not use thick borders, glowing stickers, heavy halos, or harsh object masks.
- Do not trace the subject so tightly that it feels like the object has been cut out and pasted back.
- Do not frame every visible object.
- Do not outline low-priority props unless they directly support the emotional line.

Example judgment:

- A person and dog in green foliage may need light outlines so the relationship is readable.
- A hiking gear flat lay may need group borders to create a roll-call feeling.
- A spilled drink may need soft containment lines, not alarm-like warning marks.

## SD-05 Separate Decorative Doodles From Structural Marks

Rule:

- Decorative doodles should stay sparse; structural marks can appear more often when they organize the image.

Decorative doodles:

- hearts, stars, suns, tiny faces, paw marks, sparkles, steam, small flowers
- use only when they strongly match the emotion
- keep them few and light
- make them feel like small emotional breaths, not visual rewards or sticker effects

Structural marks:

- arrows, curved motion paths, dotted routes, subject outlines, group frames, soft circles, check marks
- may appear more often when they help the viewer understand movement, relationship, preparation, or recovery
- must remain thin and quiet
- should help the eye move gently, not force it through a diagram

Avoid:

- Do not turn the photo into a sticker sheet.
- Do not add random decorative icons.
- Do not let structural marks become a dense diagram.

Good feeling:

- The viewer should notice the photo first, then slowly discover the small handwritten care around it.
- Doodles should make the moment softer, not louder.

## SD-06 Background-Specific Readability Strategy

Rule:

- Choose placement and marks according to the background type.

Use:

- Green foliage or grass: use quiet negative areas, light outlines around people/pets, and gentle motion curves.
- Gear flat lay or busy tabletop: group related items with dotted borders or thin frames; place notes near groups instead of on top of key details.
- Desk accident or spill: use soft circles, gentle arrows, and small recovery marks; avoid alarm-like warning symbols.
- Open sky or park: keep large sky areas breathable; use airy flight lines, cloud-like bubbles, or sparse notes.
- Night, red light, or complex light: use warm-white text, subtle outline, or soft shadow.
- Warm food or cafe scenes: let steam, small curves, and quiet notes carry the warmth; avoid making the table look like an ad layout.
- Portrait or pet close-ups: leave faces and eyes clean; place notes around posture, gaze, light, or surrounding quiet space.

Avoid:

- Do not write densely across a large clean sky.
- Do not write directly on detailed gear labels, faces, pet eyes, food centers, or important object edges.
- Do not over-decorate already rich backgrounds.

## SD-07 Orientation And Reading Path

Rule:

- Text layout should match the photo's natural viewing direction.

Use:

- Landscape images: arrange notes along a left-to-right or subject-to-subject reading path.
- Portrait images: follow the vertical composition and avoid rotated text that makes the viewer turn their head.
- Action scenes: use curves and arrows to guide the eye through the action.
- Collections: use grouped reading zones so the viewer can scan item clusters.

Avoid:

- Do not scatter notes randomly.
- Do not make text compete with the action path.
- Do not stack too many notes in one corner if the rest of the image has usable quiet space.

## SD-08 Breathable Final Image

Rule:

- The photo should still breathe after annotation.

Use:

- leave meaningful blank or quiet areas
- keep notes short
- let the original photo remain visually dominant
- use fewer stronger notes for simple images
- allow higher density only for intentional collections or rich scenes with enough space
- leave some emotional silence; not every good feeling needs to be written out
- prefer small, warm, specific notes over large declarations
- let the annotation feel like it arrived after looking at the photo for a moment

Avoid:

- Do not make the photo feel like a full-page worksheet.
- Do not cover the image with handwriting just because many objects are visible.
- Do not let emotional warmth become visual clutter.

Good feeling:

- The final image should feel light, kind, and a little personal.
- It should not shout "I annotated this"; it should quietly help the photo say what it was already feeling.
