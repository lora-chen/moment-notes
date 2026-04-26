# Moment Notes（此刻小记）

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
- 默认保留原图滤镜、色调和氛围，只叠加涂鸦层
- 生成后的补充信息是：1 句情绪总结 + 3 个后续建议

English:
- When image input is present, the skill should generate the annotated image first, then explain.
- Multiple uploaded images should be processed independently by default, not merged.
- Preserve the original filter, color mood, and atmosphere; only overlay the doodle layer.
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
  agents/openai.yaml
  references/prompts.md
  README.md
```

## 备注 / Notes

- 如果你希望别人直接安装，仓库建议设为 `public`。
- 如果仓库是 `private`，别人需要访问权限或 token 才能安装。
- Public repo is required for easy open install by other users.
- If the repo is private, users need access permission or token.
