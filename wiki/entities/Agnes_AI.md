---
title: "Agnes AI"
type: entity
tags: [多模态模型, 免费API, LLM, 基础模型]
sources: [raw/03-transcripts/2026-06-21-Loop Engineering+Agnes AI ，打造项目监控雷达.md]
last_updated: 2026-06-21
---

# Agnes AI

**Agnes AI** 是一家专注于多模态基础模型（Multimodal Foundation Models）的公司，提供文本、图片、视频三种模型，并全部免费开放使用，无需绑定信用卡。

## 核心产品

### Agnes 2.0 Flash
- **类型**：文本大模型
- **价格**：免费
- **上下文窗口**：100 万 tokens（灰度测试中）
- **RPM**：约 20 次请求/分钟
- **总调用量**：截至视频发布时，Agnes 全模态总调用量超过 3.12 万亿 tokens，其中 Agnes 2.0 Flash 贡献了约 1.9 万亿

### 图片与视频模型
- **图片模型**：支持 4K 输出
- **视频模型**：支持文生视频、视频+声音、音画同步输出，支持 720P 和 1080P，全部免费

## 适用场景

根据字幕中的实战经验，Agnes 2.0 Flash 特别适合：

1. **长期重复的后台任务**：如每日扫描 GitHub Trending、论文雷达、竞品监控
2. **上下文消耗大的任务**：反复读取 README、日志、历史 Markdown 等长上下文场景
3. **个人实验与自动化工作流**：免费 + 大上下文，适合低成本持续运行

## 接入方式

Agnes AI 采用 **OpenAI 兼容的 Chat Completions 格式**，可以通过本地路由工具（如 `cc switch`）接入 Claude Code 等智能体工具使用。

## 关联连接

- [[Loop_Engineering]] — 视频中用 Agnes 2.0 Flash 驱动循环工程的工作流
- [[摘要-loop-engineering-agnes-ai-project-radar]] — 该视频字幕的来源摘要
- [[project-github-radar-loop-engineering]] — 基于 Loop Engineering 的 GitHub 项目雷达实现
- [[Claude_Code]] — 视频中使用的智能体编程工具
- [[Token_Efficiency]] — 长期自动化任务的 Token 成本优化思路
