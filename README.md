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

当前正式提示词为 V6.2：主体优先 + 密度自适应 + 同图去重版。

V6.2 保留第五版的“温柔情绪小记”方向，同时加入主体优先级、注释密度自适应、复杂背景可读性、专业装备识别和主体相关手绘符号，并补充“同图文案去重与改写”规则。它会先判断照片是单一主体、明显主次、集合主体还是专业集合主体，再决定写哪些对象、写多少、是否加场景相关的小手绘符号，并在同一张图里尽量避免重复动作词、重复形容词和重复句式。

Current official prompt: V6.2, subject-priority, adaptive-density, and same-image copy de-duplication.

V6.2 keeps the gentle emotional-note style from Version 5 while adding subject priority, adaptive annotation density, readability protection, professional gear handling, subject-related doodle symbols, and same-image copy de-duplication. It first classifies the image as a single subject, clear hierarchy, collection subject, or professional collection, then decides what to annotate and how dense the notes should be, while reducing repeated wording inside the same image.

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
- 默认使用“基于上传图片编辑”的能力，在原图上只叠加涂鸦层
- 必须保留原图滤镜、色调、构图、物体位置、裁切比例和氛围
- 如果宿主工具只有纯文生图 `GenerateImage`，不能编辑输入图，请先说明限制，不要把重绘图当成原图叠加效果
- 当前正式版会保留一条温柔主线，同时允许细节服务同一张图的主情绪
- V6.2 会优先判断主体类型，避免低优先级道具抢戏；专业装备图会更认真识别关键物件
- V6.2 可以在主体明确时加入 1-2 个强相关小手绘符号，例如山峰、爪印、热气或路线线条
- V6.2 会在同一张图里尽量做措辞去重，减少重复动词、重复形容词和重复句式
- 生成后的补充信息是：1 句情绪总结 + 3 个后续建议

English:
- When image input is present, the skill should generate the annotated image first, then explain.
- Multiple uploaded images should be processed independently by default, not merged.
- Use image editing based on the uploaded image; only overlay the doodle layer on the original photo.
- Preserve the original filter, color mood, composition, object positions, crop ratio, and atmosphere.
- If the host only provides pure text-to-image `GenerateImage` and cannot edit the uploaded image, explain that limitation instead of presenting a recreated image as an original-photo overlay.
- The current official version keeps one gentle emotional line while adapting subject priority and annotation density.
- V6.2 avoids letting low-priority props take over, handles professional gear more carefully, may add 1-2 scene-relevant doodle symbols when the subject is clear, and reduces repeated wording inside the same image.
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

核心提示词在：
Core prompt templates are in:

- `references/prompts.md`

## 仓库结构 / Repository Structure

```text
moment-notes/
  SKILL.md
  VERSION
  agents/openai.yaml
  references/prompts.md
  README.md
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
- 哪个对象不该被重点标注，或哪个主体应该更优先
- 是否出现文案重复、句式重复、看图说话、低优先级道具抢戏等问题
- 使用的是哪个版本
- 可公开的截图或文字描述

如果你在支持 GitHub issue 创建的代理环境中使用这个 skill，也可以直接说：

```text
report to issue: 这里写你的问题和评论
```

skill 会整理本次请求、生成结果摘要和你的评论，并在宿主环境支持时尝试提交到本仓库 Issue；如果当前环境不支持直接创建 issue，则会给出可手动提交的 issue 草稿。
