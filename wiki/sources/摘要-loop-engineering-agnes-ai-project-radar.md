---
title: "摘要：Loop Engineering + Agnes AI，打造项目监控雷达"
type: source
tags: [B站, 视频字幕, Loop Engineering, Agnes AI, 项目雷达, 智能体]
sources: [raw/03-transcripts/2026-06-21-Loop Engineering+Agnes AI ，打造项目监控雷达.md]
last_updated: 2026-06-21
---

# 摘要：Loop Engineering + Agnes AI，打造项目监控雷达

> 原始来源：B 站「第四种黑猩猩CHIMP」| BV1G7jJ6nEQJ | 上传日期 2026-06-20

## 核心主旨

作者 Boris 通过一个实际案例——**每日自动扫描 GitHub Trending 并推送微信通知**——展示了什么叫 **Loop Engineering（循环工程）**：设计一个让 Agent 自主循环运行的系统，而不是手动为每次运行写提示词。

## 案例目标

让 Agent 每天自动完成：
1. 扫描 GitHub Trending
2. 给项目打分
3. 下载高分项目
4. 尝试安装运行
5. 发送微信通知，告知今天哪些项目值得看、哪些只是看着火但没用

## 系统设计

整个系统由一份提示词、一份历史记录和几个脚本组成，能每天自动跑起来。

### 文件结构

| 文件/目录 | 作用 |
|-----------|------|
| `prompt.md` | Agent 每次运行的固定流程 |
| `seen.txt` | 轻量去重索引，每行一个项目名/仓库名/日期/分数/是否通知过 |
| `history.md` | 高分项目的详细状态、评分理由、运行结果 |
| `reports/` | 按日期保存当天完整分析报告 |
| `workspace/` | 临时克隆项目和运行项目的地方 |
| 抓取脚本 | 抓 GitHub Trending |
| 通知脚本 | 发微信通知 |

### 核心设计思想

- **代码做稳定工具**：抓取、去重、发微信等确定性操作交给脚本
- **Markdown 保存状态**：用文件保存索引、历史、报告，避免上下文无限膨胀
- **Agent 负责判断和执行**：项目评分、深度分析、生成下一轮动作交给 Agent

## Agent 工作流程

1. **抓取脚本**返回去重后的全新项目列表
2. 按偏好**轻量打分**，维度包括：
   - 是否和 AI/开发工具相关
   - 是否有明显新意
   - star 增长是否异常
   - README 是否把问题讲清楚
   - 是否适合做短视频选题
3. **低分项目**：写入 `seen.txt` 和 `history.md`，只写一句跳过理由
4. **高分项目**：派**子 Agent** 深度分析，整理成摘要后发微信通知

## 为什么用子 Agent

跑陌生项目会产生大量脏数据（安装日志、报错堆栈、测试输出）。子 Agent 处理这些脏数据，主 Agent 只接收干净的最终分析结果，保持主 Agent 上下文清爽。单个项目失败不会影响主循环。

## 模型选择：Agnes 2.0 Flash

- 全模态、免费、无需信用卡
- 100 万 tokens 上下文窗口（灰度测试中）
- 采用 OpenAI Chat Completions 格式，可通过 `cc switch` 本地路由接入 Claude Code
- RPM 约 20 次/分钟，对个人足够
- 特别适合长期重复、上下文消耗大的后台任务

## 作者观点

免费模型最适合跑**长期重复、上下文又多、人工做起来很烦**的任务。GitHub 热门项目雷达只是一个小例子，同样思路还可以做：
- 论文雷达
- 竞品监控
- issue 追踪

## 关联连接

- [[Loop_Engineering]] — 该视频提出的核心概念
- [[Agnes_AI]] — 视频中使用的免费多模态模型
- [[project-github-radar-loop-engineering]] — 该案例的项目实现参考
- [[Claude_Code]] — 视频中用于搭建工作流的智能体工具
- [[Token_Efficiency]] — 长期自动化任务的成本优化
- [[Context_Engineering]] — 上下文管理的范式转变
