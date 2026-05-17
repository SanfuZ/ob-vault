---
title: "Steering vs Commanding（引导 vs 命令）"
type: concept
tags: [提示工程, 提示设计, 核心理念]
sources:
  - raw/03-transcripts/Prompt Engineering Full Course.md
last_updated: 2026-05-17
---

## 定义

**Steering vs Commanding（引导 vs 命令）** 是 [[Tech_With_Tim]] 提出的提示设计核心理念。它区分了两种不同的提示风格：

- **Commanding（命令）**：告诉模型"做什么"——模型自行选择长度、风格、焦点
- **Steering（引导）**：给模型明确方向——指定角色、受众、语气、格式、长度、约束

> 大多数人写提示都是在"命令"，而不是"引导"。所以同一个 LLM 给出的结果天差地别。

## 对比示例

### 命令式（Commanding）

```
总结这个内容。
```

模型自由选择：长度、风格、是否分点、聚焦哪里。

### 引导式（Steering）

```
你是一位高管秘书。把会议记录总结成 4 条要点。
聚焦于决策与行动项，不要废话。
```

模型被引导得：长度（4 条）、视角（高管秘书）、焦点（决策/行动）、风格（不废话）。

## 引导的四要素

[[Tech_With_Tim]] 建议任何提示都应包含这四个维度：

| 维度 | 作用 | 示例 |
|------|------|------|
| **Role（角色）** | 激活领域知识 | "你是一位 B2B 资深文案" |
| **Audience（受众）** | 校准内容深度 | "面向中型公司的运营经理" |
| **Tone（语气）** | 控制风格 | "自信但不要推销感" |
| **Format（格式）** | 约束输出形态 | "两句话的 LinkedIn 广告，以 CTA 结尾" |

## 与其他概念的关系

- 与 [[Constraints_and_Negatives|约束与负向指令]] 互补：引导更多关注"做什么"，约束更多关注"不要做什么"
- 是 [[Prompt_Engineering|提示工程]] 的核心心智模式
- 对 [[Claude]] 这种"按字面理解指令"的模型尤其重要

## 关键洞察

> 同样的 LLM，引导和命令给出的结果差距巨大。差异不在模型，而在你如何指挥它。

## 关联连接

- [[Prompt_Engineering]] — 提示工程总览
- [[Constraints_and_Negatives]] — 约束与负向指令
- [[Iterative_Refinement]] — 迭代精化
- [[Interview_Style_Prompting]] — 当你自己也不知道要什么时
- [[摘要-tech-with-tim-prompt-engineering-course]] — 来源
