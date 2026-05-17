---
title: "Coupling（耦合）"
type: concept
tags: [软件设计, OOP, 架构, 设计原则]
sources:
  - raw/01-articles/设计模式中的对象关系.md
last_updated: 2026-05-17
---

## 定义

**耦合（Coupling）** 是衡量软件模块之间相互依赖程度的指标。耦合越强，模块间的关系越紧密，修改一方对另一方的影响越大；耦合越弱，模块独立性越高，可替换性越强。

## 耦合强度光谱

按从弱到强的顺序：

```
Dependency（依赖）  ←最弱
   ↓
Association（关联）
   ↓
Aggregation（聚合）
   ↓
Composition（组合）  ←最强
```

| 关系 | 耦合强度 | 体现形式 |
|------|----------|----------|
| [[Dependency]] | 最弱 | 方法参数、局部变量 |
| [[Association]] | 中 | 成员变量（裸指针/引用） |
| Aggregation（聚合） | 中（与 Association 实现相同，语义更强） | 成员变量（"整体—部分"语义） |
| [[Composition]] | 最强 | 值成员、`unique_ptr` |

## 重要原则：不是越弱越好

直觉上"依赖比关联耦合更弱，所以依赖更好"，这是误解。真正的原则是：

> **让代码结构反映真实的语义关系。** 强行把"持有"关系扭曲成"使用"关系，会让代码变得难用且不诚实。

举个反例，如果一个 `Car` 类把 `Engine` 也变成方法参数：

```cpp
void Car::accelerate(Engine& e) { e.ignite(); }    // 别扭
void Car::brake(Engine& e)      { e.cutFuel(); }
void Car::idle(Engine& e)       { e.maintain(); }
```

每次都传同一个 engine 是冗余且违反直觉的——Car 显然就是有 Engine 的，把它降级成依赖是对模型的扭曲。

## 降低耦合的方法

### 1. 依赖抽象而非具体类

通过接口/基类降低耦合：

```cpp
class Logger { public: virtual void info(const std::string&) = 0; };

class ReportGenerator {
    Logger* log;  // 依赖抽象，而非 ConsoleLogger 具体类
public:
    ReportGenerator(Logger* l) : log(l) {}  // [[Dependency_Injection|依赖注入]]
};
```

### 2. [[Law_of_Demeter|迪米特法则]]

> 一个对象只跟它的"邻居"说话，不要跟"邻居的邻居"打交道。

```cpp
// 高耦合：穿透多层
customer.getAddress().getCity().getZipCode();

// 低耦合：暴露所需接口
customer.getZipCode();
```

### 3. SRP（单一职责原则）

成员变量数量是个味道：一个类如果挂了 7、8 个成员对象，通常说明"协作者过多"，可能是 SRP 被破坏的信号——考虑拆分。

## 实战取舍：选择最弱够用的关系

```
要不要把 X 做成成员变量？
│
├── 类的每个/多数方法都需要它？ ──→ 是，做成员（关联）
├── X 表示对象身份/状态的一部分？ ──→ 是，做成员
├── 跨方法调用需要保留 X 的状态？ ──→ 是，做成员
├── 想要外部可替换以便测试？ ──→ 通过构造函数注入（成员 + 接口）
│
├── 只在一两个方法里用一下？ ──→ 做参数（依赖）
├── 每次调用都换不同的 X？ ──→ 做参数
└── 仅是一次性计算的输入？ ──→ 做参数
```

## 设计的艺术

> 设计的艺术是**诚实地表达关系，而不是机械地追求"低耦合"**：
> - 如果两者都讲得通，选 **更弱** 的
> - 但如果硬把"持有"扭曲为"使用"，就是把模型搞坏了

## 关联连接

- [[Object_Relationships]] — 总览：三种结构性关系
- [[Association]] — 中等耦合
- [[Composition]] — 最强耦合
- [[Dependency]] — 最弱耦合
- [[Dependency_Injection]] — 通过注入降低耦合
- [[Law_of_Demeter]] — 降低耦合的法则
- [[摘要-software-design-object-relationships]] — 来源摘要
