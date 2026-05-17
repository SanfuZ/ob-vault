---
title: "Dependency Injection（依赖注入）"
type: concept
tags: [软件设计, OOP, 设计原则, 依赖管理]
sources:
  - raw/01-articles/设计模式中的对象关系.md
last_updated: 2026-05-17
---

## 定义

**依赖注入（Dependency Injection，简称 DI）** 是面向对象设计中的一种实现技术：让对象通过外部（通常是构造函数、setter 或属性）传入其依赖的协作对象，而不是在内部自行创建（`new`）。

DI 是 **依赖倒置原则（Dependency Inversion Principle）** 的典型实现方式。

## 核心思想

```cpp
// ❌ 内部创建依赖：高 [[Coupling|耦合]]，难测试
class ReportGenerator {
    ConsoleLogger log;  // 具体类，无法替换
public:
    ReportGenerator() {}
};

// ✅ 通过构造函数注入：低耦合，可替换
class ReportGenerator {
    Logger* log;  // 依赖抽象（接口），而非具体类
public:
    ReportGenerator(Logger* l) : log(l) {}  // 注入！
};
```

## 两个核心原则

### 1. 依赖抽象，而非具体类

依赖于接口或基类，不依赖于具体的实现类。这样：
- 可以在运行时替换不同实现
- 便于单元测试（注入 mock）
- 降低 [[Coupling|耦合]] 强度

### 2. 通过构造函数注入，而不是内部 `new`

将依赖关系从"对象内部"提升到"使用者"层面，由使用者决定具体实现。

## 与对象关系的联系

构造函数注入往往把"[[Dependency|依赖]]"升级为"[[Association|关联]]"——一旦把对方存为成员，关系就从临时变成长期了：

```cpp
// 依赖关系：Logger 仅作为方法参数
class OrderService {
    void process(Logger& log) { log.info("..."); }
};

// 注入后变成关联：Logger 被存为成员
class OrderService {
    Logger* log;
public:
    OrderService(Logger* l) : log(l) {}  // 依赖注入
    void process() { log->info("..."); }
};
```

## 实际收益

- **可替换**：可以用不同的实现满足不同环境（生产 / 测试 / 调试）
- **可测试**：测试时注入 mock 对象
- **降低耦合**：耦合于接口而不是具体类
- **遵循 SRP**：对象专注于自己的职责，不操心依赖如何创建

## 关联连接

- [[Object_Relationships]] — 总览
- [[Dependency]] — 依赖关系
- [[Association]] — 注入后形成关联
- [[Coupling]] — 降低耦合的关键手段
- [[摘要-software-design-object-relationships]] — 来源摘要
