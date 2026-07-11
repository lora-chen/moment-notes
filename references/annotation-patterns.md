# Annotation Patterns

Use this file after `photo-diagnosis.md`. Diagnosis decides what the image is about; annotation patterns decide how many notes to write, which subjects receive notes, and what kind of handwritten marks support the emotion.

Rules are numbered for review and iteration. When commenting, refer to IDs such as `AP-01` or `AP-07`.

## AP-01 Density Follows Intent

Rule:

- Annotation density should follow the user's likely display intent, not only the number of visible objects.

Use:

- Single subject or large quiet space: 2-4 notes.
- Clear hierarchy: 3-5 notes, mostly around the strong subject, action, or state.
- Portrait, pet, or landscape: usually 3-5 notes focused on state, companionship, looseness, light, or air.
- Atmosphere-subject scenes, such as quiet storefronts, street corners, harbor distance, windows, roads, dusk, rain, or strong light-and-shadow: usually 2-4 notes. Let quiet space stay quiet.
- Low-saturation indoor daily scenes, such as bed/desk corners, laptop or tablet screens, coffee, books, fabric, perfume, and soft home light: usually 2-3 notes. Do not turn them into tabletop roll-call unless the user asks.
- Food spread, coffee table, tabletop collection, small objects, or travel street scene: usually 5-8 notes; rich frames can approach 9-10 if still breathable.
- Professional gear flat lay, packing checklist, or pre-departure equipment layout: usually 6-10 notes, and sometimes dense annotation is correct because the collection itself is the subject.

Avoid:

- Do not force sparse notes on an intentional collection, such as hiking gear prepared before departure.
- Do not force many notes on a simple portrait, single dish, or quiet landscape.

Example judgment:

- A hiking gear flat lay can feel like a gentle "roll call" or "阅兵": many key items are meant to be seen and checked.
- A person playing with a dog should stay lighter; the relationship matters more than labeling every background object.
- A quiet street corner or harbor view should use a few atmosphere notes around light, shade, distance, or the small pause of passing by.
- A quiet home desk or bed scene should use a few notes around rest, screen glow, soft fabric, and slow time. The visible objects support the mood; they are not all protagonists. One whole-scene note plus one or two mood-anchor notes is usually enough.

## AP-02 Do Not Distribute Notes Evenly

Rule:

- Do not give every visible object an equal annotation. Notes should follow the emotional line and subject priority.

Use:

- Give more notes to the emotional carrier: person + pet, spilled drink + recovery mood, gear collection, or sky + kites.
- Merge weak objects into one group note when they support the same feeling.
- Leave low-priority props unannotated unless they directly support the emotional line.

Avoid:

- Do not annotate "person, dog, grass, hat, sky" as separate labels when the real subject is shared outdoor play.
- Do not annotate every desk object in a spill scene.
- Do not give every kite its own joke if the park mood is the real subject.

Example judgment:

- In a kite park photo, a few distinctive kites can carry the upward mood, while the sky and people anchor the whole scene.
- In a spilled coffee photo, the cup, keyboard, and tools should connect back to comfort or recovery, not become isolated punchlines.

## AP-03 Write From The Emotional Line

Rule:

- Every local note should support the same emotional direction, even when it points to different objects.

Use:

- Start from the emotional line decided in diagnosis.
- Write notes from concrete angles: temperature, rhythm, relationship, movement, light, state, preparation, recovery, or care.
- Keep notes Chinese-first, short, handwritten, and conversational.
- Allow tiny jokes, comfort, or softness, but never sharp or hurtful remarks.

Avoid:

- Do not write objective labels, ad copy, tutorial copy, or caption-like explanation.
- Do not let local notes each tell a different story.
- Do not over-explain professional objects.

Example judgment:

- "安全感先装好" works better than a long gear explanation.
- "慢慢收拾就好" works better than a cleanup instruction.

## AP-04 Small Accident Comfort Pattern

Rule:

- For small accidents, the emotional sequence should be: acknowledge the accident -> comfort the viewer -> offer a light sense of recovery.

Use:

- Good emotions: reassurance, gentle repair, "it is okay", "protect what matters", "the day can continue".
- Mention nearby objects only when they support comfort, cleanup, or recovery.
- Keep the tone positive and soft.

Avoid:

- Do not make embarrassment, failure, clumsiness, or blame the main emotion.
- Do not turn the image into a technical cleanup guide.
- Do not overuse jokes if the image needs comfort first.

Example judgment:

- A spilled drink on a desk should feel like a small life accident being held gently.
- The keyboard, cup, calculator, or egg can be mentioned only if they connect back to reassurance or recovery.

## AP-05 Collection Roll-Call Pattern

Rule:

- For intentional collections, especially professional or pre-departure flat lays, notes can create a "roll-call" feeling.

Use:

- Group related items: warmth layer, rain protection, storage, safety, electronics, hygiene, navigation, food, recovery.
- Give each important group a short functional-emotional note.
- Use conservative names when uncertain.
- Let the viewer feel preparation, order, safety, and confidence.

Avoid:

- Do not treat an intentional gear layout as clutter.
- Do not invent exact models, technical categories, or functions.
- Do not let tiny accessories steal focus from key gear groups.

Example judgment:

- Hiking gear before departure can use higher density because each item is part of the story.
- The mood is not "many things"; it is "everything is ready, carefully checked, and quietly reliable".

## AP-06 Scene Bias

Rule:

- Apply scene-specific writing bias after deciding the emotional line.

Use:

