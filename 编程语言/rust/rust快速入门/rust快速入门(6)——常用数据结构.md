---
title: rust快速入门(6)——常用数据结构

date: 2022-6-2 12:00:00

updated: 2022-6-2 12:00:00

tags:

- rust语言

categories:

- [编程语言, rust, rust快速入门]

---

# 一.Option

Rust 并没有空值，不过它拥有一个可以编码存在或不存在概念的枚举Option

```rust
enum Option<T> {
    None,
    Some(T),
}
```

只要一个值不是 `Option<T>` 类型，你就 **可以** 安全的认定它的值不为空。这是 Rust 的一个经过深思熟虑的设计决策，来限制空值的泛滥以增加 Rust 代码的安全性

# 
