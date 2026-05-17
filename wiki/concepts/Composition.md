---
title: "Composition（组合关系）"
type: concept
tags: [软件设计, OOP, 面向对象, UML, 强耦合]
sources:
  - raw/01-articles/设计模式中的对象关系.md
last_updated: 2026-05-17
---

## 定义

**组合（Composition）** 是面向对象设计中最强的结构性关系，表示**"整体—部分"且生命周期完全绑定**——部分对象随整体而生、随整体而灭，由整体独占拥有。

组合关系是 part-of（是其一部分）关系，是 OOP 中 [[Coupling|耦合]] 最强的形式。

## 核心特征

1. **生命周期绑定**：部分必须随整体一起销毁，无法独立存在
2. **独占拥有**：一个部分对象只能属于一个整体对象
3. **强耦合**：耦合强度最高
4. **C++ 实现**：值成员（栈对象）或 `std::unique_ptr`（堆对象独占）

## C++ 实现示例

```cpp
class Engine {
public:
    Engine()  { std::cout << "  Engine 诞生\n"; }
    ~Engine() { std::cout << "  Engine 销毁\n"; }
};

class Car {
private:
    Engine engine;   // 【组合】值成员 —— Engine 是 Car 的一部分
public:
    Car()  { std::cout << "Car 诞生（同时构造 Engine）\n"; }
    ~Car() { std::cout << "Car 销毁（同时析构 Engine）\n"; }
};

int main() {
    Car myCar;      // → Engine 自动出生
}                   // Car 销毁 → Engine 一起死
```

**输出：**
```
  Engine 诞生
Car 诞生（同时构造 Engine）
Car 销毁（同时析构 Engine）
  Engine 销毁
```

## 与关联的对比

| 维度 | [[Association]]（关联） | Composition（组合） |
| --- | --- | --- |
| 生命周期 | 双方独立 | 部分依赖整体，同生共死 |
| 所有权 | 无所有权 | 整体独占拥有部分 |
| 耦合强度 | 弱~中 | 最强 |
| 共享性 | 可被多个对象关联 | 一个部分只属于一个整体 |
| C++ 实现 | 裸指针 / 引用 / `weak_ptr` | 值成员 / `unique_ptr` |
| UML 符号 | 普通直线 | 实心菱形（指向整体侧） |
| 典型例子 | 司机—汽车、学生—老师 | 汽车—引擎、人—心脏 |

## 判断法则

> **问自己一句话：如果"整体"被销毁了，"部分"还能不能继续存活并被别人使用？**
> - **能** → [[Association]]（用指针/引用，不管生命周期）
> - **不能** → Composition（用值成员或 `unique_ptr`，负责其生命周期）

## 何时使用组合

- 部分对象在概念上"不能独立存在"（如：心脏不能离开人独立存在）
- 部分对象的生命周期天然受整体约束
- 不需要共享给其他整体对象
- 需要最强的生命周期保证

## 常见误用

- ❌ **把可共享对象做成组合**：例如把 Driver 作为 Car 的值成员，会导致 Driver 无法在多辆车之间共享
- ❌ **为了"包含"而组合**：如果部分对象有自己独立的概念意义，应该用关联或聚合

## 关联连接

- [[Object_Relationships]] — 总览
- [[Association]] — 关联关系（对比）
- [[Dependency]] — 依赖关系（对比）
- [[Coupling]] — 组合是最强耦合
- [[摘要-software-design-object-relationships]] — 来源摘要
