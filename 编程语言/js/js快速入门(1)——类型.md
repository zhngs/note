---
title: js快速入门(1)——类型

date: 2022-5-13 11:00:02

updated: 2022-5-13 11:00:02

tags:

- js

categories:

- [编程语言, js]

---

# 一.变量

## 1.let声明

let定义变量，作用域为块作用域，js为弱类型语言，定义变量时不需要带变量类型

```javascript
let name = "zs"
```

## 2.const声明

const用来定义常量，定义的时候必须初始化，不然报错

```javascript
const name = "zs"
```

## 3.最佳工程实践

- 不使用var，var也是声明变量的一个关键字，但是var的行为比较怪异，不推荐使用

- 优先使用const，let其次

# 二.数据类型

js的数据类型有6种基本类型，1种复杂数据类型

- 基本类型：Undefined、Null、Boolean、Number、String 和 Symbol

- 复杂类型：Object

## 1.Undefined

Undefined 类型只有一个值，就是特殊值 undefined，在声明变量但没有初始化的时候会出现undefined

```javascript
let name;
console.log(name); // "undefined"
```

## 2.Null

Null类型只有一个值，即特殊值null，逻辑上讲，null值表示一个空对象指针

```javascript
let car = null; 
console.log(typeof car); // "object"
```

## 3.Boolean

有两个字面值：true 和 false，可以使用Boolean()转型函数将其他类型转换成布尔类型，转换规则如下

| 数据类型      | 转换为true     | 转换为false  |
| --------- | ----------- | --------- |
| String    | 非空字符串       | ""（空字符串）  |
| Number    | 非零数值（包括无穷值） | 0、NaN     |
| Object    | 任意对象        | null      |
| Undefined | N/A（不存在）    | undefined |

## 4.Number

Number类型使用 IEEE 754 格式表示整数和浮点值值（在某些语言中也叫双精度值），有两种类型的特殊值，Infinity和NaN，Infinity表示无限大，NaN表示不是数值

```javascript
console.log(0/0); // NaN 
console.log(-0/+0); // NaN
console.log(5/0); // Infinity 
console.log(5/-0); // -Infinity
```

## 5.String

String（字符串）数据类型表示零或多个 16 位 Unicode 字符序列。字符串可以使用双引号，单引号，反引号来表示

```javascript
let firstName = "John"; 
let lastName = 'Jacob'; 
let lastName = `Jingleheimerschmidt`;
```

## 6.Symbol

符号是原始值，且符号实例是唯一、不可变的。符号的用途是确保对象属性使用唯一标符，不会发生属性冲突的危险

## 7.Object

对象其实就是一组数据和功能的集合，Object 是所有对象的基类，Object 的实例本身并不是很有用，但理解与它相关的概念非常重要，Object 类型的所有属性和方法在派生的对象上同样存在。创建对象有三种方式：

- 早期使用Object创建
  
  ```javascript
  let person = new Object(); 
  person.name = "Nicholas"; 
  person.age = 29; 
  person.job = "Software Engineer"; 
  person.sayName = function() { 
   console.log(this.name); 
  };
  ```

- 后面函数字面量成了更流行的方式
  
  ```javascript
  let person = { 
   name: "Nicholas", 
   age: 29, 
   job: "Software Engineer", 
   sayName() { 
   console.log(this.name); 
   } 
  };
  ```

- 构造函数模式来创建，使用这种模式需要new操作符，这种模式会执行以下操作
  
  (1) 在内存中创建一个新对象
  
  (2) 这个新对象内部的[[Prototype]]特性被赋值为构造函数的 prototype 属性
  
  (3) 构造函数内部的 this 被赋值为这个新对象（即 this 指向新对象）
  
  (4) 执行构造函数内部的代码（给新对象添加属性）
  
  (5) 如果构造函数返回非空对象，则返回该对象；否则，返回刚创建的新对象
  
  ```javascript
  function Person(name, age, job){ 
   this.name = name; 
   this.age = age; 
   this.job = job; 
   this.sayName = function() { 
   console.log(this.name); 
   }; 
  } 
  let person1 = new Person("Nicholas", 29, "Software Engineer"); 
  let person2 = new Person("Greg", 27, "Doctor"); 
  person1.sayName(); // Nicholas 
  person2.sayName(); // Greg
  ```


