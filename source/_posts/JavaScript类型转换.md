---
title: JavaScript类型转换
excerpt: 介绍JS类型转换机制
toc: true
tag: 'JavaScript'
categories:
- 前端
---

## 一、前言

JS有七种简单数据类型：`undefined`、`null`、`boolean`、`string`、`number`、`symbol`、`bigint`，以及引用类型 `object`

但由于JavaScript是弱类型语言，所以只有在运行期间才会确定当前类型

```javascript
const x = y ? 1 : a;
```

上面代码中，`x`的值在编译阶段是无法获取的，只有等到程序运行时才能知道

虽然变量的数据类型是不确定的，但是各种运算符对于数据类型是有要求的，如果运算符的类型与预期不符合，就会触发类型转换机制

常见的类型转换有：

- 强制转换(显示转换)
- 自动转换(隐式转换)