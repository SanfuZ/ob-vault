---
title: "UML（统一建模语言）"
type: entity
tags: [软件工程, 建模, 标准, 工具]
sources:
  - raw/01-articles/设计模式中的对象关系.md
last_updated: 2026-05-17
---

## 定义

**UML（Unified Modeling Language，统一建模语言）** 是一种用于软件工程的标准化通用建模语言。它通过图形化方式描述软件系统的结构、行为、交互和部署，被广泛用于面向对象设计（OOD）与文档化沟通。

## 主要图类型

- **类图（Class Diagram）**：描述类、属性、方法与关系
- **对象图（Object Diagram）**：类的具体实例
- **时序图（Sequence Diagram）**：消息传递时间顺序
- **用例图（Use Case Diagram）**：系统功能与角色
- **状态图（State Diagram）**：状态转换
- **活动图（Activity Diagram）**：流程

## 类关系的 UML 表示

在 UML 类图中，[[Object_Relationships|对象关系]]通过不同符号区分：

| 关系 | UML 符号 | 含义 |
|------|----------|------|
| [[Dependency]] | 虚线箭头 ⇢ | 临时使用 |
| [[Association]] | 实线 — | 长期持有 |
| Aggregation（聚合） | 空心菱形 ◇— | 整体-部分（弱拥有） |
| [[Composition]] | 实心菱形 ◆— | 整体-部分（强拥有） |
| Generalization（继承） | 实线空心三角 △— | is-a 关系 |
| Realization（实现） | 虚线空心三角 △⇢ | 接口实现 |

## 关联连接

- [[Object_Relationships]] — UML 类关系的具体应用
- [[Association]] — 关联关系（UML：实线）
- [[Composition]] — 组合关系（UML：实心菱形）
- [[Dependency]] — 依赖关系（UML：虚线箭头）
- [[摘要-software-design-object-relationships]] — 来源摘要
