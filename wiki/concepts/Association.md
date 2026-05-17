---
title: "Association（关联关系）"
type: concept
tags: [软件设计, OOP, 面向对象, UML]
sources:
  - raw/01-articles/设计模式中的对象关系.md
last_updated: 2026-05-17
---

## 定义

**关联（Association）** 是 UML 中描述类与类之间的一种结构性关系，表示一个类**长期"知道"另一个类的存在（has-a 关系）**，通常通过成员变量（指针或引用）来实现。关联是稳定的引用，但**不负责对方的生命周期**。

## 核心特征

1. **长期持有**：与 [[Dependency]] 不同，关联是稳定的、贯穿对象生命的引用
2. **生命周期独立**：双方对象可以独立存在，互不负责创建和销毁
3. **方向性**：可以是单向或双向
4. **多重性**：可以是 1对1、1对多、多对多

## C++ 实现：教师—学生（双向、一对多关联）

```cpp
class Student {
private:
    std::string name;
    Teacher* tutor;   // 关联：指向 Teacher 的指针（不拥有）
public:
    void setTutor(Teacher* t) { tutor = t; }
};

class Teacher {
private:
    std::string name;
    std::vector<Student*> students;  // 关联：持有多个 Student 的指针（不拥有）
public:
    void addStudent(Student* s) {
        students.push_back(s);
        s->setTutor(this);   // 维护双向关联
    }
};
```

## 关键点解析

| 设计要点 | 体现 |
| --- | --- |
| 结构稳定 | `Student::tutor` 和 `Teacher::students` 是成员变量，不是函数参数 |
| 不负责生命周期 | 使用裸指针，`Teacher` 析构时不会 `delete` 学生 |
| 双向导航 | 通过两端的成员变量，互相可以访问 |
| 多重性 | 一个 Teacher 对应多个 Student（vector），一个 Student 对应一个 Teacher |

> ⚠️ 如果使用 `std::unique_ptr<Student>` 持有学生，那就变成了 [[Composition]]（组合）关系——这是与关联最容易混淆的地方。区分的关键就在于：**谁负责管理生命周期**。

## 与组合的本质区别

最本质的区别是 **生命周期所有权**：

- **组合**：整体"拥有"部分，部分随整体而生、随整体而灭
- **关联**：只是"知道"对方，对方独立存活

| 维度 | 关联（Association） | 组合（Composition） |
| --- | --- | --- |
| 生命周期 | 双方独立 | 部分依赖整体，同生共死 |
| 所有权 | 无所有权 | 整体独占拥有部分 |
| 耦合强度 | 弱 | 最强 |
| 共享性 | 可被多个对象关联 | 一个部分只属于一个整体 |
| C++ 实现 | 裸指针 / 引用 / `weak_ptr` | 值成员 / `unique_ptr` |
| UML 符号 | 普通直线 | 实心菱形（指向整体侧） |
| 典型例子 | 司机—汽车、学生—老师 | 汽车—引擎、人—心脏 |

## 聚合：关联的子类型

实际上还有一种介于关联和组合之间的关系叫 **聚合（Aggregation）**：球队解散后球员仍然存在，但语义上球员是球队的"组成部分"。在 C++ 实现上，聚合与关联几乎一样（都是非拥有指针），区别只在语义层面。

## 何时选择关联（成员）

| 场景 | 推荐 | 理由 |
| --- | --- | --- |
| 几乎每个方法都要用 | 成员（关联） | 避免重复传参 |
| 跨方法保持状态/身份 | 成员（关联） | 它属于对象的"自我"一部分 |
| 整个对象生命周期内引用同一个 | 成员（关联） | 体现长期协作 |

## 关联连接

- [[Object_Relationships]] — 总览
- [[Composition]] — 组合关系（对比）
- [[Dependency]] — 依赖关系（对比）
- [[Coupling]] — 关联是中等耦合
- [[Dependency_Injection]] — 通常通过构造函数将依赖注入为关联
- [[摘要-software-design-object-relationships]] — 来源摘要
