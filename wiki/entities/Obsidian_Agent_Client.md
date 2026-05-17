---
title: "Obsidian Agent Client"
type: entity
tags: [工具, Obsidian, 插件, AI智能体, 多智能体]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
last_updated: 2026-05-17
---

## 定义

**Obsidian Agent Client** 是 [[Obsidian]] 中**最主流的多智能体客户端插件之一**。与 [[Claudian]] 只支持 [[Claude_Code]] 不同，它支持大部分主流智能体工具，让用户可在 Obsidian 内部统一调用任意 Agent。

## 支持的智能体

- [[Claude_Code]]（Anthropic 智能体编程工具）
- Codex（OpenAI 编程智能体）
- [[Gemini_CLI]]（Google 智能体）
- [[OpenCode]]（开源智能体工具）
- 阿里千问 Code
- 其他

## 安装方法

通过 [[BRAT]] 安装：

1. 安装 BRAT 插件
2. Add Beta plugin → 输入 Obsidian Agent Client 仓库地址

## 配置示例（以 [[OpenCode]] 为例）

进入插件设置，在 **Custom Agent** 中点击 **Add**：

1. **Agent ID** 和 **Display Name**：填写 `OpenCode`
2. **Path**：填入 OpenCode 的可执行路径
   - 不知道路径？打开命令行输入 `where opencode`（Windows）或 `which opencode`（macOS/Linux）
3. **Arguments**：按文档配置启动参数
   - 注意其中要包含 Obsidian 知识库的路径
4. 重启 Obsidian
5. 打开 AI 对话框测试，发送"你好"，如有 AI 回复则配置成功

## 与 [[Claudian]] 的对比

| 维度 | [[Claudian]] | Obsidian Agent Client |
|------|--------------|------------------------|
| 支持智能体 | 仅 Claude Code | 多个智能体 |
| 配置复杂度 | 低 | 中 |
| 灵活性 | 低 | 高 |
| 适合 | Claude 重度用户 | 多智能体使用者、想尝试不同 AI 的人 |

## 图标识别

两个主流插件的图标都是机器人图标。根据自己的需求二选一即可。

## 关联连接

- [[Claudian]] — 仅支持 Claude Code 的对应插件
- [[Claude_Code]] — 支持的智能体之一
- [[Gemini_CLI]] — 支持的智能体之一
- [[OpenCode]] — 支持的智能体之一
- [[Obsidian]] — 母平台
- [[BRAT]] — 安装工具
- [[摘要-obsidian-9-essential-agent-skills]] — 来源
