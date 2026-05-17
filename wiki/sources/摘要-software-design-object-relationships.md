---
title: "摘要-software-design-object-relationships"
type: source
tags: [来源, 软件设计, OOP, C++, UML, 面向对象]
sources:
  - raw/01-articles/设计模式中的对象关系.md
last_updated: 2026-05-17
---

## 核心摘要

本文以 C++ 为案例语言，系统梳理面向对象设计中三种核心结构性关系：**关联（Association）**、**组合（Composition）** 和 **依赖（Dependency）**，并讨论它们的边界与设计取舍。

核心结论：

1. **三种关系的本质区别**：依赖是"用一下"（方法参数），关联是"知道并长期持有"（成员变量、不管生命周期），组合是"拥有并同生共死"（值成员或独占智能指针）。
2. **判断口诀**：「**状态进字段，操作走参数**」——是身份的一部分用成员，仅做一次性使用用参数。
3. **设计原则**：让代码结构反映真实语义关系；不是越弱越好，而是"匹配现实 + 用最弱够用的"。
4. **延伸原则**：依赖倒置 + 依赖注入、迪米特法则（Law of Demeter）、SRP（单一职责原则）。

## 关联连接

- [[Object_Relationships]] — 总览：三种结构性关系的对比框架
- [[Association]] — 关联关系详解
- [[Composition]] — 组合关系详解
- [[Dependency]] — 依赖关系详解
- [[Coupling]] — 耦合强度概念
- [[UML]] — 统一建模语言
