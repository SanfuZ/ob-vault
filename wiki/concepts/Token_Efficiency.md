---
title: "Token Efficiency（Token 效率）"
type: concept
tags: [概念, Token优化, 成本, LLM, AI智能体]
sources: [raw/03-transcripts/2026-05-15-Obsidian CLI 详细教程：官方命令行工具，激进拥抱智能体，高效 + 自动化 + 降低Token消耗。.md, raw/02-papers/5C Prompt Contracts .pdf]
last_updated: 2026-05-16
---

## 定义

Token Efficiency(Token 效率)是指在与大语言模型(LLM)交互时,**用尽可能少的 Token 达成目标**的能力或策略。它直接关系到 API 成本、响应延迟和上下文窗口占用,是构建可持续 AI 应用的核心约束。

## 为什么 Token 效率重要

| 维度 | 影响 |
|------|------|
| **API 成本** | 多数 LLM 按 Token 计费,输入/输出都计算 |
| **响应延迟** | Token 越多,处理时间越长 |
| **上下文窗口** | 有限的窗口必须给关键信息预留空间 |
| **可持续性** | 长时间运行的智能体需要严格控制成本 |
| **缓存命中率** | 紧凑的提示更容易命中缓存 |

## 两种典型场景

### 场景一:提示工程层面 —— [[5C_Framework]]

5C Prompt Contracts 框架的核心卖点之一就是 Token 效率:
- 平均仅需 **54 Tokens** 输入即可表达完整契约
- 比传统 DSL 节省 **6 倍以上**
- 复杂 DSL 的"Token 和认知开销"会限制 LLM 的"熵预算"
- 简化结构让 LLM 专注于语义理解和创意生成

> 详见 [[摘要-5c-prompt-contracts-paper]]

### 场景二:工具集成层面 —— [[Obsidian_CLI]]

让 AI 智能体操作软件时,Token 效率的差异更加悬殊:

| 操作方式 | Token 消耗(估算) |
|----------|------------------|
| AI 扫描整个 Obsidian 笔记库 | **数百万 Token** |
| 通过 Obsidian CLI 查询孤岛笔记 | **约 100 Token** |
| 通过 Obsidian CLI 修改 YAML 元数据 | **几十 Token**(无需读取全文) |

底层机制是 [[IPC]]:AI 只需发送一条命令,由 Obsidian 进程本地完成操作并返回结果。

## 提升 Token 效率的策略

### 1. 减少冗余输入
- 提示压缩、删除无意义的客套话
- 使用结构化模板(如 5C)取代散文式描述

### 2. 工具化代替全文读取
- 通过 CLI、API 让外部程序完成结构性查询
- AI 只接收"压缩后的结果",不读原始文件
- 典型案例:[[Obsidian_CLI]] 通过 [[IPC]] 操作笔记

### 3. 用工作流取代智能体
> **越是确定性的任务,越要用工作流和代码,而不是智能体**。否则你的 Token 消耗得飞快。 —— 视频作者建议

- 规则明确的任务用 [[n8n]]、Python 脚本
- 仅在需要"判断和决策"时调用 LLM

### 4. 选择高免费额度的工具
- [[Gemini_CLI]] 提供大量免费 Token 额度
- 与付费工具(如 [[Claude_Code]])灵活搭配

### 5. 缓存与复用
- 系统提示、工具定义保持稳定以利缓存
- 利用 prompt caching(参见 [[Context_Engineering]])

## 关联连接
- [[5C_Framework]] — 提示工程层的 Token 效率框架
- [[摘要-5c-prompt-contracts-paper]] — 5C 论文,论证 Token 效率
- [[Obsidian_CLI]] — 工具集成层的 Token 效率典范
- [[IPC]] — 实现工具集成层 Token 效率的底层机制
- [[n8n]] — 用工作流替代智能体以节约 Token
- [[Gemini_CLI]] — 免费额度优先的智能体工具
- [[Claude_Code]] — 需重点考量 Token 成本的智能体工具
- [[Context_Engineering]] — 整体上下文优化范式
- [[摘要-obsidian-cli-tutorial]] — 来源教程
