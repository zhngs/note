---
title: rust快速入门(2)——语句和表达式

date: 2022-5-30 17:00:00

updated: 2022-5-30 17:00:00

tags:

- rust语言

categories:

- [编程语言, rust, rust快速入门]

---

# 一.概念

Rust 是一门基于表达式（expression-based）的语言，**语句**（*Statements*）是执行一些操作但不返回值的指令，表达式（*Expressions*）计算并产生一个值，`可以简单地理解为，语句后需要加分号，表达式后不需要加分号`

```rust
fn main() {
    let x = 1; // 语句
    let y = { // 大括号本身是一个表达式
        let x = 3;
        x + 1 
    };
}
```

note：大括号本身是一个表达式，`x + 1`后没带分号，表示返回表达式的值，`如果没有显式指定返回值，则表达式默认返回单元值()`

# 二.表达式

## 1.if

if语句用法如下

```rust
fn main() {
    let number = 6;
    if number % 4 == 0 {
        println!("number is divisible by 4");
    } else if number % 3 == 0 {
        println!("number is divisible by 3");
    } else if number % 2 == 0 {
        println!("number is divisible by 2");
    } else {
        println!("number is not divisible by 4, 3, or 2");
    }
}
```

可以看到if语句可以作为表达式返回值

```rust
fn main() {
    let condition = true;
    let number = if condition { 
        5 
    } else { 
        6 
    };
    println!("The value of number is: {}", number);
}
```

## 2.loop

loop创建一个无限循环

```rust
fn main() {
    loop {
        println!("again!");
    }
}
```

可以从loop中返回值

```rust
fn main() {
    let mut counter = 0;
    let result = loop {
        counter += 1;
        if counter == 10 {
            break counter * 2;
        }
    };
    println!("The result is {}", result);
}
```

## 3.while

当条件为真，执行循环

```rust
fn main() {
    let mut number = 3;
    while number != 0 {
        println!("{}!", number);
        number -= 1;
    }
    println!("LIFTOFF!!!");
}
```

## 4.for

`for` 循环用来遍历集合，其安全性和简洁性使得它成为 Rust 中使用最多的循环结构

```rust
fn main() {
    let a = [10, 20, 30, 40, 50];
    for element in a {
        println!("the value is: {}", element);
    }
}
```


