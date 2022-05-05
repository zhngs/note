---
title: go快速入门

data: 2022-5-5 10:59:20

updated: 2022-5-5 10:59:20

tags:

- go语言

categories:

- [编程语言, go]

---

# 语言基础

## 变量

### 变量声明

- 变量声明通用语句：`var name type = expression`，其中type和expression两者可以省略其中一个，但不可以都省略。
  
  - 如果省略type，则type会由expression推导出来
  
  - 如果省略expression，初始值对应该类型的零值，数字为0，布尔值为false，string为""，接口和引用类型（slice、指针、map、通道、函数）为nil

- 短变量声明语句：`name := expression`，name的类型由expression推导而来，需要注意整数会被自动推导成int，浮点数会被自动推导成float64，单个字符会被推导成int32
  
  ```go
  number := 6
  floatnumber := 3.5
  str := 'a'
  fmt.Printf("%T value: %v\n", number, number)    //int value: 6
  fmt.Printf("%T value: %v\n", floatnumber, floatnumber)    //float64 value: 3.5
  fmt.Printf("%T value: %v\n", str, str)    //int32 value: 97
  ```

- go语言可以同时声明多个变量
  
  ```go
  var i, j, k int
  var b, f, s = true, 2.3, "hello"
  m, n := 1, "hi"
  ```

### 变量赋值

- 使用=即可进行赋值，go也支持多重赋值
  
  ```go
  var i, j int
  i, j = 1, 2
  i, j = j, i //多重赋值，交换两个变量
  ```

## 常量

- 使用`const name type = expression`声明，其中type可以省略，若省略则会自动推断name的type

# 数据类型

## 基础类型

### 整型

- 8位：`int8`、`uint8`、`byte`，`byte`为uint8的同义词

- 16位：int16、uint16

- 32位：`int32`、`uint32`、`rune`，`rune`是int32的同义词，常用于指明一个值是unicode码点

- 64位：`int64`、`uint64`、

- 平台相关：`int`、`uint`，可能是32位和64位

- 大小不明确：`uintptr`，大小足以存放完整指针，该类型仅用于底层编程，如go程序和c程序库或操作系统的接口界面

### 浮点

- `float32`和`float64`

### 复数

- `complex64`和`complex128`，分别由float32和float64构成

### 布尔

- `true`和`false`

- note：bool值无法隐式转换成数值（0或1），数值也无法隐式转换成bool值

### 字符串

- `string`，该类型底层采用utf8编码

- 4个标准包对字符串操作非常重要：bytes、strings、strconv、unicode

## 聚合类型

> 组合各种简单类型得到更复杂的类型

### 数组

- 类型为`[n]T`，n为一个具体的数字，T为具体的数据类型

### 结构体

- 结构体类型需要自定义，如下所示，定义了一个类型为`Person`的结构体

```go
type Person struct {
    name string
    age int
}
```

## 引用类型

> 间接指向程序变量或状态

### 指针

- 类型为`*T`，T为具体的数据类型

- 指针的值是一个变量的地址

### slice

- 类型为`[]T`，T为具体的类型，和数组的区别在于slice没有指定具体的大小，因为其底层是一个动态数组

### map

- 类型为`map[k]v`，k和v分别是字典的键和值对应的数据类型，其中k必须可以使用==来进行比较

- map是一个拥有键值对元素的无序组合，底层是一个散列表

### 函数

- 类型为`func (parameter-list) (result-list)`

### 通道

- 双向通道类型为`chan T`，T为具体的类型

- 单向的只能发送的通道类型为`chan<- T`

- 单向的只能接收的通道类型为`<-chan T`

## 接口类型

> 接口是对其他类型行为的概括和抽象

- 接口类型需要自定义，如下面定义了标准库内广泛使用的类型为Reader的接口

```go
type Reader interface {
    Read(p []byte) (n int, err error)
}
```

## 定义新类型

- 使用`type name underlying-type`，可以定义一个名为name的新类型，它和underlying-type具有相同的底层类型
