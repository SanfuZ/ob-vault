---
title: "OpenCode"
type: entity
tags: [工具, AI智能体, CLI, 编程, 多模型]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
  - raw/03-transcripts/2026-05-17-AI一键搭建Obsidian知识库架构和学习路径，从0开始学习并精通任何一个知识领域。.md
last_updated: 2026-05-17
---

## 定义

**OpenCode** 是一款开源的 AI 智能体编程工具，特点是**接入多种免费 AI 模型**，让用户可以在编程任务中灵活切换不同的大模型。OpenCode 常被作为 [[Claude_Code]]、[[Gemini_CLI]] 等收费工具的替代品。

## 核心特性

### 1. 免费 AI 额度

接入多种免费可用的模型：
- 小米的大模型
- 阿里千问最新模型
- 其他开源模型

### 2. 多智能体接入

OpenCode 也是 [[Obsidian_Agent_Client]] 等多智能体客户端的支持目标之一。

### 3. 适合长任务

如配合 [[Tutor_Skill]] 构建完整 [[Obsidian]] 知识库时，OpenCode 的免费额度让长时间任务的成本可控。

## 典型使用场景

### 场景 1：通过 Tutor Skill 学习

```bash
# 创建项目目录
mkdir my_project && cd my_project
mkdir resources StudyVault
# 把 PDF 放入 resources/
# 在 OpenCode 中打开当前目录
# 输入 /tutor-setup
```

OpenCode 调用免费模型完成知识库构建，避免使用昂贵的付费模型。

### 场景 2：作为 [[Obsidian_Agent_Client]] 中的 Agent

在 Obsidian Agent Client 中配置 OpenCode：
- Agent ID: `OpenCode`
- Path: OpenCode 可执行路径
- Arguments: 含 Obsidian Vault 路径

## 与同类工具对比

| 工具 | 主要模型 | 成本 |
|------|----------|------|
| OpenCode | 免费多模型 | 0 |
| [[Claude_Code]] | Claude 系列 | 较高 |
| [[Gemini_CLI]] | Gemini 系列 | 免费额度优先 |

## 关联连接

- [[Claude_Code]] — 同类（付费旗舰） 
- [[Gemini_CLI]] — 同类（免费优先）
- [[Tutor_Skill]] — 常配合使用
- [[Obsidian_Agent_Client]] — 支持 OpenCode 作为 Agent
- [[Agent_Skill]] — Skill 标准
- [[摘要-obsidian-9-essential-agent-skills]] — 来源
- [[摘要-ai-obsidian-knowledge-base-workflow]] — 来源
