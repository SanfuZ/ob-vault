---
title: "Excalidraw"
type: entity
tags: [工具, 绘图, Obsidian, 插件, 头脑风暴]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
last_invalidated: 2026-05-17
last_updated: 2026-05-17
---

## 定义

**Excalidraw** 是一款流行的开源手绘风格白板/绘图工具，以其**自然手绘感**著称。在 [[Obsidian]] 生态中，Excalidraw 插件是**下载量排名第一的社区插件**，被广泛用于知识梳理和头脑风暴。

## 核心特性

- **手绘风格**：图形看起来像在白板上随手画的
- **轻量级**：基于 SVG，文件小、加载快
- **协作友好**：支持实时多人协作（独立版）
- **Obsidian 集成**：作为插件可在 Obsidian 中直接创建/编辑

## 在 Obsidian 中的使用

### 作为插件

- 安装 Excalidraw 插件
- 创建 .excalidraw 文件
- 可嵌入到 Markdown 笔记中

### 作为 [[Agent_Skill|Agent Skill]]

[[Axton]] 开发了 Excalidraw Skill，让智能体能够：
- 生成 Excalidraw 图表
- 所有节点大小自动适配
- 结构清晰完整
- 即使使用免费大模型，输出质量也很高

## 适用场景

| 场景 | 适配度 |
|------|--------|
| 知识梳理 / 头脑风暴 | ⭐⭐⭐⭐⭐ |
| 流程图 / 架构图 | ⭐⭐⭐⭐ |
| 思维导图 | ⭐⭐⭐ |
| 精确技术图（如 UML） | ⭐⭐ |

## 与其他绘图方案对比

| 工具 | 风格 | 优势 |
|------|------|------|
| [[Excalidraw]] | 手绘 | 头脑风暴、视觉亲和 |
| Canvas（JSON Canvas） | 卡片+连线 | 知识架构、原生 Obsidian |
| [[Mermaid]] | 文本驱动 | 流程图、易版本控制 |

## 关联连接

- [[Axton]] — Excalidraw Skill 的作者
- [[Obsidian]] — 插件下载量第一的母平台
- [[Mermaid]] — 替代方案之一
- [[Agent_Skill]] — Skill 标准
- [[摘要-obsidian-9-essential-agent-skills]] — 来源
