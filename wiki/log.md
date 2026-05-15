# Wiki 操作日志

---

## [2026-04-12] ingest | 批量摄入提示工程核心资料

### 处理文件清单

**Articles（5 篇）：**
- `raw/01-articles/提示设计策略  _  Gemini API.md` — Google Gemini 中文指南
- `raw/01-articles/Prompt Engineering in 2025_ Complete Guide for ChatGPT, Claude, and Gemini.md` — PromptBuilder 指南
- `raw/01-articles/The Complete Guide to AI Prompt Engineering in 2025-2026.md` — Espo.ai 指南
- `raw/01-articles/The Complete Prompt Engineering Guide (2025).md` — BrilliantPrompts 指南
- `raw/01-articles/Prompting best practices-Anthropic.md` — Anthropic 官方最佳实践

**Papers（2 篇）：**
- `raw/02-papers/Goolge-Prompt-Engineering-whitepaper.pdf` — Google 官方白皮书（65 页）
- `raw/02-papers/5C Prompt Contracts .pdf` — 5C 提示契约研究论文

### 创建的来源摘要（7 个）

| 文件 | 描述 |
|------|------|
| [[摘要-gemini-api-prompting-strategies]] | Gemini API 提示设计策略 |
| [[摘要-prompt-engineering-2025-guide-promptbuilder]] | Prompt Engineering 2025 完整指南 |
| [[摘要-ai-prompt-engineering-2025-2026-espo]] | AI 提示工程 2025-2026 指南 |
| [[摘要-complete-prompt-engineering-guide-2025]] | 完整提示工程指南 2025 |
| [[摘要-anthropic-prompting-best-practices]] | Anthropic 提示最佳实践 |
| [[摘要-google-prompt-engineering-whitepaper]] | Google 提示工程白皮书 |
| [[摘要-5c-prompt-contracts-paper]] | 5C Prompt Contracts 论文 |

### 创建的概念页面（5 个）

| 页面 | 类型 | 核心内容 |
|------|------|----------|
| [[Prompt_Engineering]] | 核心概念 | 提示工程总览、七大要素、技术分类 |
| [[5C_Framework]] | 框架 | 5C 提示契约框架详解 |
| [[Chain_of_Thought]] | 技术 | 思维链技术、Zero-shot/Few-shot CoT |
| [[Few_Shot_Prompting]] | 技术 | 少样本提示最佳实践 |
| [[Context_Engineering]] | 范式 | 从提示工程到上下文工程的转变 |

### 创建的实体页面（4 个）

| 页面 | 描述 |
|------|------|
| [[Google]] | Google 公司及其 AI 产品 |
| [[Anthropic]] | Anthropic 公司及其安全研究 |
| [[Gemini]] | Google Gemini 模型家族特性 |
| [[Claude]] | Anthropic Claude 模型家族特性 |

### 冲突与发现

**知识冲突（已标注）：**
- 在 [[5C_Framework]] 页面中记录了「5C vs 复杂 DSL 之争」的知识冲突

**重要发现：**
1. **提示长度悖论**：研究表明 150-300 词是最佳长度，超过 3,000 tokens 性能显著下降
2. **CoT 悖论**：现代推理模型（GPT-5, Claude 4, Gemini 3）内部自动推理，显式 CoT 反而可能有害
3. **5C 效率优势**：平均仅需 54 tokens 输入，比 DSL 节省 6 倍以上
4. **Gemini 简化趋势**：Gemini 3 不再需要复杂提示工程，建议使用简化提示
5. **Context Engineering 范式**：行业正在从单个提示优化转向系统上下文管理

### 更新文件
- [[index.md]] — 重新组织了总目录结构
- [[log.md]] — 记录本次操作（本条目）

### 归档操作
所有 7 个源文件已移动至 `raw/09-archive/` 目录。

---

## [2026-04-12] query | 基于 5C Framework 设计 Markdown 笔记提示词

- **查询**: 根据 5C Framework 设计撰写 Markdown 格式知识笔记的提示词
- **引用**: [[5C_Framework]]
- **输出**: 已创建 synthesis 文件 [[5c-prompt-markdown-note-taking]]
- **更新**: [[index.md]] 已注册新 synthesis

### 提示词特色
- 遵循 5C 框架：Character/Cause/Constraint/Contingency/Calibration
- Token 高效（约 150 tokens）
- 包含完整的使用示例和变体建议
- 内置质量自检机制（Calibration）

---

## [2026-04-12] lint | 知识库健康检查

### ✅ 绿灯项
- 所有来源页面均有双向链接引用
- 所有概念页面均有双向链接引用
- 所有实体页面均有双向链接引用
- 新知识冲突已正确标注

### ⚠️ 黄灯项
- **8 个未同步索引（文件不存在但 index.md 已注册）**：
  - [[Zero_Shot_Prompting]] — 计划中，待创建
  - [[APE_Framework]] — 计划中，待创建
  - [[CO-STAR_Framework]] — 计划中，待创建
  - [[RISEN_Framework]] — 计划中，待创建
  - [[CRAFT_Framework]] — 计划中，待创建
  - [[POWER_Framework]] — 计划中，待创建
  - [[ReAct]] — 计划中，待创建
  - [[Tree_of_Thoughts]] — 计划中，待创建
  - [[RAG]] — 计划中，待创建

