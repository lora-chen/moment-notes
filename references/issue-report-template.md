# Issue Report Template

Use this file when the user says `report to issue:`. The goal is not only to describe the final bad result, but also to preserve the V6.3 decision trail so a maintainer can tell which workflow node failed.

Do not invent metadata. If the current host did not expose an item, write `not captured`.

Treat issue creation as a public action. Always show the public-safe draft to the user and obtain explicit confirmation before submitting it. Never attach a user photo, generated image, local path, or personal information unless the user separately confirms that the specific material is safe to publish.

## IR-01 Report Title

Use a short title that names the failure mode and scene.

Good patterns:

- `[V6.3] 咖啡小事故被写成物品标签`
- `[V6.3] 装备平铺没有形成阅兵感`
- `[V6.3] 人宠互动被拆成单独物体注释`

## IR-02 User Context

Record the user's original request and complaint.

Include:

- user request
- `report to issue:` feedback text
- whether the user wanted generation, analysis, retry, or comparison
- number of input images
- whether the image can be publicly attached

## IR-03 Result Summary

Summarize what was generated.

Include:

- output count
- whether each input image produced exactly one output
- whether a retry happened
- whether the source photo was preserved
- short description of visible annotations

## IR-04 Photo Diagnosis Meta

Carry forward the diagnosis node.

Include:

- emotional line
- scene state
- relationship summary
- subject mode: single subject, clear hierarchy, collection subject, or professional collection
- key subjects or object groups
- low-priority props
- quiet/readability-safe areas
- confidence notes, especially for professional or hard-to-name objects

This is the first place to check when the output emotion is wrong.

## IR-05 Annotation Strategy Meta

Carry forward the overlay planning node.

Include:

- intended annotation density
- local notes planned
- objects that should not receive standalone notes
- structural marks planned, such as outlines, grouping frames, arrows, flight lines, or motion lines
- decorative doodles planned
- which annotation rules were relevant, such as AP-01 density, AP-04 small accident comfort, or AP-05 collection roll-call

This is the first place to check when the emotion was understood but the marks were distributed badly.

## IR-06 Prompt Meta

Record how the final edit prompt was assembled.

Include:

- prompt template section used
- relationship-driven fill, collection roll-call fill, small-accident fill, or background-specific fill
- final instruction emphasis, such as preserve original photo, white handwriting layer, avoid redrawing, avoid copying examples
- any constraints that were missing or weakened

This is the first place to check when the plan was good but the generated result ignored it.

## IR-07 QA Meta

Record the post-generation check.

Include:

- failed QA IDs, such as QA-01 original photo preservation or QA-04 density and breath
- severity: pass, minor issue, serious failure
- retry decision: no retry, retry once, or retry already used
- if retried, what the retry was supposed to fix
- whether the final result still has residual risk

This is the first place to check when a bad output should have been caught before delivery.

## IR-08 Example Calibration Meta

If examples influenced the judgment, record only the calibration reference.

Include:

- relevant positive case IDs or names
- what was borrowed as judgment, such as relationship-first, collection roll-call, or small-accident comfort
- confirmation that exact composition, objects, annotations, and doodles were not copied

Do not attach private examples unless the user has confirmed they are public-safe.

## IR-09 Expected Vs Actual

Compare the intended behavior with the failed output.

Use this compact structure:

```text
Expected:
- ...

Actual:
- ...

Likely failed node:
- photo-diagnosis / annotation-patterns / prompt-template / qa-checklist / unknown
```

## IR-10 Manual Issue Draft

When direct GitHub issue creation is unavailable, output this shape:

```text
Title:
[V6.3] <failure mode + scene>

Body:
## User Context
...

## Result Summary
...

## V6.3 Workflow Metadata
### Photo Diagnosis
...

### Annotation Strategy
...

### Prompt
...

### QA
...

### Example Calibration
...

## Expected Vs Actual
...

## Attachments
- Public-safe image or screenshot: yes/no/not captured
```
