---
title: "Obsidian"
type: entity
tags: [工具, 笔记软件, 知识管理, Markdown, 本地优先]
sources: [raw/03-transcripts/2026-05-15-Obsidian CLI 详细教程：官方命令行工具，激进拥抱智能体，高效 + 自动化 + 降低Token消耗。.md]
last_updated: 2026-05-16
---

## 定义

Obsidian 是一款基于本地 Markdown 文件的桌面笔记软件,主打"第二大脑"(second brain)的知识管理理念。它通过**双向链接(Wiki-link)**、**标签**和**图谱视图**将碎片化笔记编织为相互关联的知识网络,并支持丰富的插件生态。

## 核心特性

### 1. 本地优先(Local-First)
- 所有数据以 Markdown 文件形式存储在本地文件系统
- 用户完全掌握自己的笔记数据
- 注重隐私,不强制云同步
- 遵循 [[Local_First]] 原则

### 2. 双向链接(Wiki-link)
- 使用 `[[页面名称]]` 语法创建内部链接
- 自动维护反向引用(backlinks)
- 支持嵌入(embed):`![[文件名]]`

### 3. 插件生态
- **核心插件**:日记、模板、图谱视图、Canvas 等
- **社区插件**:数千个开源插件扩展功能
- **主题与皮肤**:如 [[Kepano]] 创作的 Minimal 主题

### 4. 命令行工具([[Obsidian_CLI]])
- 1.12 版本起官方推出 CLI
- 主要面向 AI 智能体而非人类用户
- 通过 [[IPC]] 与 Obsidian 进程通信

## 战略定位

### 不做官方 AI
CEO [[Kepano]] 在采访中明确表示:不会像 [[Notion]] 那样推出官方 AI 工具。
- 数据全部掌握在用户手里
- 由用户决定如何使用 AI
- 提供 [[Agent_Skill]] 让用户接入任意智能体

### 拥抱智能体时代
- 2026 年初 Agent Skill 标准发布后,Kepano 立即发布 3 个 Obsidian Skills
- 推出 Obsidian CLI 为智能体提供深度操作能力
- 目前官方已发布 5 个 Skills,涵盖 CLI 操作、网页内容提取等

## 关联连接
- [[Obsidian_CLI]] — 官方命令行工具
- [[Kepano]] — 现任 CEO
- [[Agent_Skill]] — 智能体扩展标准
- [[Local_First]] — 核心理念
- [[摘要-obsidian-cli-tutorial]] — 来源教程
