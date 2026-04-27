---
name: moment-notes
description: Create emotional hand-drawn annotations on photos with scene understanding, emotion mapping, and orientation-aware text layout. Use when generating lightweight image notes for daily sharing, especially when the user wants meaningful mood expression from a single moment photo.
---

# Moment Notes

Generate image annotations with three layers:
1. Visible elements in the photo
2. Scene understanding behind those elements
3. Emotional response that the viewer can feel

This skill is image-first. When image input is present, the first output should be the generated annotated image result, not a clarification round or a text-only draft.

## Workflow

1. If multiple images are uploaded, treat them as separate jobs by default.
2. For each image, read the photo and infer the scene context plus one dominant emotional line.
3. Scan the whole image for major visible details instead of limiting the generation to only a few named objects.
4. Decide whether the main viewing orientation is landscape or portrait.
5. Generate the annotated image first while preserving the original filter and visual style.
6. After image generation, optionally add one short emotional summary and three follow-up suggestions.

## Prompt Source

Use [references/prompts.md](references/prompts.md) as the prompt base.

## Update Preference

- This skill should prefer the latest version from the GitHub repository when the host environment supports remote sync or refresh.
- If the environment uses a local cached copy, the user should update that local copy from the repository before expecting new behavior.
- Repository source of truth: `https://github.com/foxbitcoo/moment-notes`

## Update Action

If the user asks to update `moment-notes`, the intended action is:
1. Pull or fetch the latest skill files from `https://github.com/foxbitcoo/moment-notes`
2. Sync the latest `SKILL.md`, `README.md`, `agents/openai.yaml`, and `references/prompts.md`
3. Replace the local installed copy of the skill with those latest files

If the host environment cannot perform remote sync by itself, it should instruct or trigger a repository refresh first, then update the local installed copy from that refreshed source.

## Triggering

This skill can be activated in three equivalent ways:
1. Explicit skill tag: `$moment-notes`
2. Skill name mention: `use moment-notes`
3. Natural language intent: `add emotional hand-drawn notes to this photo`

Notes:
- In tools like OpenClaw, `/` is usually reserved for built-in commands (for example `/status`).
- `$` is a clear visual marker for explicit skill activation, but it is optional.

## Hard Rules

- When the user provides one or more images, do not ask for confirmation before the first generation unless the user explicitly requests a planning round.
- When multiple images are provided, process them one by one and return one generated result per image.
- Never merge multiple uploaded images into one output unless the user explicitly asks for collage, merge, or composition.
- Do not replace the first-generation step with a txt file, note file, or text-only response.
- Keep the source image filter, color mood, and overall visual character intact; annotations should feel overlaid, not rebuilt from scratch.
- Do not compress the image-generation prompt into a tiny fixed object list. The model should cover the main visible elements across the whole frame.

## Output Requirements

- Keep line style lightweight and hand-drawn in white.
- Keep language short, conversational, and emotional.
- Keep all local notes aligned with one emotional direction.
- Keep text layout consistent with landscape or portrait viewing.
- For detail-rich tabletop or daily-object scenes, prefer rich annotation density when it does not block readability.
- Make the annotated image the first output when image generation is possible.
- End with one summary sentence that emotionally responds to the image.
