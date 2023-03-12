---
title: JavaScript中的数据类型
excerpt: 介绍了JavaScript中的八种数据类型，以及它们的存储方式的区别
toc: true
tag: JavaScript
categories:
- 前端
---

## 前言

在`JavaScript`中，数据类型可以分为两种：

- 基本类型
- 复杂类型

两种类型的区别是：存储位置不同

## 一、基本类型

基本类型主要为以下6种：

- Number
- String
- Boolean
- Symbol
- BigInt
- Null
- Undefined

### Number

数值最常见的整数类型格式为十进制,也可以设置八进制(零开头)和十六进制(0x开头)

```javascript
let intNum = 55;
let num1 = 070;
let hexNum1 = 0xA;
```

浮点类型则在数值汇总必须包含小数点，还可通过科学计数法表示

```javascript
let floatNum1 = 1.1;
let floatNum2 = 0.1;
let floatNum3 = .1; // 有效，但不推荐
let floatNum = 3.125e7; // 等于31250000
```

在数值类型中，存在一个特殊值`NaN`，意为“不是数值”，用于表示本来要返回数值的操作失败了（而不是抛出错误）

```javascript
console.log(0/0) // NaN
console.log(-0/+0) // NaN
```

### Undefined

`undefined`类型只有一个值，就是特殊值`undefined`。当使用`code`或`let`声明了变量但没有初始化时，就相当于给变量赋予了`undefined`值

```javascript
let message;
console.log(message === undefined);
```

包含`undefined`值的变量跟未定义变量是有区别的

```javascript
let message; // 这个变量被声明了，只是值为undefined

console.log(message);
console.log(age) // 没有声明这个变量，报错
```

### String

字符串可以使用双引号(")、单引号(')或反引号(`)标示

```javascript
let firstName = "John";
let lastName = "Jacob";
let lastName = `Jingleheimerschmidt`;
```

字符串是不可变的，意思是一旦创建，它们的值就不能变了

```javascript
let lang = "Java";
lang = lang + "Script" // 先创建再销毁
```

### Null

`Null`类型同样只有一个值，即特殊值`null`

逻辑上讲，null值表示一个空指针对象，这也是给`typeof`传一个`null`会返回`object`的原因

```javascript
let car = null;
console.log(typeof car) // object
```

`undefined`值是由`null`值派生而来

```javascript
console.log(null == undefined);
```
只要变量保存对象，而当时又没有那个对象可保存，就可以用 `null` 填充该变量

### Boolean

布尔类型有两个字面值：`true`和 `false`，通过 `Boolean` 可以将其它类型的数据转化为布尔值

规则如下：


| 数据类型  | 转为true   | 转为false |
| --------- | ---------- | --------- |
| String    | 非空字符串 | ""        |
| Number    | 非零数值   | 0、NaN    |
| Object    | 任意对象   | N/A       |
| null      | N/A        | null      |
| Undefined | N/A        | undeinfed |

### Symbol

Symbol(符号)是原始值，且符号实例是唯一、不可变的。符号的用途是确保对象属性使用唯一标识，不会发生属性冲突的危险

```javascript
let genericSymbol = Symbol();
let otherGenericSymbol = Symbol();
console.log(genericSymbol == otherGenericSymbol); // false

let fooSymbol = Symbol('foo');
let otherFooSymbol = Symbol('foo');
console.log(fooSymbol == otherFooSymbol); // false
```

## 二、引用类型

复杂类型统称为 `Object`，我们这里主要讲述下面三种：

- Object
- Array
- Function

### Object

创建`object`常用方式为对象字面量表示法，属性名可以是字符串或数值

```javascript
let person = {
  name: "Nicholas",
  age: 29,
  5: true
}
```

### Array

`JavaScript`数组是一组有序的数据，但跟其他语言不同的是，数组中每个槽位可以存储任意类型的数据，并且，数组也是动态大小的，会随着数据添加而自动增长

```javascript
let colors = ['red', 2, {age: 20}]
colors.push(2)
```

### Function

函数实际是对象，每个函数都是 `Function` 类型的实例，而 `Function` 也有属性和方法，跟其他引用类型一样

函数存在三种常见的表达方式：

- 函数声明

```javascript
function sum(num1, num2) {
  return num1 + num2;
}
```

- 函数表达式

```javascript
const sum = function(num1, num2) {
  return num1 + num2;
}
```

- 箭头函数

```javascript
const sum = (num1, num2) => {
  return num1 + num2;
}
```

### 其他引用类型

除了上述说的三种之外，还包括 `Date`、`RegExp`、`Map`、`Set`等......

## 三、存储区别

基本数据类型和引用数据类型存储在内存中的位置不同：

- 基本数据类型存储在栈中
- 引用类型的对象存储于堆中

当我们把变量赋值给另一个变量时，解析器首先要确认的就是这个值是基本类型还是引用类型

举个例子

### 基本类型

```javascript
let a = 10;
let b = a;
b = 20;
console.log(a); // 10值
```

`a`的值为一个基本类型，是存储在栈中，将 `a`的值赋给 `b`，虽然两个变量的值相等，但是两个变量保存了两个不同的内存地址

### 引用类型

```javascript
let obj1 = {};
let obj2 = obj1;

obj2.name = 'xxx';

console.log(obj1.name); // xxx
```

引用类型数据存放在堆中，每个堆内存对象都有对应的引用地址指向它，引用地址存放在栈中。

`obj1`是一个引用类型，在赋值操作过程中，实际是将堆内存对象在栈内存的引用地址复制了一份给了 `obj2`，实际上它们共同指向同一个堆内存对象，所以更改 `obj2`会对 `obj1` 产生影响

### 小结

- 声明变量时不同的内存地址分配：
  - 简单类型的值存放在栈内存中
  - 引用类型的值存放在堆内存中，栈内存中存放的是指向堆内存的地址
- 不同的类型数据导致赋值变量方式不同：
  - 简单类型赋值，是生成相同的值，两个对象对应不同的地址
  - 引用类型赋值，是将保存对象的内存地址赋值给另一个变量。也就是两个变量指向堆内存中同一个对象