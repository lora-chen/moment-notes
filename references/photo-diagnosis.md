# Photo Diagnosis

Before writing local annotations, diagnose what the image is emotionally asking for.

## Emotional Line

Pick one gentle emotional line for the whole image. The emotional line should come from the scene state, not directly from object names.

Ask first: what is happening here, and what feeling does this situation need?

Examples:

- a small moment of rest
- prepared and steady before departure
- a warm meal that makes the day softer
- a companion quietly being present
- a messy life moment that still deserves kindness
- a professional setup that feels careful and reliable
- a shared outdoor action that makes the day feel lighter
- a small accident that needs comfort before cleanup
- an open park scene that lifts the mood upward

The line should respond to the image, not objectively summarize it.

Do not derive emotion by naming objects. A cup, keyboard, dog, kite, or backpack is only the raw material. The emotional line comes from the situation: a spill that needs reassurance, a person and pet playing together, gear being checked before departure, or wind and sky making people feel more open.

## Relationship First

Before listing objects, identify the important relationships in the image.

Useful relationship types:

- person + pet: shared action, companionship, attention, play, waiting, protection
- person + object: preparation, care, effort, repair, reward, ritual
- object + accident: what happened, what needs comfort, what should be protected
- object + object: a collection forming a shared purpose, such as gear before hiking or dishes on a table
- scene + people: how the place changes the mood, such as a park, trail, cafe, desk, street, or home
- sky/wind/light + subject: openness, upward energy, movement, warmth, quietness
- atmosphere + place: when the main subject is not one object, but light, color, weather, distance, shade, storefront warmth, or a road/harbor/street corner inviting the viewer to slow down

Examples:

- A person and border collie outdoors is not "person + dog + grass". It is the playful relationship between the person and dog, plus the lightness of being outside.
- A spilled drink on a desk is not "cup + keyboard + calculator". It is an everyday accident that needs reassurance and a gentle recovery mood.
- A park with many kites is not "many kites". It is sky, wind, city edge, people watching, and flying objects creating an upward feeling together.
- A quiet street corner or harbor view is not "sign + window + mountain". It is the temperature of the light, the distance, and the small pause the place creates.

If the relationship is clear, annotations should support that relationship instead of giving every object an isolated note.

## Subject Mode

Classify every photo into one mode before choosing annotation density.

- Single subject: one clear person, pet, object, dish, or scene focus. Use fewer notes.
- Clear hierarchy: one strong foreground subject with weaker background context. Write mostly around the strong subject.
- Collection subject: many items together form what the user is showing, such as a food spread, tabletop, street scene, or gear layout.
- Professional collection: gear, tools, workspaces, or domain-specific scenes where item recognition matters, such as climbing, hiking, diving, cycling, camping, photography, surgery, lab, or workbench.
- Atmosphere subject: no single object dominates; the scene mood comes from light, color, space, weather, distance, signs, windows, water, mountains, or people being small in the frame. Use sparse notes and let the image breathe.

## Atmosphere As Subject

Some photos do not need object-by-object interpretation. The subject is the atmosphere.

Treat atmosphere as the main subject when the image looks like:

- a low-saturation indoor daily scene, bed/desk corner, quiet home table, laptop/tablet screen, book, coffee, fabric, shadow, or soft private pause
- a quiet street corner, storefront, cafe exterior, alley, market edge, or window scene
- a harbor, mountain distance, road, train/bus view, open sky, dusk, rain, or strong light-and-shadow scene
- a wide travel photo where people or objects are small and the place carries the emotion
- a photo whose strongest feeling is "停一下", "透口气", "夏天来了", "路过也很好", or "远一点也安心"

In these cases, identify atmosphere carriers instead of forcing object labels:

- light and shadow
- color temperature
- air, wind, humidity, heat, quietness
- distance, horizon, window, road, water, sky, mountain line
- a sign, awning, table, boat, chair, or doorway only when it anchors the mood

Use fewer notes, usually 2-4. Notes should point to the mood carriers, not label every visible object. Leave large quiet areas open unless a single small note helps the image feel more personal.

For quiet indoor daily scenes, do not treat every tabletop object as a collection subject just because many objects are visible. The emotion usually comes from home light, low saturation, screen glow, fabric softness, and a private slow moment. Keep coffee, perfume, glasses, book pages, keyboard, and cup as supporting mood anchors unless the user explicitly asks for a tabletop roll-call.

Do not turn atmosphere scenes into travel guides, storefront ads, landscape labels, or object-by-object lifestyle captions. "山影在等风" is better than "远处是山"; "路过也很认真" is better than naming a sign; "家里的光慢下来" is better than giving every cup/book/perfume its own metaphor.

## Collection As Subject

Sometimes a collection is not background clutter. The collection itself is the thing the user wants to show.

Treat the collection as the main subject when the image looks like:

- gear arranged before departure
- food spread or drink table
- tabletop objects intentionally displayed
- packing, checklist, haul, workspace, toolkit, or flat lay
- professional preparation where each item has a role

In these cases, create a "roll-call" feeling: identify item groups, notice their purpose, and give each important group a short emotional function. This can feel like a gentle "阅兵" before action: every key item is seen, named safely, and mentally checked.

High annotation density is acceptable for these scenes when the frame has room and the collection is intentionally displayed. The goal is not minimalism; the goal is readable preparation and care.

Do not use this rule for random messy backgrounds. A collection becomes the subject only when the arrangement or user intent suggests "look at these things together".

## Visible Object List

Create a compact internal list:

- main subject
- supporting objects
- background context
- likely low-priority props
- uncertain professional objects that need conservative naming

Do not output the list unless the user asks for analysis.

The object list should drive the overlay strategy:

- choose which objects deserve notes
- group similar objects when individual labels would be too dense
- mark low-priority props that should not steal focus
- identify uncertain items that need generic names
- connect objects back to the emotional line

For collection subjects, list item groups instead of every tiny item. For relationship-driven photos, list the relationship first and objects second.

## Object Priority

Write the emotional carriers first, then the environment.

- High priority: people, pets, food subject, main action, important light, works or gear the user clearly wants to show.
- High priority in atmosphere-subject photos: the strongest light/shadow area, open sky, road or water path, horizon, doorway/window/storefront warmth, and any small human trace that makes the place feel lived-in.
- Medium priority: environmental objects that form a relationship with the subject, such as a bag on a mountain trail, a drink beside hotpot, or a dog in a gym.
- Low priority: spoon, mat, ordinary equipment, wall, edge decoration, generic background item, and props with no story. Do not give these standalone emotional notes unless they are unusually prominent or strongly related to the subject.

Visible does not mean worth annotating.

## Professional Scenes

Recognize important gear when confident, but stay humble.

- Outdoor and sport scenes: rope, carabiner, harness, helmet, backpack, rain shell, warm layer, first-aid kit, camera, bike parts, tent, stove.
- Medical, lab, photography, and workbench scenes: main tools and work relationships.
- If the exact item is uncertain, use a safer generic name. For example, use "保护器/下降器" instead of a specific belay-device model, or "锁扣/连接扣" instead of a precise carabiner type.
- Professional notes should carry emotion, such as "安全感先装好", "出发前的认真", or "每一样都在托底". Do not write long explanations.
