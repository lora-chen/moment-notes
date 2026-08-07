# Moment Notes（此刻小记）

[![skills.sh](https://skills.sh/b/foxbitcoo/moment-notes)](https://skills.sh/foxbitcoo/moment-notes/moment-notes)

一句话描述：
把照片里的“一个时刻”变成有情绪的轻注释，适合朋友圈和社交平台分享。

One-line description:
Turn a photo moment into lightweight emotional notes for social sharing.

`moment-notes` 是一个用于图片情绪注释的 Codex 技能。  
它会把一张照片中的瞬间，转成更有表达力的手绘感注释内容，核心能力包括：

- 场景理解
- 情绪映射
- 横竖屏视角一致的文字排布

`moment-notes` is a Codex skill for emotional photo annotations.
It turns a single image moment into lightweight hand-drawn notes with:

- scene understanding
- emotion mapping
- orientation-aware text layout (landscape vs portrait)

## 当前正式版 / Current Version

当前正式提示词为 V6.3：脚手架拆分 + QA 反思版。

V6.3 保留 V6.2 的主体优先级、注释密度自适应、复杂背景可读性、专业装备识别、主体相关手绘符号和同图文案去重规则，同时把脚手架拆成可按需读取的 reference 资产。它会先判断照片情绪主线、主体类型、关键物品 list 和低优先级道具，再生成 overlay 策略；每张输入图默认只生成 1 张，生成后按 QA 清单检查，只有严重失败时才最多重绘 1 次。

Current official prompt: V6.3, scaffolded references and QA reflection.

V6.3 keeps V6.2's subject priority, adaptive annotation density, readability protection, professional gear handling, subject-related doodle symbols, and same-image copy de-duplication, then splits the workflow into reference assets. It diagnoses the emotional line, subject mode, key object list, and low-priority props before building an overlay strategy. Each input image gets one default generation; QA failures may trigger at most one retry.

## V6.3 架构 / Architecture

V6.3 不再依赖单一长提示词，而是一个轻量入口 + 多个可按需读取的 reference 节点。

V6.3 no longer depends on one long prompt. It uses a lightweight entry point plus modular reference nodes that are read only when needed.

```text
SKILL.md
  -> photo-diagnosis.md
  -> annotation-patterns.md + style-dna.md
  -> prompt-template.md
  -> qa-checklist.md + bad-cases.md
  -> issue-report-template.md
```

节点职责：

- `photo-diagnosis.md`：先判断情绪主线、关系、主体模式、物品组和低优先级道具。
- `annotation-patterns.md`：决定写多少、写哪里、哪些对象保持沉默、手绘符号如何服务关系。
- `style-dna.md`：约束视觉气质，保护原图，只做白色手写层和轻量可读性处理。
- `prompt-template.md`：把前面的诊断和策略组装成单张图片编辑提示词。
- `qa-checklist.md` + `bad-cases.md`：生成后检查；严重失败时最多重绘一次。
- `issue-report-template.md`：当用户说 `report to issue:` 时，上报节点 meta，方便回溯。

核心链路：

```text
Photo Diagnosis
  -> Annotation Strategy
  -> Prompt Assembly
  -> Single Generation
  -> QA Reflection
  -> Issue Meta
```

## 通用安装（IDE / Agent） / Universal Install (IDE / Agent)

如果你不是只用 Codex，可以直接用下面这条通用方式：
If you are not using only Codex, use this universal setup:

```bash
git clone https://github.com/foxbitcoo/moment-notes.git
```

然后在你的 IDE / Agent 工具里，把 `moment-notes` 目录作为技能目录或本地能力目录加载。  
Then load the `moment-notes` folder in your IDE/agent as a local skill/capability directory.

常见用法（统一思路）：
Common pattern:
- Cursor: add this repo as a local prompt/skill source
- Claude Code: reference this repo folder as a reusable skill prompt pack
- Codex: install from GitHub URL or copy folder into your skills directory

## 在 Codex 中安装 / Install in Codex

使用下面的 GitHub 地址安装：
Install with this GitHub URL:

```bash
python <path-to-skill-installer>/scripts/install-skill-from-github.py --url https://github.com/foxbitcoo/moment-notes/tree/main
```

如果你的 Codex 环境已经支持 `$skill-installer`，也可以直接让它安装：
If your Codex environment already supports `$skill-installer`, you can ask:

```text
Install this skill from GitHub:
https://github.com/foxbitcoo/moment-notes/tree/main
```

安装后请重启 Codex，让技能生效。  
After install, restart Codex to load the new skill.

## 更新技能 / Update the Skill

中文：
- 这个 skill 的最新版本以 GitHub 仓库为准：
  `https://github.com/foxbitcoo/moment-notes`
- 如果用户的指令是“更新这个 moment-notes skill”，默认目标应该是：
  从这个 GitHub 仓库拉取最新版本，再同步覆盖本地安装的 skill 文件
- 如果你是通过 `git clone` 使用：

```bash
git pull origin main
```

- 如果你是通过 Codex 的 GitHub 安装方式使用，更新后建议重新执行一次安装命令，让本地副本覆盖到最新版本。
- 如果你的 Agent / IDE 支持远程仓库同步或 refresh，请优先从这个仓库地址拉取最新版本，而不是继续使用旧的本地缓存。
- 如果你的 Agent 支持 SessionStart 自动更新，也可以让它在新会话开始时自动同步本技能。

English:
- The source of truth for this skill is the GitHub repository:
  `https://github.com/foxbitcoo/moment-notes`
- If the user's intent is "update this moment-notes skill", the default action should be:
  pull the latest version from this GitHub repository, then sync and overwrite the local installed skill files
- If you use a cloned copy:

```bash
git pull origin main
```

- If you installed it through a GitHub-based Codex skill install flow, run the install command again after updates so the local copy is refreshed.
- If your Agent / IDE supports remote sync or refresh, prefer pulling the latest version from this repository instead of relying on an old local cache.
- If your agent supports SessionStart auto-update, it can also sync this skill automatically when a new session starts.

## 如何触发 / How to Trigger

你可以用三种方式触发：
You can trigger it in three ways:

1. Explicitly mention skill name:
```text
Use $moment-notes to annotate this photo.
```

2. Mention skill name without `$`:
```text
Use moment-notes to annotate this photo.
```

3. Natural language request that matches the skill description:
```text
Please add emotional hand-drawn notes to this image with scene understanding.
```

调用符号说明（OpenClaw/Codex）:
- `/` 一般用于工具内置命令（例如 `/status`、`/new`）。
- `$moment-notes` 是显式技能调用标记，更清晰，但不是强制。
- 不写 `$` 也可以，只要语义明显（如“用 moment-notes 处理这张图”）。

Prefix notes (OpenClaw/Codex):
- `/` is usually reserved for built-in tool commands.
- `$moment-notes` is an explicit skill marker for clarity, but optional.
- Plain language or skill-name mention can still route to this skill.

## 默认行为 / Default Behavior

中文：
- 用户上传图片后，默认先直接生成注释图，再补充解释
- 多张图片默认逐张独立生成，不拼成一张
- 每张输入图默认只生成 1 张结果
- 默认使用“基于上传图片编辑”的能力，在原图上只叠加涂鸦层
- 必须保留原图滤镜、色调、构图、物体位置、裁切比例和氛围
- 如果宿主工具只有纯文生图 `GenerateImage`，不能编辑输入图，请先说明限制，不要把重绘图当成原图叠加效果
- 当前正式版会保留一条温柔主线，同时允许细节服务同一张图的主情绪
- V6.3 会先判断图片情绪主线、关系、主体类型、关键物品 list 和低优先级道具
- V6.3 会先形成 overlay 策略，再进入单张图片编辑提示词
- V6.3 会在生成后按 QA 清单检查；只有严重失败时才最多重绘 1 次
- V6.3 会优先判断主体类型，避免低优先级道具抢戏；专业装备图会更认真识别关键物件
- V6.3 可以在主体明确时加入 1-2 个强相关小手绘符号，例如山峰、爪印、热气或路线线条
- V6.3 会在同一张图里尽量做措辞去重，减少重复动词、重复形容词和重复句式
- 生成后的补充信息是：1 句情绪总结 + 3 个后续建议

English:
- When image input is present, the skill should generate the annotated image first, then explain.
- Multiple uploaded images should be processed independently by default, not merged.
- Each input image gets exactly one default result.
- Use image editing based on the uploaded image; only overlay the doodle layer on the original photo.
- Preserve the original filter, color mood, composition, object positions, crop ratio, and atmosphere.
- If the host only provides pure text-to-image `GenerateImage` and cannot edit the uploaded image, explain that limitation instead of presenting a recreated image as an original-photo overlay.
- The current official version keeps one gentle emotional line while adapting subject priority and annotation density.
- V6.3 diagnoses the emotional line, relationship, subject mode, key object list, and low-priority props before building an overlay strategy.
- V6.3 generates one result per input image by default, then runs QA and retries at most once only for serious failures.
- V6.3 avoids letting low-priority props take over, handles professional gear more carefully, may add 1-2 scene-relevant doodle symbols when the subject is clear, and reduces repeated wording inside the same image.
- Post-generation add-ons are: one emotional summary line and three follow-up suggestions.

## 能力说明 / What It Does

中文：
- 理解画面里的可见元素和背后场景
- 提炼整张图统一的情绪线
- 让局部注释围绕同一情绪方向
- 文字方向和图片横竖屏保持一致
- 最后输出一句整体情绪总结

English:
- Understands visible objects and hidden scene context
- Builds one unified emotional line for the image
- Keeps all local notes aligned with the same mood
- Matches text direction to image orientation
- Ends with one emotional summary sentence

## 提示词位置 / Prompt Source

核心提示词已拆成多个 reference 资产：
Core prompt templates are split into reference assets:

- `references/style-dna.md`：视觉 DNA、原图保护、白色手写层、可读性。
- `references/photo-diagnosis.md`：情绪判断、主体类型、物品优先级、物品 list。
- `references/annotation-patterns.md`：注释密度、文案去重、场景偏置、手绘符号。
- `references/prompt-template.md`：单张图片编辑提示词模板。
- `references/qa-checklist.md`：生成后检查和最多一次重绘规则。
- `references/bad-cases.md`：明确禁忌和失败模式。
- `references/issue-report-template.md`：`report to issue` 的节点信息上报模板。
- `references/v6.3-rule-map.md`：V6.3 收敛规则表，用于测试验收和版本对比。
- `references/prompts.md`：兼容旧安装路径的索引文件。

## 示例资产 / Example Assets

`examples/` 和 `assets/examples/` 只用于低频质量校准，不进入默认生成路径。

`examples/` and `assets/examples/` are calibration assets only. They are not part of the default generation path.

示例可以帮助模型理解：

- 什么是关系判断，例如人和宠物互动，而不是“人 + 狗 + 草地”
- 什么是场景状态判断，例如咖啡撒了需要安慰，而不是“杯子 + 键盘 + 污渍”
- 什么是集合主体，例如装备平铺本身就是主角，需要形成“阅兵感”
- 什么是积极情绪传递，例如风筝、公园、天空、风和坐着看的人共同构成向上的感觉

示例不能用于：

- 照抄构图
- 照抄物件
- 照抄注释文案
- 照抄箭头、边框、飞行线、爱心、星星等手绘符号
- 替代当前照片的重新判断

不要把未审核的私人照片、测试集、坏例截图或本地输出放进公开示例目录。只有明确确认可公开的原图 / 成品图，才可以进入 `assets/examples/`。

当前正例说明在 `examples/positive-cases.md`。当前已放入公开资产的正例图在 `assets/examples/`。

## 仓库结构 / Repository Structure

```text
moment-notes/
  .gitattributes
  .gitignore
  SKILL.md
  VERSION
  agents/openai.yaml
  assets/examples/README.md
  assets/examples/positive-03-hiking-gear-roll-call.jpg
  assets/examples/positive-04-park-kites-uplift.jpg
  examples/positive-cases.md
  examples/README.md
  hooks/session-start-update.example.json
  README.md
  SECURITY.md
  references/annotation-patterns.md
  references/bad-cases.md
  references/photo-diagnosis.md
  references/issue-report-template.md
  references/prompt-template.md
  references/prompts.md
  references/qa-checklist.md
  references/style-dna.md
  references/v6.3-rule-map.md
```

## 备注 / Notes

- 如果你希望别人直接安装，仓库建议设为 `public`。
- 如果仓库是 `private`，别人需要访问权限或 token 才能安装。
- Public repo is required for easy open install by other users.
- If the repo is private, users need access permission or token.

## Bad Case 反馈 / Report Bad Cases

如果你遇到效果不好的案例，欢迎提交 GitHub Issue：

`https://github.com/foxbitcoo/moment-notes/issues`

建议提供：

- 原图是什么场景，例如宠物、美食、街景、装备平铺
- 你希望这张图被理解成什么情绪主线
- 实际结果哪里跑偏了
- 是否原图被重绘、裁切、换风格或改变物体位置
- 哪个对象不该被重点标注，或哪个主体应该更优先
- 是否出现文案重复、句式重复、看图说话、注释太满、低优先级道具抢戏、专业名词乱认等问题
- 使用的是哪个版本
- V6.3 节点信息：情绪诊断、关系判断、主体模式、物品优先级、注释策略、prompt 模板、QA 失败项、bad-case IDs、是否重绘
- 可公开的截图或文字描述

如果你在支持 GitHub issue 创建的代理环境中使用这个 skill，也可以直接说：

```text
report to issue: 这里写你的问题和评论
```

skill 会整理本次请求、生成结果摘要、你的评论，以及 V6.3 工作流节点 meta 信息，并在宿主环境支持时尝试提交到本仓库 Issue；如果当前环境不支持直接创建 issue，则会给出可手动提交的 issue 草稿。没有被当前宿主记录到的信息会标注为 `not captured`，不会临时编造。

节点化 issue 草稿会尽量包含：

- Photo Diagnosis：情绪主线、关系、主体模式、物品组、低优先级道具
- Annotation Strategy：注释密度、局部注释意图、结构标记、涂鸦意图
- Prompt Assembly：使用的提示词模板和关键约束
- QA Reflection：失败的 QA 项、bad-case IDs、是否触发最多一次重绘
- Example Calibration：如果参考了正例，只记录判断方式，不复制示例内容
