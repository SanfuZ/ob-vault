---
title: "BRAT"
type: entity
tags: [工具, Obsidian, 插件, 测试版本管理]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
last_updated: 2026-05-17
---

## 定义

**BRAT（Beta Reviewer's Auto-update Tool）** 是 [[Obsidian]] 的一款**测试版插件管理工具**。它允许用户安装那些**未上架官方插件市场**的 Beta 版/未审核的第三方插件，常用于尝鲜或安装小众工具。

## 核心功能

- 安装尚未上架官方市场的 Beta 插件
- 通过 GitHub 仓库地址直接安装插件
- 自动检查更新
- 可批量管理多个测试插件

## 安装方式

BRAT 本身在 Obsidian 官方插件市场中可直接搜索安装。

## 典型使用流程

1. 在第三方插件市场中搜索并安装 BRAT
2. 打开 BRAT 设置
3. 点击 **Add Beta plugin**
4. 输入 GitHub 仓库地址（如 `username/plugin-name`）
5. 点击添加
6. 重启 Obsidian 即可启用

## 常见用途

- 安装 [[Claudian]]（Obsidian + Claude Code 集成）
- 安装 [[Obsidian_Agent_Client]]（多智能体客户端）
- 安装其他第三方智能体相关插件

## 与官方市场的对比

| 维度 | 官方插件市场 | BRAT |
|------|--------------|------|
| 审核 | ✅ 经过审核 | ❌ 未经审核 |
| 安全性 | 较高 | 取决于源 |
| 插件丰富度 | 高 | 更多（含 Beta） |
| 更新及时性 | 滞后 | 实时 |

## 安全提示

通过 BRAT 安装的插件未经 Obsidian 官方审核，**请确认 GitHub 仓库的可信度**。

## 关联连接

- [[Obsidian]] — 母平台
- [[Claudian]] — BRAT 常用安装目标
- [[Obsidian_Agent_Client]] — BRAT 常用安装目标
- [[摘要-obsidian-9-essential-agent-skills]] — 来源
