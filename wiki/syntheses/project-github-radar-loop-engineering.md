---
title: "项目：GitHub Trending 监控雷达（Loop Engineering 实现）"
type: synthesis
tags: [项目案例, Loop Engineering, GitHub, 智能体, 自动化, Agnes AI]
sources: [raw/03-transcripts/2026-06-21-Loop Engineering+Agnes AI ，打造项目监控雷达.md]
last_updated: 2026-06-21
---

# 项目：GitHub Trending 监控雷达（Loop Engineering 实现）

本项目是一个基于 [[Loop_Engineering]] 范式的实际案例：让 AI Agent 每天自动扫描 GitHub Trending，筛选、分析、尝试运行高分项目，最终通过微信推送最值得看的 3~5 个项目。

## 项目目标

自动化完成以下流程：
1. 抓取 GitHub Trending 项目
2. 去重并轻量打分
3. 对高分项目做深度分析（克隆、读 README、安装、运行、测试）
4. 生成每日报告
5. 推送微信通知

## 文件结构

```
project-github-radar/
├── prompt.md           # Agent 主循环的固定流程提示词
├── seen.txt            # 轻量去重索引
├── history.md          # 项目分析历史与跳过理由
├── reports/            # 按日期归档的完整分析报告
│   └── YYYY-MM-DD.md
├── workspace/          # 临时克隆和运行项目的工作目录
├── scripts/
│   ├── fetch_trending.py   # 抓取 GitHub Trending 并去重
│   └── notify_wechat.py    # 微信通知脚本
└── README.md           # 项目说明
```

## 核心分工

### 脚本层：确定性操作

| 脚本 | 职责 | 原因 |
|------|------|------|
| `fetch_trending.py` | 抓取 GitHub Trending、去重 | 去重是集合运算，确定性高，脚本又快又稳 |
| `notify_wechat.py` | 调用 Server 酱等微信服务号发送通知 | 单向通知，无需 Agent 临时判断 |

### Agent 层：判断性操作

| 步骤 | Agent 任务 |
|------|-----------|
| 1 | 读取抓取脚本返回的新项目列表 |
| 2 | 按维度轻量打分 |
| 3 | 低分项目：写入 `seen.txt` 和 `history.md`，记录跳过理由 |
| 4 | 高分项目：派子 Agent 深度分析 |
| 5 | 整理摘要，调用通知脚本发微信 |

## 评分维度

每个项目从以下维度打分：

1. **相关性**：是否和 AI/开发工具相关
2. **新意**：是否有明显的新意
3. **热度**：star 增长是否异常
4. **可读性**：README 是否把问题讲清楚
5. **选题价值**：是否适合做短视频选题

## 子 Agent 深度分析流程

对高分项目，子 Agent 执行：

1. 克隆项目到 `workspace/`
2. 读取 README、依赖文件、配置文件、issue
3. 搞清楚项目是干什么的、怎么启动
4. 尝试安装、运行、测试
5. 记录关键报错或成功启动命令
6. 输出项目分析：
   - 项目做什么
   - 为什么火
   - 技术含量
   - 是否跑通
   - 是否适合做视频

## 上下文管理策略

- `seen.txt` 只存项目标识（仓库名、日期、分数、通知状态），不存详细理由
- `history.md` 追加记录详细分析、跳过理由、运行结果
- 报告按日期归档，避免主 Agent 上下文膨胀
- 子 Agent 承担脏数据处理，主 Agent 上下文始终保持清爽

## 模型配置

推荐使用 [[Agnes_AI]] 的 **Agnes 2.0 Flash**：

- 免费、无需信用卡
- 100 万 tokens 上下文窗口
- OpenAI Chat Completions 兼容格式
- 可通过 `cc switch` 等本地路由工具接入 [[Claude_Code]]

## 接入 Claude Code 的步骤

1. 使用 `cc switch` 开启本地路由
2. 选择 cloud 路由模式
3. 添加 cloud code 配置：
   - 填写 Agnes API URL
   - 填写 API Key
   - 模型选择 `agnes-2.0-flash`
4. 让 Claude Code 根据目标结构自动生成 `prompt.md` 和脚本

## 开发顺序建议

1. 先开发 `fetch_trending.py`：测试能否正常抓取并去重
2. 再开发 `notify_wechat.py`：测试能否正常收到微信通知
3. 最后跑主 Agent：从抓取到发微信完整跑一遍

## 输出示例

### history.md
- 哪些项目分析过
- 哪些被跳过
- 为什么跳过

### reports/YYYY-MM-DD.md
- 当天完整的项目分析

### workspace/
- 高分项目的克隆副本
- 终端日志：安装/运行成功或失败的痕迹

### 微信通知
一条消息推送 3~5 个最值得看的项目，格式示例：

> 今天值得看的 GitHub 热门项目：
> - 项目 A：已成功跑通，适合深挖
> - 项目 B：有点意思，但 demo 跑失败了
> - 项目 C：适合做一期短视频

## 扩展思路

同样的 Loop Engineering 思路可以迁移到：

- 论文雷达
- 竞品监控
- issue 追踪
- 新闻摘要
- 社交媒体趋势监控

## 关联连接

- [[Loop_Engineering]] — 本项目采用的工程范式
- [[Agnes_AI]] — 推荐使用的免费大模型
- [[摘要-loop-engineering-agnes-ai-project-radar]] — 原始视频字幕摘要
- [[Claude_Code]] — 用于搭建和运行该工作流的智能体工具
- [[Token_Efficiency]] — 长期任务的 Token 成本控制
- [[Context_Engineering]] — 上下文管理范式
- [[Agent_Skill]] — 智能体扩展能力标准
