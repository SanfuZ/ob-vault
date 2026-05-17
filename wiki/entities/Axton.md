---
title: "Axton"
type: entity
tags: [人物, 博主, AI, Obsidian, Skill作者]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
last_updated: 2026-05-17
---

## 定义

**Axton** 是著名的 AI 博主，自媒体 ID 为「回到 Axton」。他在 AI Agent 与 Obsidian 集成领域贡献了多个高质量的 [[Agent_Skill|Agent Skills]]，尤其在画图类 Skill 上有口皆碑。

## 主要贡献

Axton 开发了 **3 个画图类 Skills**，覆盖了 Obsidian 中几乎所有图表制作场景：

### 1. JSON Canvas Skill（推荐替代 [[Kepano]] 版本）

- 针对 Canvas 节点的坐标与布局做了优化
- 解决了 Kepano 版本"节点大小计算不准确、文字溢出"的问题
- 同时支持**思维导图模式**和**自由图表模式**
- 在自由模式下可通过 Canvas 分组实现结构化展示

### 2. Mermaid Skill

- 生成的 [[Mermaid]] 代码结构清晰、样式美观
- 几乎不需要手动调试
- 成功率高

### 3. Excalidraw Skill

- 生成的 [[Excalidraw]] 图表手绘风美观
- 适合知识梳理与头脑风暴

## Skill 设计特点

- **坐标与布局优化**：使用免费大模型也能输出整洁图表
- **多模式支持**：思维导图 vs 自由图表
- **场景覆盖完整**：3 个 Skill 覆盖 Obsidian 中所有图表需求

## 关键洞察

[[Kepano]] 发布的官方 JSON Canvas Skill 在布局上存在瑕疵（节点大小、文字溢出），Axton 通过引入对坐标的精确控制，在同样模型下产出明显更优。**这成为 9 个 Skills 中 Kepano JSON Canvas 唯一不推荐的原因**。

## 关联连接

- [[Kepano]] — Obsidian CEO，其 JSON Canvas Skill 被 Axton 版本取代
- [[Obsidian]] — Skills 服务的目标平台
- [[Excalidraw]] — 手绘风绘图工具
- [[Mermaid]] — 文本绘图语法
- [[Agent_Skill]] — Skill 标准
- [[摘要-obsidian-9-essential-agent-skills]] — 来源
