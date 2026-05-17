---
title: "Tutor Skill"
type: entity
tags: [工具, AI智能体, Skill, 学习, Obsidian, MOC]
sources:
  - raw/03-transcripts/2026-05-15-如何为 Obsidian 配置 AI Agent？9 个必备 Skill 详解与安装指南.md
last_updated: 2026-05-17
---

## 定义

**Tutor Skill** 是一个 [[Agent_Skill|Agent Skill]]，能够把用户提供的文档资料（PDF、Markdown、GitHub 项目等）一键转换为一个**完整的 [[Obsidian]] 知识库**，包含：

- 分类文件夹结构
- 原子化的知识笔记（[[Atomic_Note]]）
- 双向链接关联
- [[MOC|MOC 内容地图]]
- 测试与学习仪表板

> Tutor Skill 是绝大多数学习场景下最值得安装的 Skill。

## 与 [[Scholar_Skill]] 的关系

两者都是深度学习类 Skill，区别在于：

| 维度 | Tutor Skill | Scholar Skill |
|------|-------------|---------------|
| 适用场景 | 学习文档、考试备考、面试 | 学术科研、论文深读 |
| 任务时长 | 较短 | 长周期（数小时） |
| Token 消耗 | 中等 | 极高 |
| 工作流复杂度 | 标准 | 重度编排（含记忆管理、异步任务） |
| 智能体依赖 | 通用 | 深度依赖 OpenClaw |
| 支持代码仓库 | ✅ 支持分析 GitHub 项目 | ❌ 专注论文 |
| 推荐程度 | ⭐⭐⭐⭐⭐ 重点推荐 | 仅学术需要时 |

## 工作流程

### 准备

```
my_project/
├── resources/    ← 把要学习的 PDF/资料放这里
└── StudyVault/   ← Skill 会在这里创建完整知识库
```

> 注意：`resources` 和 `StudyVault` 是 Skill 的**硬性命名规定**。

### 执行步骤

1. 在智能体（如 [[OpenCode]]）中打开项目目录
2. 输入 `/tutor-setup`
3. Skill 自动生成提示词并启动
4. 智能体长时间工作，构建完整知识库
5. 用 Obsidian 打开 `StudyVault` 文件夹

### 后续操作

- `/tutor` 生成测试题（检验学习成果）
- 自动生成学习仪表板（[[MOC]] 形式）
- 展示对每个知识领域的掌握程度

## 产出特色

### 1. 完整的 Obsidian 知识库

- 分类文件夹
- 原子笔记（[[Atomic_Note]]）
- 双向链接构建知识图谱
- [[MOC]] 内容地图笔记

### 2. 知识图谱关联

笔记之间用 Obsidian 双链关联，在「图谱视图」中可看到完整网络。

### 3. 代码块结构图

笔记中用代码块绘制概念结构图（如 Mermaid 流程图），增强可视化。

### 4. 考试专项训练

针对考试场景生成测试笔记，**特别适合准备考试或面试**。

## 适用场景

- 📚 想快速掌握一个新知识领域
- 📝 准备考试或面试
- 💻 想快速理解一个 GitHub 开源项目
- 📖 已有专业 PDF 但缺乏学习路径

## 关联连接

- [[Scholar_Skill]] — 同类但更学术化
- [[Obsidian]] — 目标知识库平台
- [[Agent_Skill]] — Skill 标准
- [[MOC]] — Skill 产出的内容组织方式
- [[Atomic_Note]] — Skill 产出的笔记单元
- [[OpenCode]] — 推荐宿主智能体
- [[Token_Efficiency]] — Skill 对 token 的消耗权衡
- [[摘要-obsidian-9-essential-agent-skills]] — 来源
