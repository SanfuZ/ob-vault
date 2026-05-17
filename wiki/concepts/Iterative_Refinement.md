---
title: "Iterative Refinement（迭代精化）"
type: concept
tags: [提示工程, 工作流, 优化策略]
sources:
  - raw/03-transcripts/Prompt Engineering Full Course.md
last_updated: 2026-05-17
---

## 定义

**Iterative Refinement（迭代精化）** 是一种提示工程工作流方法：**把提示当作对话而不是一次性投递**。当第一次响应不完美时，不要重新开始，而是基于现有结果不断微调指令，逐步逼近期望输出。

## 核心理念

> 把提示视为对话（conversation），而不是单次提交（one-shot attempt）。

## 典型流程

```
初始提示  → 模型响应
   ↓
"再短一点"  → 模型响应
   ↓
"再正式些"  → 模型响应
   ↓
"加一个例子"  → 模型响应
   ↓
"只聚焦在 X 上"  → 满意，结束
```

## 实例

```
你：写一段两句话的 LinkedIn 广告，关于我们的新产品。

模型：[输出 4 句话，过于推销]

你：缩到 2 句。更事实化，少些推销感。

模型：[输出 2 句，但少了 CTA]

你：保留两句结构，结尾加一个 CTA。

模型：[完美]
```

## 为什么有效

1. **首次提示往往不准**：很少有人能一次性写出完美提示
2. **基于反馈调整成本低**：比重新构思整个提示更快
3. **保持上下文连贯**：模型记得前几轮的细节，调整时更精准
4. **模拟与人合作**：本质上像与同事来回讨论一份文档

## 何时不要迭代

- 上下文已被污染（错误的早期回复影响了后续输出） → 开新对话
- 任务方向完全错误 → 重写而非微调
- [[Token_Efficiency|Token 成本]] 累积过高 → 评估是否值得继续

## 与其他技术的对比

| 方法 | 适用场景 |
|------|----------|
| [[Iterative_Refinement|迭代精化]] | 第一次输出已经接近，需要微调 |
| [[Prompt_Chaining|提示链]] | 任务复杂、需要分步骤完成 |
| [[Interview_Style_Prompting|访谈式提示]] | 自己不确定需要提供哪些上下文 |

## 关联连接

- [[Prompt_Engineering]] — 提示工程总览
- [[Prompt_Chaining]] — 另一种分步策略
- [[Interview_Style_Prompting]] — 反向：让模型问你
- [[Self_Evaluation]] — 让模型自评估也是迭代的一种
- [[摘要-tech-with-tim-prompt-engineering-course]] — 来源
