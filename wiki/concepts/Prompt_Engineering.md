---
title: "Prompt Engineering（提示工程）"
type: concept
tags: [提示工程, LLM, AI, 核心概念]
sources: 
  - raw/01-articles/提示设计策略  _  Gemini API.md
  - raw/01-articles/Prompting best practices-Anthropic.md
  - raw/02-papers/Goolge-Prompt-Engineering-whitepaper.pdf
  - raw/03-transcripts/Prompt Engineering Full Course.md
last_updated: 2026-05-17
---

## 定义

提示工程（Prompt Engineering）是设计和优化输入给大型语言模型（LLM）的文本提示，以引导模型生成准确、有用、符合预期输出的技术学科。它是人机交互与 NLP 的交叉领域，涉及清晰表达意图、提供上下文、设定约束和示例选择。

> "Prompt 工程是迭代过程。不充分的提示可能导致模糊、不准确的响应，阻碍模型提供有意义的输出。" —— Google 白皮书

## 核心要素

根据 Anthropic、OpenAI 和 Google 的共识，有效提示包含七个核心组件：

| 组件                     | 作用      | 示例                     |
| ---------------------- | ------- | ---------------------- |
| **Role/Persona**       | 激活领域知识  | "你是财富 500 强公司的高级数据科学家" |
| **Task Context**       | 背景和受众信息 | "结果将呈现给董事会"            |
| **Clear Instructions** | 核心请求    | "用 3 个要点总结"            |
| **Sequential Steps**   | 确保执行顺序  | 编号步骤列表                 |
| **Few-shot Examples**  | 演示期望格式  | 3-5 个相关多样化示例           |
| **Output Format**      | 响应结构    | "返回 JSON，字段包括..."      |
| **Constraints**        | 限制输出空间  | "200字以内，不使用术语"         |

## 主要技术

### 基础技术
- **Zero-Shot**：无示例直接提问，适用于简单任务
- **Few-Shot**（[[Few_Shot_Prompting]]）：提供 3-5 个示例引导模型学习模式
- **Role Prompting**：分配角色以激活特定知识域
- **Contextual Prompting**：提供任务特定背景信息

### 控制与约束
- **[[Steering_vs_Commanding]]**：引导而非命令，明确角色 + 受众 + 语气 + 格式
- **[[Constraints_and_Negatives]]**：负向指令与约束（"不要做 Y" 有时比 "做 X" 更有效）
- **[[Structured_Output]]**：要求 JSON / 表格 / XML 等结构化输出
- **[[Temperature]]**：调整模型采样的确定性 vs 创造性

### 上下文与提示架构
- **[[System_Prompt]]**：系统提示 vs 用户提示的区分
- **[[Context_Engineering]]**：从单个提示到系统上下文管理的范式转变
- **[[Interview_Style_Prompting]]**：让模型反向采访你以补全上下文

### 工作流与迭代
- **[[Iterative_Refinement]]**：把提示当对话，逐步精化输出
- **[[Prompt_Chaining]]**：把复杂任务拆为多步，前一步输出作为下一步输入
- **[[Self_Evaluation]]**：让模型评估自身输出，迭代改进

### 高级推理技术
- **Chain-of-Thought (CoT)**（[[Chain_of_Thought]]）：要求模型展示推理步骤，显著提升数学和逻辑任务表现
  - 注意：现代推理模型（GPT-5、Claude 4、Gemini 3）内部自动思考，显式 CoT 可能反而有害
- **Self-consistency**：多次采样取最一致的答案
- **Tree of Thoughts (ToT)**：同时探索多条推理路径
- **ReAct**：结合推理（Reasoning）与行动（Acting）的代理范式
- **Step-back Prompting**：先问一般性问题再解决具体任务

## 范式演变

### Prompt Engineering → Context Engineering

2024-2025 年领域的重要转变：

- **过去**：专注于单个提示的词句优化
- **现在**：理解为"上下文工程"——策划系统提示、工具、外部数据和消息历史的最优 token 集合

> "最佳提示不是最复杂的，而是用最少的必要上下文达成目标的。" —— Anthropic

## 最佳实践

1. **具体明确**：每个词都应帮助 AI 准确理解需求
2. **简洁优先**：研究表明 **150-300 词**是最佳长度，超过 3,000 tokens 性能显著下降
3. **使用分隔符**：XML 标签（`<context>`, `<task>`）或 Markdown 标题
4. **示例质量胜过数量**：3-5 个高质量、多样化示例优于大量雷同示例
5. **指令优于约束**：说"做 X"比"不要做 Y"更有效
6. **迭代优化**：基于输出反馈持续改进

## 模型特定注意事项

| 模型 | 特点 | 建议 |
|------|------|------|
| **Claude 4.x** | 字面理解指令 | 明确表达期望行为，使用 XML 标签 |
| **GPT-4.1/5** | 对冲突指令敏感 | 避免矛盾指令，注意推理模型不要 CoT |
| **Gemini 3** | 内置思考机制 | 简化提示，`thinking_level: "high"` |

## 关联连接

### 框架与方法
- [[5C_Framework]] — 5C 提示契约框架
- [[Context_Engineering]] — 上下文工程

### 基础提示技术
- [[Zero_Shot_Prompting]] — 零样本提示
- [[Few_Shot_Prompting]] — 少样本提示
- [[Chain_of_Thought]] — 思维链详解

### 控制与设计
- [[Steering_vs_Commanding]] — 引导 vs 命令
- [[Constraints_and_Negatives]] — 约束与负向指令
- [[Structured_Output]] — 结构化输出
- [[System_Prompt]] — 系统提示 vs 用户提示
- [[Temperature]] — 温度参数

### 工作流
- [[Iterative_Refinement]] — 迭代精化
- [[Interview_Style_Prompting]] — 访谈式提示
- [[Prompt_Chaining]] — 提示链
- [[Self_Evaluation]] — 自评估

### 来源
- [[摘要-gemini-api-prompting-strategies]] — Gemini 策略来源
- [[摘要-anthropic-prompting-best-practices]] — Claude 最佳实践来源
- [[摘要-google-prompt-engineering-whitepaper]] — Google 白皮书来源
- [[摘要-tech-with-tim-prompt-engineering-course]] — Tech With Tim 课程