- Portrait: write the person's current state, relationship, light, and atmosphere; do not only write "好看" or "漂亮".
- Food: write temperature, aroma, texture, color, portion, table relationships, and the safety of eating; do not only write "好吃" or "治愈".
- Travel and landscape: write looseness, air, light, distance, and being on the road; do not only label "山", "海", "云", or "天很蓝".
- Street corner, storefront, and window scenes: write passing-by warmth, shade, color, signs as mood anchors, and the feeling of a small pause; do not turn the image into store promotion or street-object labeling.
- Harbor, road, and distance scenes: write faraway calm, wind, horizon, waterline, mountain shadow, and route feeling; do not annotate every boat, pole, sign, or railing.
- Indoor daily / low-saturation home scenes: write quiet light, screen glow, fabric softness, bed/desk coziness, and the permission to slow down; do not make perfume, books, glasses, keyboard, cups, or coffee compete as separate lifestyle captions.
- Pets: write small actions, eyes, tail, companionship, and the relationship between pet and environment; do not only label the species.
- Gear and professional scenes: sound observant, not explanatory; focus on preparation, safety, order, and serious living.
- Park, kite, and open-sky scenes: write upward energy, openness, wind, watching, and playfulness; do not only label kite types or animals.

Avoid:

- Do not let background objects steal focus from a clear foreground pet, person, or action.
- Do not use one scene's style on another scene. A desk accident needs comfort; an outdoor play scene needs lightness.

## AP-07 Copy De-Duplication

Rule:

- Before generation, draft candidate notes and run a same-image de-duplication pass.

Use:

- If action words repeat, keep one and rewrite the rest.
- If adjectives repeat, keep the strongest one and change the others.
- If sentence templates repeat, change at least one.
- If two notes say nearly the same thing, keep the one closer to the high-priority subject and rewrite the other from a different angle.
- Keep the mood consistent after rewriting.

Avoid:

- Do not repeat the same comfort phrase across many objects.
- Do not use a chain of identical templates such as "X 也..." or "X 先...".

## AP-08 Doodles Should Express Relationships

Rule:

- Doodles and lines should express relationships, not decorate randomly.

Use:

- Person + pet interaction: motion curves, attention lines, light hearts, paw-like accents, or a path that connects the action.
- Gear roll-call: thin outlines, group frames, dotted borders, small check marks, route lines, tiny mountain or sun symbols.
- Small accident comfort: soft circles, gentle arrows, small sparkles, light hearts, or protective outlines around what matters.
- Park, kite, and open sky: flight lines, curved wind paths, tiny stars, paper-plane-like marks, or light cloud bubbles.
- Food and drink: steam, cup-rim line, small stars, satisfaction marks.

Avoid:

- Do not add symbols unrelated to the subject.
- Do not turn doodles into stickers.
- Do not use too many decorative hearts, stars, or warning marks.
- Do not cover the main subject with frames or doodles.

Example judgment:

- A dog running toward a person benefits from a curved motion path.
- A gear flat lay benefits from group frames.
- A spilled drink benefits from soft recovery marks, not alarm symbols.

## AP-09 Orientation And Placement

Rule:

- Text placement should respect the image orientation and visual quiet areas.

Use:

- Landscape images: arrange notes along natural horizontal reading paths.
- Portrait images: follow the vertical composition so the viewer does not need to rotate the image mentally.
- Atmosphere-subject images: place notes in existing negative space, along light/shadow edges, horizon lines, road/water paths, windows, awnings, or quiet sky. Use arrows only when a mood anchor needs help.
- Busy backgrounds: place notes in quieter areas and point back with arrows or curved lines.
- Bright or noisy backgrounds: use subtle readability protection from `style-dna.md`.

Avoid:

- Do not cover faces, pets, food centers, key gear, or action lines.
- Do not place white text over bright highlights or white objects.
- Do not let text blocks compete with the subject.

## AP-10 Atmosphere Carrier Pattern

Rule:

- When the diagnosis says atmosphere is the subject, annotate mood carriers rather than visible object names.

Use:

- Prefer 2-3 notes.
- Let one note name the whole state, such as "家里的光慢下来" or "慢一点也没关系".
- Let one or two notes point to real mood carriers, such as screen glow, soft bedding, shadow, window light, road, water, or horizon.
- Use decorative marks only to guide the eye through the atmosphere.

Avoid:

- Do not invent detached metaphors for random objects, such as calling a cup, coffee, perfume, keyboard, or book the main emotional device when it is only background support.
- Do not write object lifestyle captions that sound like a product flat lay.
- Do not add a note near every visually pleasing object.

Use:

- Pick 2-4 carriers: light/shadow, warm color, wind/air, horizon, road, water, window, storefront sign, awning, mountain line, small people, or a quiet empty area.
- Write notes that make the viewer feel the moment: "路过也认真", "夏天在转弯", "远一点也很稳", "阴影里有风", "今天慢一点".
- Use one larger emotional note if the image has a big quiet sky, wall, water, or shadow area.
- Let arrows, curves, and tiny marks follow natural scene lines instead of creating a new diagram.

Avoid:

- Do not label objects just because they are visible.
- Do not write travel-guide, store-promo, or postcard copy.
- Do not fill every empty area. Negative space is part of the feeling.
- Do not make all notes tiny; sparse scenes often need fewer but more legible notes.

Example judgment:

- A storefront in strong summer light can be about "passing warmth", not the sign itself.
- A harbor with mountains can be about distance and air, not identifying every boat.
