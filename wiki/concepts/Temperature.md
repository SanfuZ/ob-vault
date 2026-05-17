---
title: "Temperature（温度参数）"
type: concept
tags: [LLM, 模型参数, API, 输出控制]
sources:
  - raw/03-transcripts/Prompt Engineering Full Course.md
  - raw/02-papers/Goolge-Prompt-Engineering-whitepaper.pdf
last_updated: 2026-05-17
---

## 定义

**Temperature（温度）** 是 LLM API 中的核心采样参数，控制模型输出的**确定性 vs 随机性**：

- **低温度（如 0.0-0.3）**：模型输出更确定、可重复
- **高温度（如 0.7-1.0+）**：模型输出更有创造性、多样化

## 工作原理

LLM 输出每个 token 时，会基于上下文计算所有可能 token 的概率分布。Temperature 控制如何从这个分布中采样：

- **T = 0**：永远选择概率最高的 token（贪婪解码）
- **T < 1**：让分布更尖锐，倾向高概率 token
- **T = 1**：按原始概率分布采样
- **T > 1**：让分布更平缓，低概率 token 也有机会出现

## 类比

> LLM 默认是 **non-deterministic**（非确定性）的：同样的输入可能得到不同的输出。Temperature 就是控制"有多随机"。

| 类比 | 类比对象 |
|------|----------|
| 笔的开合 | 总是按下（deterministic） |
| 掷骰子 | 高随机（non-deterministic，T 高） |

## 使用建议

### 低温度（0.0 - 0.3）

适用：
- 结构化输出（[[Structured_Output|JSON / 表格]]）
- 代码生成
- 事实陈述、文档摘要
- 分类任务（"情感是正还是负"）
- 需要可重复结果的场景

### 中等温度（0.3 - 0.7）

适用：
- 一般对话
- 平衡创造性与准确性的任务
- 写作类任务（博客、邮件）

### 高温度（0.7 - 1.0+）

适用：
- 头脑风暴
- 创意写作（小说、诗歌、广告语）
- 多样化输出（同一问题生成多个方案）
- 高级规划（不确定的探索）

## 调参建议

> 如果输出太随机 → 降低温度
> 如果输出太重复 → 升高温度
> 默认值通常在 0.7 左右；ChatGPT/Claude UI 默认偏低

## 与其他参数的关系

| 参数 | 作用 |
|------|------|
| Temperature | 全局采样分布陡峭度 |
| Top-p（核采样） | 仅从累积概率前 p% 的 token 中采样 |
| Top-k | 仅从概率前 k 个 token 中采样 |

通常调一个就够了：Temperature 是最常用的。

## 使用场景示例

| 任务 | 推荐 Temperature |
|------|------------------|
| 提取实体（JSON） | 0.0 |
| 代码补全 | 0.0 - 0.3 |
| 客户邮件回复 | 0.3 - 0.5 |
| 一般对话 | 0.5 - 0.7 |
| 营销文案 | 0.7 - 0.9 |
| 故事创作 | 0.8 - 1.0 |

## 注意事项

- 默认 UI（ChatGPT/Claude.ai）通常已设定温度，无法直接调整
- API 调用时才能精确控制
- **现代推理模型（如 [[Claude]] 4.x）**：温度设置作用减弱，模型内部会智能调整
- Temperature 0 时仍可能有微小随机性（GPU 计算的非确定性）

## 关联连接

- [[Prompt_Engineering]] — 提示工程总览
- [[Structured_Output]] — 结构化输出常配合低温
- [[Self_Evaluation]] — 评估可用低温度提高一致性
- [[Claude]] — Claude 模型参数说明
- [[摘要-tech-with-tim-prompt-engineering-course]] — 来源
- [[摘要-google-prompt-engineering-whitepaper]] — Google 白皮书也讨论了温度
