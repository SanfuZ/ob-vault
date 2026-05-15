---
title: "Gemini CLI"
type: entity
tags: [工具, AI智能体, CLI, Google, 编程助手]
sources: [raw/03-transcripts/2026-05-15-Obsidian CLI 详细教程：官方命令行工具，激进拥抱智能体，高效 + 自动化 + 降低Token消耗。.md]
last_updated: 2026-05-16
---

## 定义

Gemini CLI 是 [[Google]] 推出的智能体命令行工具,基于 [[Gemini]] 模型家族。它的核心特点是**提供大量免费 Token 额度**,因此在成本敏感的场景下广受欢迎。

## 核心定位

- **免费额度友好**:相比 [[Claude_Code]] 等付费工具,Gemini CLI 的免费额度更慷慨
- **CLI 智能体**:命令行驱动,可执行多步骤任务
- **支持 [[Agent_Skill]]**:可加载第三方 Skills 扩展能力

## 与 Obsidian 的结合

视频作者使用 Gemini CLI 演示如何让智能体操作 [[Obsidian]]:

### 工作流
1. 从 [[Kepano]] 的 GitHub 下载 `obsidian-skills`
2. 安装 Skills 到 Gemini CLI
3. 用自然语言下达指令,智能体自动调用 [[Obsidian_CLI]]

### 实战案例
> 让 Gemini CLI 获取 arXiv 上 AI 目录下的最新 10 篇论文,读取并翻译信息,整理成表格,在 Obsidian 中创建当日日记(标题"今日 AI 论文"),将表格添加到日记中。

智能体在创建日记时:
- 自动触发日记模板机制
- 笔记自动创建到 diary 文件夹
- 表格中包含可点击的 arXiv 论文链接

## 视频作者推荐理由

> 之所以使用 Gemini CLI,还是因为它有大量的免费 Token 额度...如果你的主要使用场景是 Obsidian,那可以尝试 Gemini CLI 和 opencode 这两个智能体工具,它们的免费 Token 额度还是很多的。

## 关联连接
- [[Google]] — 开发公司
- [[Gemini]] — 底层模型家族
- [[Agent_Skill]] — 扩展机制
- [[Obsidian_CLI]] — 典型集成场景
- [[Claude_Code]] — 类似工具对比
- [[Token_Efficiency]] — 选择该工具的核心考量
- [[摘要-obsidian-cli-tutorial]] — 来源教程
