---
title: "Loop Engineering"
type: concept
tags: [循环工程, 智能体, 提示工程, 自动化, 工作流]
sources: [raw/03-transcripts/2026-06-21-Loop Engineering+Agnes AI ，打造项目监控雷达.md]
last_updated: 2026-06-21
---

# Loop Engineering

**Loop Engineering（循环工程）** 是一种让 AI Agent 自主运行循环任务的工程范式：不再为每一次执行手动编写提示词，而是设计一个循环结构，让 Agent 自己定时发现任务、处理任务、记录结果，并基于结果自动生成下一轮的提示词继续执行。

## 核心思想

> "别再手动一条一条给你的 agent 写提示词了。设计一个循环，让 agent 自己去定时发现任务、处理任务、记录结果，然后 agent 自己写下一轮的提示词接着跑。"

## 关键原则

### 1. 代码做稳定工具

确定性操作交给脚本/代码：
- 数据抓取
- 去重/集合运算
- 发送通知
- 文件读写

这样更稳定、更快、更省钱，避免让 Agent 反复做重复判断。

### 2. Markdown 保存状态

用轻量、可读的 Markdown/文本文件保存运行状态和历史：
- 索引文件（如 `seen.txt`）：只存关键字段，避免上下文膨胀
- 历史文件（如 `history.md`）：记录详细分析、跳过理由、运行结果
- 报告文件（`reports/YYYY-MM-DD.md`）：每日完整分析归档

### 3. Agent 负责判断和执行

Agent 的核心价值在于**不确定性的判断**：
- 项目评分与筛选
- 深度分析与总结
- 决定是否深入挖掘
- 生成下一轮动作

## 典型架构

```
prompt.md      → Agent 每次运行的固定流程
seen.txt       → 轻量去重索引
history.md     → 高分项目详细状态与运行记录
reports/       → 每日完整分析报告
workspace/     → 临时克隆项目、运行痕迹
scripts/       → 确定性脚本（抓取、通知等）
```

## 与子 Agent 协作

对于会产生大量脏数据的高分项目分析，可以派**子 Agent** 执行：
- 克隆项目
- 读 README、依赖配置、issue
- 尝试安装、运行、测试
- 记录成功/失败的关键信息

主 Agent 只接收干净的最终分析结果，保持自身上下文清爽。单个项目失败不会影响主循环。

## 与提示工程的关系

Loop Engineering 是**提示工程的延伸**：从优化单条提示词，转向设计一个能自我推进、自我记录的提示词系统。它强调：

- 提示词不是一次性消耗品，而是循环中的"控制协议"
- 上下文管理比提示词技巧更重要
- 让 Agent 自己维护和更新上下文

## 关联连接

- [[project-github-radar-loop-engineering]] — 一个具体的 Loop Engineering 实现案例
- [[Agnes_AI]] — 适合驱动 Loop Engineering 的免费大模型
- [[摘要-loop-engineering-agnes-ai-project-radar]] — 该概念的原始来源摘要
- [[Prompt_Engineering]] — 提示工程基础
- [[Context_Engineering]] — 从单个提示到系统上下文管理的范式
- [[ReAct]] — 推理与行动结合的 Agent 范式
- [[Token_Efficiency]] — 长期任务的 Token 成本优化
- [[Agent_Skill]] — 智能体扩展能力的标准化包
