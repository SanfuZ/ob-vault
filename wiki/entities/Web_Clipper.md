---
title: "Web Clipper"
type: entity
tags: [工具, Obsidian, 插件, 网页剪藏]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
last_updated: 2026-05-17
---

## 定义

**Web Clipper** 是 [[Obsidian]] 官方推出的网页剪藏浏览器插件，底层基于 [[Defuddle]] 工具，能够将网页内容一键转换为 Markdown 格式并保存到用户的 Obsidian 知识库。

## 核心功能

- **一键剪藏**：浏览网页时点击插件按钮即可保存
- **结构保留**：保留网页中的标题、列表、代码块、图片等结构
- **去除噪音**：自动过滤导航、广告、侧边栏等无关内容
- **直接入库**：保存到指定的 Obsidian Vault 路径

## 与 [[Defuddle]] 的关系

- [[Defuddle]] 是底层 CLI 工具，由 [[Kepano]] 开发
- Web Clipper 是基于 Defuddle 封装的浏览器插件，提供 GUI 交互
- 两者可互补：Web Clipper 用于浏览中剪藏，Defuddle 用于批量/自动化场景

## 使用场景

| 场景 | 推荐工具 |
|------|----------|
| 浏览网页时即兴收藏 | Web Clipper |
| AI 自动剪藏 + 翻译 | Defuddle Skill + Agent |
| 批量处理 URL 列表 | Defuddle 命令行 |

## 关联连接

- [[Defuddle]] — 底层 CLI 工具
- [[Kepano]] — 作者
- [[Obsidian]] — 母平台
- [[摘要-obsidian-9-essential-agent-skills]] — 来源
