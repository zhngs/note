---
title: rust注解(4)——函数

date: 2022-6-1 15:00:00

updated: 2022-6-1 15:00:00

tags:

- 编程语言
- rust语言

categories:

- rust注解

---

# 一.函数定义

rust函数使用关键字`fn`来定义，函数名风格使用snake case，所有字母都是小写并使用下划线分隔单词

```rust
fn main() {
    let x = plus_one(5);
    println!("The value of x is: {}", x);
}

fn plus_one(x: i32) -> i32 {
    x + 1
}
```

函数名后跟形参列表，如果有返回值的话，可以在箭头后声明类型，`函数的返回值等同于函数体最后一个表达式的值，如果不写返回值的话，默认返回单元类型()`

# 二.闭包
