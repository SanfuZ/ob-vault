---
title: "Self Evaluation（自评估）"
type: concept
tags: [提示工程, 质量控制, 高级技巧]
sources:
  - raw/03-transcripts/Prompt Engineering Full Course.md
last_updated: 2026-05-17
---

## 定义

**Self Evaluation（自评估）** 是一种提示工程技巧：让模型对自己（或其他模型）的输出进行**评分、批判或改进建议**，从而提升整体输出质量。

## 核心理念

> 模型经常能识别自己输出的问题，前提是用恰当的方式提问。

## 典型提示模板

```
这是我写的一段摘要：
{摘要内容}

请按以下维度打分（1-5 分）：
- 清晰度
- 完整性

并给出一句话的改进建议——只提最重要的一点。
```

## 关键技巧：欺骗模型

> 不要让模型评估它自己刚写的内容！它会有"自我合理化"偏见。

正确做法：

1. **新开一个会话（新的 chat）**：避免模型记得"这是我写的"
2. **伪装来源**：把"AI 写的"伪装成"我写的"
   ```
   ❌ "请评分一下你刚才生成的这段摘要"
   ✅ "我写了这段摘要，帮我评分一下"
   ```

否则模型可能：
- 偏向给自己高分
- 给出"积极向上"的客套话
- 避免指出严重问题

## 评估维度（按场景）

### 写作类
- 清晰度（clarity）
- 完整性（completeness）
- 简洁性（conciseness）
- 语气一致性（tone consistency）

### 代码类
- 正确性（correctness）
- 可读性（readability）
- 性能（performance）
- 安全性（security）

### 分析类
- 论据充分性（evidence）
- 逻辑严密性（logic）
- 覆盖度（coverage）

## 工作流：评估 → 改进循环

```
1. 模型生成初稿
2. 新会话中要求模型评分 + 提改进建议
3. 把改进建议反馈给原模型（或新会话）
4. 模型基于反馈改写
5. 必要时重复
```

## 与其他技术的关系

- 是 [[Iterative_Refinement|迭代精化]] 的自动化版本
- 可以放入 [[Prompt_Chaining|提示链]] 中作为质量门
- 在 [[Agent_Skill|Agent 系统]] 中常用于自动审查

## 注意事项

- 评估本身也可能有偏差：用多个模型交叉验证
- 评估成本不低：会增加 [[Token_Efficiency|token]] 消耗
- 不是万能的：模型在自己不擅长的领域评估也不擅长

## 关联连接

- [[Prompt_Engineering]] — 提示工程总览
- [[Iterative_Refinement]] — 迭代精化
- [[Prompt_Chaining]] — 提示链
- [[摘要-tech-with-tim-prompt-engineering-course]] — 来源
