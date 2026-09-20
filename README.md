# Photo Minimal Flat Editorial（照片极简扁平插画 · 改造版）

> 本仓库是基于 [ZzzLc0405/photo-abstract-editorial](https://github.com/ZzzLc0405/photo-abstract-editorial) 的**二次开发 / 深度改造版本**，原项目作者：ZzzLc0405（@AM.）。原项目仅限个人学习、研究、非商业用途，本仓库同样遵守该约定。

## 与原版的区别（本次改造点）

- **新增双模式**：模式 A（原照片忠实保留在上方 + 下方同一场景的极简扁平插画 + 米白面板 + 2–5 词英文诗意标题）；模式 B（全幅插画版，天空与原片同样鲜艳，不带照片区域）
- **新增 14 条可通用设计原理**：忠实原图、主体＋衬托客体、借白描之法、3–5 纯平涂色、构图工整、地面锚定、场景适配与纵深、自然过渡、氛围与光线、天空与云、距离感、空间忠实、物理合理、天空一致性
- **提示词全面重写**（中 / 英文两版），提炼为可供豆包、Codex、Claude 等不同模型直接使用的工作流
- 极简的原则是"减少视觉疲劳、不删意义"：突出主体，但保留有衬托作用的客体（地面、光线、天空、代表性环境物）

## 目录结构

```text
photo-minimal-flat-editorial/
├── SKILL.md                         # Skill 入口：工作流 + 通用原理 + guardrails
├── agents/openai.yaml               # Codex 界面元数据（沿用原项目）
├── references/
│   ├── photo-abstract-editorial-prompt.zh-CN.md   # 中文提示词（改造版）
│   └── photo-abstract-editorial-prompt.en.md      # English prompt (revised)
└── assets/examples/                 # 示例图片（来自原仓库，原作者拍摄）
```

## 使用方法

1. 将整个文件夹复制到你的 Skill 目录：Codex `~/.codex/skills/`、Claude Code `~/.claude/skills/`、豆包 `.user_skills/` 等
2. 开启新对话，上传一张希望处理的照片
3. 提出需求，例如："使用 photo-abstract-editorial 将这张照片制作成摄影＋极简扁平插画的竖向编辑作品"
4. 也可直接将 `references/` 下的提示词粘贴给任意文生图 / 图像编辑模型使用

## 许可说明

本仓库内容继承原项目的非商业使用许可（见 `LICENSE.md`）：仅限个人学习、研究、非商业用途；商业使用（含基于本 Skill 修改后的商业分发）须事先获得原作者授权。示例图片版权归原作者 ZzzLc0405 所有。

如果本仓库对你有帮助，欢迎 Star ⭐；若在原项目基础上继续修改，请保留上述署名与许可声明。
