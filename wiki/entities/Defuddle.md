---
title: "Defuddle"
type: entity
tags: [工具, CLI, Obsidian, 网页剪藏, Skill, Markdown]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
last_updated: 2026-05-17
---

## 定义

**Defuddle** 是由 [[Obsidian]] CEO [[Kepano]] 开发的一款开源命令行工具，用于将网页内容转换为干净的 Markdown 格式。它是 Obsidian 官方 [[Web_Clipper|Web Clipper]] 剪藏插件的底层引擎。

> 在智能体时代，Defuddle Skill 是 Obsidian 用户必备的核心 Skill。

## 核心功能

1. **网页剪藏**：把任意网页 URL 转换为干净的 Markdown，去除导航/广告/侧边栏等噪声
2. **YouTube 视频转录**：通过 YouTube 官方 API 一键提取视频文案
3. **代码块与图片保留**：转换过程中正确保留代码块、图片、列表等结构

## 与同类工具的对比

| 特性 | Defuddle | yt-dlp（提取视频） |
|------|----------|---------------------|
| YouTube 视频转录 | ✅ 官方 API | 需配置 cookie |
| 稳定性 | 高（官方支持） | 受平台限制变化影响 |
| 配置成本 | 低 | 需 cookie 管理 |

## 安装方式

```bash
npm install -g defuddle
```

## 作为 [[Agent_Skill|Agent Skill]] 使用

Defuddle Skill 是 [[Kepano]] 在 GitHub `kepano/obsidian-skills` 仓库中发布的 5 个 Skill 之一。安装方式：

1. 通过命令行安装 defuddle 命令：`npm install -g defuddle`
2. 将 defuddle skill 文件夹放入智能体目录
3. 智能体即可处理"剪藏这个 URL"类指令

## 使用方式

### 用户直接命令行

```bash
defuddle <URL>
```

直接产生 Markdown 输出，[[Token_Efficiency|更节省 token]] 但英文资料需要额外 AI 翻译。

### 通过 AI 智能体

发送 URL 给智能体，让它调用 Defuddle Skill 转换并翻译。这种方式更便利，适合非英文资料。

### 通过 Obsidian Web Clipper

[[Web_Clipper]] 是 Obsidian 官方剪藏插件，内置 Defuddle 引擎。

## 三种处理路径对比

| 方式 | 优点 | 适用场景 |
|------|------|----------|
| `defuddle <URL>` 命令行 | 最省 token | 中文资料、批量处理 |
| Agent + Defuddle Skill | 自动翻译 | 英文资料 |
| Obsidian Web Clipper | 浏览器内一键 | 浏览中临时收藏 |

## 关联连接

- [[Kepano]] — Defuddle 作者，[[Obsidian]] CEO
- [[Obsidian]] — 母平台
- [[Web_Clipper]] — Obsidian 官方剪藏插件，使用 Defuddle 引擎
- [[Agent_Skill]] — Skill 标准
- [[Token_Efficiency]] — 直接命令行调用比 AI 转换更省 token
- [[摘要-obsidian-9-essential-agent-skills]] — 来源
