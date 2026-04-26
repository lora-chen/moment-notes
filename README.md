# Moment Notes（此刻小记）

`moment-notes` is a Codex skill for emotional photo annotations.
It turns a single image moment into lightweight hand-drawn notes with:

- scene understanding
- emotion mapping
- orientation-aware text layout (landscape vs portrait)

## Install in Codex

Use the skill installer with this GitHub URL:

```bash
python <path-to-skill-installer>/scripts/install-skill-from-github.py --url https://github.com/lora-chen/moment-notes/tree/main
```

If your Codex environment already supports `$skill-installer`, you can ask:

```text
Install this skill from GitHub:
https://github.com/lora-chen/moment-notes/tree/main
```

After install, restart Codex to load the new skill.

## How to Trigger

You can trigger it in two ways:

1. Explicitly mention skill name:
```text
Use $moment-notes to annotate this photo.
```

2. Natural language request that matches the skill description:
```text
Please add emotional hand-drawn notes to this image with scene understanding.
```

## What It Does

- Understands visible objects and hidden scene context
- Builds one unified emotional line for the image
- Keeps all local notes aligned with the same mood
- Matches text direction to image orientation
- Ends with one emotional summary sentence

## Prompt Source

Core prompt templates are in:

- `references/prompts.md`

## Repository Structure

```text
moment-notes/
  SKILL.md
  agents/openai.yaml
  references/prompts.md
  README.md
```

## Notes

- Public repo is required for easy open install by other users.
- If the repo is private, users need access permission or token.
