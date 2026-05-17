---
title: "摘要-obsidian-9-essential-agent-skills"
type: source
tags: [来源, Obsidian, AI智能体, Skills, 实战教程]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
last_updated: 2026-05-17
---

## 核心摘要

B 站「杰森的效率工坊」发布的 Obsidian AI Agent 必备 Skills 详解视频。视频核心观点：**在智能体时代，Skill 市场鱼龙混杂，盲目选 Skill 不仅完不成任务，还会白白烧掉大量 [[Token_Efficiency|Token]]。**

视频系统梳理了 9 个 Skill，涵盖三大类：

1. **[[Kepano]] 的官方 Skills（5 个）**：[[Defuddle]]（网页剪藏）、[[Obsidian_CLI]]、[[Obsidian_Bases]]、Obsidian Markdown、JSON Canvas
2. **[[Axton]] 的画图 Skills（3 个）**：JSON Canvas、[[Excalidraw]]、[[Mermaid]]
3. **学习类 Skills（2 个）**：[[Tutor_Skill]]、[[Scholar_Skill]]

视频核心结论：

- **OpenClaw 官方仓库的 obsidian skill 已过时**：底层依赖的不是官方 [[Obsidian_CLI]]，而是 2023 年的 notesmd-cli 项目，本质是文件系统 I/O，消耗大量 token
- **kepano 的 JSON Canvas skill 推荐被 Axton 的版本替代**：节点坐标与布局优化更好
- **Tutor Skill 是绝大多数学习场景的最佳选择**：可一键把 PDF/GitHub 项目转为完整 Obsidian 知识库（含双链 + [[MOC|MOC 内容地图]]）
- **Scholar Skill 是学术科研专用**：长生命周期任务编排，深度依赖 OpenClaw，消耗大量 token
- **Obsidian Markdown Skill 建议自行扩展**：用户应把自己的格式偏好（如不要一级标题、不要嵌套列表）写入其中

视频末尾还介绍了两个主流 Obsidian 智能体插件：[[Claudian]] 和 [[Obsidian_Agent_Client]]。

## 关联连接

- [[Defuddle]] — 网页剪藏 CLI 工具（核心必备）
- [[Obsidian_CLI]] — Obsidian 官方命令行工具
- [[Obsidian_Bases]] — Bases 数据库
- [[Axton]] — 画图 Skills 作者
- [[Excalidraw]] — 手绘风绘图工具
- [[Mermaid]] — 文本绘图语法
- [[Tutor_Skill]] — 学习用 Skill（重点推荐）
- [[Scholar_Skill]] — 学术科研 Skill
- [[Claudian]] — Obsidian 集成 Claude Code 的插件
- [[Obsidian_Agent_Client]] — 多智能体客户端
- [[MOC]] — Map of Content
- [[Kepano]] — Skills 作者
- [[Agent_Skill]] — Skill 标准概念
- [[Obsidian]] — 母平台