- **10 个死链（页面引用不存在的文件）**：
  - [[Constitutional_AI]]（被 Anthropic.md 引用）
  - [[Adaptive_Thinking]]（被 Anthropic.md、Claude.md 引用）
  - [[Agentic_Systems]]（被 Anthropic.md、Context_Engineering.md 引用）
  - [[Token_Efficiency]]（被 5C_Framework.md、摘要-5c-prompt-contracts-paper.md 引用）
  - [[Prompt_Design]]（被 5C_Framework.md、摘要-5c-prompt-contracts-paper.md 引用）
  - [[DSL_Prompting]]（被 5C_Framework.md 引用）
  - [[ChatGPT]]（被 摘要-complete-prompt-engineering-guide-2025.md 引用）
  - [[DeepMind]]（被 Google.md 引用）

### ❌ 红灯项
- **1 个待解决的知识冲突**：
  - [[5C_Framework]] 页面中记录的「5C vs 复杂 DSL 之争」（概念性标注，待补充具体冲突内容）

### 🛠️ 下一步行动
1. **高优先级**：创建核心概念页面（Zero_Shot_Prompting、ReAct、RAG）
2. **中优先级**：创建框架页面（APE、CO-STAR、RISEN、CRAFT、POWER）
3. **低优先级**：补充辅助概念（Constitutional_AI、DeepMind、Token_Efficiency 等）
4. **可选**：完善 5C_Framework 的知识冲突区块，补充具体争议点

### 统计
- 总文件数：19 个（不含 index/log）
- 存在页面：19 个
- 孤儿页面：0 个
- 未同步索引：8 个（计划中的框架/技术）
- 死链：10 个（辅助/补充概念）
- 知识冲突：1 个（概念性标注）

---

## [2026-05-16] ingest | 引入 Obsidian CLI 教程与 AI 智能体生态知识

### 处理文件

**Transcripts（1 篇）:**
- `raw/03-transcripts/2026-05-15-Obsidian CLI 详细教程:官方命令行工具,激进拥抱智能体,高效 + 自动化 + 降低Token消耗。.md` — B 站「杰森的效率工坊」视频教程

### 创建的来源摘要（1 个）

| 文件 | 描述 |
|------|------|
| [[摘要-obsidian-cli-tutorial]] | Obsidian CLI 详细教程:官方命令行工具拥抱智能体 |

### 创建的实体页面（6 个）

| 页面 | 类型 | 核心内容 |
|------|------|----------|
| [[Obsidian]] | 笔记软件 | 本地优先 Markdown 笔记软件,定位与战略 |
| [[Obsidian_CLI]] | 工具 | 官方 CLI 工具详解,机制/优势/使用场景 |
| [[Kepano]] | 人物 | Obsidian CEO,Skills 作者,Local-First 倡导者 |
| [[Claude_Code]] | 工具 | Anthropic 智能体编程工具(CLI) |
| [[Gemini_CLI]] | 工具 | Google 智能体命令行工具(免费额度优先) |
| [[n8n]] | 工具 | 开源可视化工作流自动化平台 |

### 创建的概念页面（4 个）

| 页面 | 类型 | 核心内容 |
|------|------|----------|
| [[Agent_Skill]] | 标准 | 智能体扩展能力的标准化包 |
| [[IPC]] | 架构 | 进程间通信,Obsidian CLI 的底层机制 |
| [[Local_First]] | 哲学 | 本地优先的设计范式与数据主权理念 |
| [[Token_Efficiency]] | 跨主题 | 跨提示工程与工具集成的 Token 优化(同时修复死链) |

### 重要发现

1. **AI 操作软件的范式转变**:从"文件系统读写"到"IPC 进程通信",带来 Token 消耗数量级下降(数百万 → ~100)
2. **Obsidian 的智能体战略**:不做官方 AI,而是通过 CLI + Agent Skills 接入所有第三方智能体,既保持 Local-First,又拥抱智能体生态
3. **工作流 vs 智能体的选择原则**:"越是确定性的任务,越要用工作流和代码,而不是智能体" —— Token 成本的核心权衡
4. **Token Efficiency 跨主题桥接**:5C 框架的"提示层 Token 效率"与 Obsidian CLI 的"工具层 Token 效率"在 [[Token_Efficiency]] 页面统一,形成跨主题知识桥接

### 修复死链
- [[Token_Efficiency]] — 此前被 [[5C_Framework]] 和 [[摘要-5c-prompt-contracts-paper]] 引用但缺失,本次创建并扩展覆盖

### 冲突
无知识冲突。本次引入的智能体生态主题与已有的提示工程主题相互正交、有机互补。

### 更新文件
- [[index.md]] — 新增「AI 智能体 × Obsidian」分类,扩展 Sources/Entities/Concepts 三大区
- [[log.md]] — 记录本次操作（本条目）

### 归档操作
源文件已移动至 `raw/09-archive/` 目录。

---
