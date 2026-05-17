---
title: "Dependency（依赖关系）"
type: concept
tags: [软件设计, OOP, 面向对象, UML, 弱耦合]
sources:
  - raw/01-articles/设计模式中的对象关系.md
last_updated: 2026-05-17
---

## 定义

**依赖（Dependency）** 是面向对象设计中最弱的一种结构性关系。它表示一个类**在某个方法执行时"临时用一下"另一个类**，用完就走，不在结构上长期持有。

依赖是 uses-a（用一下）关系，与 [[Association|关联]]/[[Composition|组合]] 的本质区别是：**依赖是"用一下"，关联/组合是"持有住"**。

## 核心特征

1. **作用范围在方法级**：只出现在方法参数、局部变量或返回值中
2. **持续性是临时的**：仅在方法调用期间存在
3. **互不干涉生命周期**
4. **耦合强度最弱**
5. **UML 用虚线箭头 ⇢** 表示，以示其"轻量、临时"

## C++ 实现示例

```cpp
// 加油站：Car 在 refuel() 时才会用到它
class GasStation {
public:
    void pump(int liters) {
        std::cout << "加油站为车加了 " << liters << " 升油\n";
    }
};

class Car {
public:
    // 【依赖】GasStation 只作为参数出现，方法结束就忘了
    void refuel(GasStation& station) {
        station.pump(50);
    }
};
```

`GasStation` 不是 `Car` 类的字段，仅出现在方法签名中，方法结束后 `Car` 不再持有它。

## 三种关系对比

| 维度 | Dependency（依赖） | [[Association]]（关联） | [[Composition]]（组合） |
| --- | --- | --- | --- |
| 关系类型 | uses-a（用一下） | has-a（持有） | part-of（是其一部分） |
| 作用范围 | 方法/函数级 | 类级（成员） | 类级（成员） |
| 持续性 | 临时（方法调用期间） | 长期 | 长期且同生共死 |
| 生命周期 | 互不干涉 | 双方独立 | 部分依赖整体 |
| 耦合强度 | 最弱 | 中 | 最强 |
| C++ 体现 | 方法参数 / 局部变量 / 返回值 | 成员是裸指针/引用 | 成员是值或 `unique_ptr` |
| UML 符号 | 虚线箭头 ⇢ | 实线 — | 实心菱形 ◆— |

## 容易混淆的边界

### 边界一：把依赖"升级"成关联

通过构造函数注入往往把"依赖"升级为"关联"——一旦把对方存为成员，关系就从临时变成长期了：

```cpp
// 依赖：Logger 只在 process() 内部用一下
class OrderService {
    void process(Logger& log) { log.info("..."); }
};

// 关联：Logger 被存为成员变量
class OrderService {
    Logger* log;
public:
    OrderService(Logger* l) : log(l) {}  // [[Dependency_Injection|依赖注入]]
    void process() { log->info("..."); }
};
```

### 边界二：短暂存在但被存住，算什么？

判断标准**不是"用了多久"，而是"是不是类的结构组成部分"**：
- 哪怕方法里只调用一次，只要存为成员，就是 [[Association|关联]]
- 反之，哪怕调用持续好几小时，只要它只是个参数，就是依赖

## 何时使用依赖

| 场景 | 推荐 | 理由 |
| --- | --- | --- |
| 仅在某一两个方法中使用 | 参数（依赖） | 不污染类的结构 |
| 每次调用传入的不同 | 参数（依赖） | 本来就该外部决定 |
| 仅用于一次性的转换/计算 | 参数 / 返回值 | 临时性强 |

## 设计原则：最小可见原则

**用最弱够用的关系**。如果只需要一次性使用，就别提升为成员。每多知道一点就多 [[Coupling|耦合]] 一分。

关键问句：

> **这个东西是这个对象身份的一部分，还是只是它当前做这件事用一下？**

## 常见反模式

- ❌ 强行把"持有"扭曲成"使用"：如果 Car 的 Engine 也用参数传，每次都要传同一个 engine，违反直觉
- ❌ 同一组对象总是一起出现在多个方法里却不升级为成员：应当升级为类的"协作者"

## 关联连接

- [[Object_Relationships]] — 总览
- [[Association]] — 关联关系（对比）
- [[Composition]] — 组合关系（对比）
- [[Coupling]] — 依赖是最弱耦合
- [[Dependency_Injection]] — 依赖注入：通过构造函数将依赖转为关联
- [[摘要-software-design-object-relationships]] — 来源摘要
