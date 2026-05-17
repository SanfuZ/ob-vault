---
title: "System Prompt vs User Prompt（系统提示与用户提示）"
type: concept
tags: [提示工程, API, 模型架构]
sources:
  - raw/03-transcripts/Prompt Engineering Full Course.md
last_updated: 2026-05-17
---

## 定义

在 LLM 的多轮对话架构中，**System Prompt（系统提示）** 与 **User Prompt（用户提示）** 是两种不同角色的提示：

- **System Prompt**：设定模型的身份、规则、风格，**通常对终端用户不可见**，所有对话都先读取此提示
- **User Prompt**：用户每次实际输入的内容，是模型对话的主要驱动

## 角色对比

| 维度 | System Prompt | User Prompt |
|------|---------------|-------------|
| **作用** | 设定模型的"人设"和"规则" | 表达具体的任务/问题 |
| **频率** | 一次设定，长期使用 | 每次对话都会变化 |
| **可见性** | 通常对终端用户隐藏 | 用户直接输入 |
| **优先级** | 高，模型优先遵守 | 受 System Prompt 约束 |

## 实例

```
[System Prompt]
你是一位资深的编程助手，专长是 Python。
回答时使用代码示例。不要假设用户的水平。
不要使用 emoji。

[User Prompt]
如何在 Python 中读取文件的第一行？
```

模型每次都会读取 System Prompt 在前，然后处理 User Prompt。

## 在不同产品中的体现

### ChatGPT / Claude.ai

可在设置中配置 **Custom Instructions** 或 **Personality**，本质就是 System Prompt：

```
- 采用怀疑式提问方法
- 采取前瞻性视角
- 健谈、对话式
```

### Cursor / Claude Code

为编程任务定制 System Prompt：
- "你是一位编程助手..."
- 注入项目上下文（如 CLAUDE.md 文件）

### API 开发

```python
client.messages.create(
    system="You're a helpful coding assistant...",  # System Prompt
    messages=[
        {"role": "user", "content": "How to..."}    # User Prompt
    ]
)
```

## 设计 System Prompt 的最佳实践

1. **简洁明确**：避免冗长，挑选必要的规则
2. **角色 + 行为 + 约束**：明确身份、要做什么、不要做什么
3. **不要重复每次告诉**：System Prompt 已设定后，User Prompt 中不必重复
4. **对 [[Claude]] 4.x**：避免过激词如"CRITICAL"、"YOU MUST"，简洁陈述即可

## 与其他概念的关系

- 是 [[Context_Engineering|上下文工程]] 的重要部分
- 通常包含 [[Constraints_and_Negatives|约束指令]]
- 配合 [[Few_Shot_Prompting|示例]] 形成完整的提示策略

## 注意事项

- 早期模型对 System Prompt 遵循度不一，现代模型（GPT-4+、Claude 3+、Gemini）都严格遵守
- System Prompt 也消耗 [[Token_Efficiency|token]]，需要权衡

## 关联连接

- [[Prompt_Engineering]] — 提示工程总览
- [[Context_Engineering]] — 上下文工程
- [[Constraints_and_Negatives]] — 约束指令
- [[Few_Shot_Prompting]] — 通常在 System Prompt 中提供示例
- [[摘要-tech-with-tim-prompt-engineering-course]] — 来源
