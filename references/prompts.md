# Moment Notes V6.3 Prompt Index

This file is kept as a compatibility index for older installs that look for `references/prompts.md`.

Current official prompt: V6.3, scaffolded references and QA reflection.

Use these files instead of treating this file as the full prompt:

- `style-dna.md`: visual DNA, original-photo preservation, handwritten overlay style, readability.
- `photo-diagnosis.md`: emotional line, subject mode, visible object list, object priority.
- `annotation-patterns.md`: density, copy de-duplication, scene bias, subject-related doodles.
- `prompt-template.md`: single-image edit prompt template.
- `qa-checklist.md`: post-generation checks and at-most-one-regeneration rules.
- `bad-cases.md`: explicit failure patterns to avoid.
- `issue-report-template.md`: metadata schema for `report to issue` feedback.
- `v6.3-rule-map.md`: converged rule map for reviews, comparisons, and test acceptance.

The workflow is: read the photo, diagnose the emotion and objects, build an overlay strategy, generate one edited result per input image, run QA, and retry at most once only for serious failures.
