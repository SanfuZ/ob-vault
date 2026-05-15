---
title: "n8n"
type: entity
tags: [工具, 工作流, 自动化, 开源, 集成]
sources: [raw/03-transcripts/2026-05-15-Obsidian CLI 详细教程：官方命令行工具，激进拥抱智能体，高效 + 自动化 + 降低Token消耗。.md]
last_updated: 2026-05-16
---

## 定义

n8n 是一款开源的工作流自动化平台,提供可视化的节点式工作流编辑器,支持本地部署。它可以连接数百种应用与 API,适合搭建数据流转、信息聚合、任务编排等自动化场景。

## 核心特性

- **可视化工作流编辑器**:通过拖拽节点构建流程
- **本地部署**:数据自主可控,符合 [[Local_First]] 理念
- **丰富的节点生态**:支持大量第三方应用集成
- **代码扩展能力**:可在节点中执行 JavaScript、Python 等脚本

## 与 [[Obsidian]] 的集成

### 通过 [[Obsidian_CLI]] 操作笔记库
在 n8n 工作流面板添加一个 **`execute command`** 节点,执行 Python 脚本调用 Obsidian CLI 即可让工作流操作 Obsidian 笔记。

### 典型场景
- 定时抓取信息(如 RSS、arXiv 论文)并归档到 Obsidian
- 监听邮件、消息触发笔记创建
- 跨工具的数据同步(Notion ↔ Obsidian)

## 视频中的建议

视频作者特别强调:
> **越是确定性的任务,越要用工作流和代码,而不是智能体**。否则你的 Token 消耗得飞快。

这意味着对于规则明确、流程固定的笔记自动化,n8n 工作流比 AI 智能体更经济(参见 [[Token_Efficiency]])。

## 关联连接
- [[Obsidian_CLI]] — 集成入口
- [[Obsidian]] — 集成目标
- [[Token_Efficiency]] — 选择工作流而非智能体的核心理由
- [[Local_First]] — 共同的部署理念
- [[摘要-obsidian-cli-tutorial]] — 来源教程
