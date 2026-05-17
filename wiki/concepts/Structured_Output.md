---
title: "Structured Output（结构化输出）"
type: concept
tags: [提示工程, 输出控制, JSON, 开发集成]
sources:
  - raw/03-transcripts/Prompt Engineering Full Course.md
last_updated: 2026-05-17
---

## 定义

**Structured Output（结构化输出）** 是一种提示工程技巧：要求模型以特定的结构化格式（如 JSON、表格、XML、Markdown）输出结果，**并提供精确的模板示例**，以便下游程序能可靠地解析和使用模型的响应。

## 核心思想

把模型当作"格式化的 API"：你定义输出 schema，模型按 schema 填充内容。

## 典型提示模板

```
对比 Trello、Monday.com、ClickUp（5-10 人的小团队场景）。
我想了解每个产品的主要功能、限制和价格。

请只输出有效的 JSON，不要任何其他文字。
JSON 格式如下：

{
  "products": [
    {
      "name": "...",
      "features": [...],
      "limitations": [...],
      "pricing": "..."
    }
  ]
}
```

## 常见输出格式

| 格式 | 适用场景 |
|------|----------|
| **JSON** | API 集成、数据库存储、前端渲染 |
| **Markdown 表格** | 报告、人类可读的对比 |
| **YAML** | 配置文件、Obsidian frontmatter |
| **XML** | 旧系统集成、复杂嵌套数据 |
| **CSV** | 数据导入、Excel 处理 |

## 为什么有效

1. **可靠解析**：明确格式后可以用 `json.loads()` 等程序化解析
2. **强制思维结构化**：模型按 schema 思考，避免遗漏字段
3. **隐式 [[Few_Shot_Prompting|示例]] 效果**：给出格式样例就像给了一个示范

## 最佳实践

### 1. 显式禁止无关文字

```
只输出 JSON。不要包含任何前后文字、解释或代码块标记。
```

### 2. 提供完整示例 schema

不要只写"JSON 格式"，要写出具体字段名和类型。

### 3. 与 [[Constraints_and_Negatives|约束指令]] 结合

```
- 字段名必须使用 snake_case
- 数组至少 3 项
- 不要包含 null
```

### 4. 失败回退策略

在代码层：尝试解析失败时重新请求，或用容错性更强的方法（如 JSON5、宽松解析器）。

## 与其他技术的关系

- 与 [[Few_Shot_Prompting|少样本提示]] 互补：提供输出样例本身就是 few-shot
- 通常配合较低的 [[Temperature|Temperature]]（如 0.0-0.3）使用，以保证格式稳定
- 是 [[Prompt_Chaining|提示链]] 中传递数据的关键

## 关联连接

- [[Prompt_Engineering]] — 提示工程总览
- [[Few_Shot_Prompting]] — 提供示例
- [[Constraints_and_Negatives]] — 严格的格式约束
- [[Temperature]] — 低温度保证结构稳定
- [[Prompt_Chaining]] — 提示链常用结构化输出传递
- [[摘要-tech-with-tim-prompt-engineering-course]] — 来源
