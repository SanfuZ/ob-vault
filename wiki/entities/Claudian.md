---
title: "Claudian"
type: entity
tags: [工具, Obsidian, 插件, AI智能体, Claude]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
last_updated: 2026-05-17
---

## 定义

**Claudian** 是一个 [[Obsidian]] 插件，将 [[Claude_Code]]（Anthropic 的智能体编程工具）集成到 Obsidian 中，用户可以在 Obsidian 笔记界面直接与 Claude Code 交互，完成笔记智能操作。

## 核心功能

- 在 Obsidian 内部直接调用 Claude Code
- 支持当前笔记上下文（current_note）
- 支持编辑器选中文本上下文（editor_selection）
- 支持浏览器视图选择上下文（browser_selection）
- 完全本地化、保持 [[Local_First|Local-First]] 原则

## 安装方法

### 方法一：通过 BRAT（推荐）

[[BRAT]] 是 Obsidian Beta 插件管理工具：

1. 在第三方插件市场安装 BRAT 插件
2. 进入 BRAT 设置，点击 **Add Beta plugin**
3. 输入 Claudian 仓库地址
4. 完成安装

### 方法二：手动安装

下载 Claudian 的 3 个核心文件，放入 Obsidian 的 plugins 文件夹。

## 配置

### 基础设置

- **称呼**：设置 AI 称呼用户的方式（如 "Jason"）

### 环境变量（地区受限用户）

如果所在地区被 Anthropic 限制，需要在环境变量中填入转接兼容模型的配置：
- API 端点地址
- 模型名称
- 认证信息

## 与 [[Obsidian_Agent_Client]] 的对比

| 维度 | Claudian | [[Obsidian_Agent_Client]] |
|------|----------|----------------------------|
| 支持的智能体 | 仅 [[Claude_Code]] | 多个（[[Claude_Code]]、Codex、[[Gemini_CLI]]、[[OpenCode]]、千问 Code 等） |
| 配置复杂度 | 低 | 中（需配置每个 agent） |
| 适合人群 | Claude 用户 | 多智能体使用者 |

## 前置要求

- 安装好 [[Claude_Code]]
- Obsidian 版本支持

## 关联连接

- [[Claude_Code]] — 集成的智能体
- [[Obsidian_Agent_Client]] — 替代方案（多智能体）
- [[Obsidian]] — 母平台
- [[BRAT]] — 推荐的安装方法
- [[Claude]] — 底层 LLM
- [[Local_First]] — 设计原则
- [[摘要-obsidian-9-essential-agent-skills]] — 来源
