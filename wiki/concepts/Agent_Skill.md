---
title: "Agent Skill"
type: concept
tags: [概念, AI智能体, 扩展机制, 标准]
sources: [raw/03-transcripts/2026-05-15-Obsidian CLI 详细教程：官方命令行工具，激进拥抱智能体，高效 + 自动化 + 降低Token消耗。.md]
last_updated: 2026-05-16
---

## 定义

Agent Skill 是 2026 年初提出的智能体扩展标准。它将一组**操作能力 + 上下文知识 + 提示词**打包为可分发、可加载的"技能模块",让 AI 智能体可以按需获得操作特定工具或领域的能力,而无需重新训练模型或硬编码工具调用。

## 核心思想

| 维度 | 传统方式 | Agent Skill |
|------|----------|-------------|
| 工具集成 | 在智能体代码中硬编码 | 作为可加载的 Skill 包 |
| 上下文知识 | 训练时灌入或长提示 | 与 Skill 一起按需加载 |
| 分发方式 | 不可分发 | 通过 GitHub 等仓库分享 |
| 跨智能体复用 | 需重新实现 | 同一 Skill 可被多智能体使用 |

## Skill 通常包含

1. **能力定义**:可以执行哪些操作(如调用 [[Obsidian_CLI]] 命令)
2. **上下文文档**:相关工具的官方文档摘要,补足模型知识盲区
3. **提示词模板**:指导智能体如何在特定场景下决策
4. **示例与说明**:典型用法示范

## 典型应用:Obsidian Skills

[[Kepano]] 在 2026 年初 Agent Skill 标准发布后,立即在 GitHub 发布了 `kepano/obsidian-skills` 仓库,目前已包含 5 个官方 Skills:

1. **Obsidian CLI Skill**:让智能体学会使用 [[Obsidian_CLI]] 操作笔记库
2. **网页内容提取 Skill**:从网页提取内容并转换为干净的 Markdown,适合资料剪藏
3. (以及之前发布的 3 个 Skills)

### 安装流程
1. 从 GitHub 下载所有 Skills
2. 安装到智能体工具(如 [[Claude_Code]]、[[Gemini_CLI]])
3. 智能体自动获得对应能力,通过自然语言驱动

## 战略意义

### 对 Obsidian
- 不必自建官方 AI,而是通过 Skills 接入所有第三方智能体
- 维护 [[Local_First]] 原则:用户自选 AI,数据始终在本地
- 标志 Obsidian "全面拥抱智能体时代"

### 对 AI Agent 生态
- 标准化了智能体的工具扩展方式
- 形成开源协作的 Skill 生态
- 降低了"让 AI 操作某个软件"的开发成本

## 关联连接
- [[Obsidian]] — Skills 的重要发布方
- [[Obsidian_CLI]] — Skill 操作的目标
- [[Kepano]] — Obsidian Skills 作者
- [[Claude_Code]] — Skill 宿主智能体之一
- [[Gemini_CLI]] — Skill 宿主智能体之一
- [[Local_First]] — Skills 体系背后的理念
- [[摘要-obsidian-cli-tutorial]] — 来源教程
