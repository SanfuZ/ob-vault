---
title: "Law of Demeter（迪米特法则）"
type: concept
tags: [软件设计, OOP, 设计原则, 解耦]
sources:
  - raw/01-articles/设计模式中的对象关系.md
last_updated: 2026-05-17
---

## 定义

**迪米特法则（Law of Demeter，简称 LoD）** 也称作"最少知识原则（Principle of Least Knowledge）"，其核心理念是：

> **一个对象只跟它的"邻居"说话，不要跟"邻居的邻居"打交道。**

## 经典示例

```cpp
// ❌ 不好：你只该认识 customer，不该穿透到 address 里去
customer.getAddress().getCity().getZipCode();

// ✅ 好：让 customer 自己暴露需要的接口
customer.getZipCode();
```

链式调用 `customer.getAddress().getCity().getZipCode()` 暴露了 `customer` 的内部结构：调用方不仅要知道 `customer`，还要知道 `Address` 类、`City` 类，违反了迪米特法则。

## 核心含义

一个方法 `M` 调用的对象应限于：

1. 方法 `M` 所在的对象本身（`this`）
2. 作为参数传入 `M` 的对象
3. `M` 内部创建的对象
4. `M` 所属对象的直接成员（"邻居"）

**不应**调用：邻居的成员、邻居的邻居（孙子级别的访问）。

## 与 [[Coupling|耦合]] 的关系

迪米特法则是降低耦合的关键手段。穿透多层访问会导致：

- **结构暴露**：调用方知道太多内部结构
- **修改成本高**：中间任何一层结构变化都会影响调用方
- **可测试性差**：需要 mock 整条链上的所有对象

## 实践技巧

### 暴露所需的接口而非内部对象

让"邻居"自己提供所需的服务，而不是把内部对象拿出来让调用方自己操作：

```cpp
// ❌ 暴露内部
class Customer {
public:
    Address* getAddress() { return &address; }  // 把内部对象暴露
};

// ✅ 提供服务接口
class Customer {
public:
    std::string getZipCode() { return address.getCity().getZipCode(); }
};
```

### 使用 Tell, Don't Ask 风格

不要"询问"对方的状态再做决定，而是"告诉"对方做什么：

```cpp
// ❌ Ask
if (account.getBalance() > 100) account.setBalance(account.getBalance() - 100);

// ✅ Tell
account.withdraw(100);
```

## 何时打破规则

迪米特法则不是绝对的。对于：
- 数据传输对象（DTO）
- 流式 API / 构建器模式
- 不可变的值对象

链式调用是常见且合理的模式。

## 关联连接

- [[Object_Relationships]] — 总览
- [[Coupling]] — 耦合
- [[Association]] — 关联关系
- [[摘要-software-design-object-relationships]] — 来源摘要
