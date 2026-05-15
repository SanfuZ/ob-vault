---
title: "Claude Code"
type: entity
tags: [工具, AI智能体, CLI, Anthropic, 编程助手]
sources: [raw/03-transcripts/2026-05-15-Obsidian CLI 详细教程：官方命令行工具，激进拥抱智能体，高效 + 自动化 + 降低Token消耗。.md]
last_updated: 2026-05-16
---

## 定义

Claude Code 是 [[Anthropic]] 推出的智能体编程工具,基于 [[Claude]] 模型家族构建,以命令行界面(CLI)为主要交互方式。它能够阅读代码、执行命令、修改文件,并在用户授权下自动完成多步骤的编程和自动化任务。

## 核心定位

- **AI Agent 工具**:不仅是聊天,而是能直接操作文件系统、运行命令的智能体
- **CLI 优先**:命令行驱动,便于与其他工具(如 [[Obsidian_CLI]])链式组合
- **Skill 化扩展**:支持 [[Agent_Skill]] 机制,通过外部 Skills 扩展能力

## 与 Obsidian 的结合

通过安装 [[Kepano]] 在 GitHub 发布的 `obsidian-skills`,Claude Code 可以:
- 使用 Obsidian CLI 操作笔记库
- 创建笔记时自动触发模板机制
- 查询双链、标签、元数据等结构信息
- 大幅降低操作笔记库的 Token 消耗(参见 [[Token_Efficiency]])

## 衍生与替代

视频中提到 **OpenClaw**(中文社区昵称"大龙虾"):
- Claude Code 的开源替代品(或基于其设计的衍生)
- 视频作者反映其 Token 消耗显著,使用时需谨慎

## 注意事项

- **确定性任务建议改用代码/工作流**:视频作者强调,智能体调用消耗 Token 飞快,确定性高的任务用 Python 脚本或 [[n8n]] 工作流更经济
- 与 [[Gemini_CLI]] 对比:Gemini CLI 提供大量免费 Token 额度,Claude Code 相对昂贵

## 关联连接
- [[Anthropic]] — 开发公司
- [[Claude]] — 底层模型家族
- [[Agent_Skill]] — 扩展机制
- [[Obsidian_CLI]] — 典型集成场景
- [[Gemini_CLI]] — 类似工具对比
- [[Token_Efficiency]] — 重要的成本考量
- [[摘要-obsidian-cli-tutorial]] — 来源教程
