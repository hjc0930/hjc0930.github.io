---
title: 使用mathjs进行高精度运算
excerpt: 可以使用mathjs来实现JavaScript的精度计算
toc: true
tag: JavaScript
categories:
- 前端
- JavaScript
---

## 前言

[mathjs](https://github.com/josdejong/mathjs)是用于JavaScript和NodeJS的数学库。它内置大量函数与常量，并提供集成解决方案来处理不同的数据类型，如数字，大数字，复数，分数，单位和矩阵等

## 使用

- 安装

```bash
npm i mathjs
```

### 基本使用

`format`用于格式化输出，其中`precision`参数用于指定格式化精度的位数

```javascript
import { create, all } from "mathjs";

// 创建mathjs实例
const mathjs = create(all, {
  number: "BigNumber",
  precision: 20,
});

// add
const add = (num1, num2) => +mathjs.format(mathjs.add(1, 2), {
  precision: 16,
})

// subtract
const subtract = (num1, num2) => +mathjs.format(mathjs.subtract(1, 2), {
  precision: 16,
})

// multiply
const multiply = (num1, num2) => +mathjs.format(mathjs.multiply(1, 2), {
  precision: 16,
})

// divide
const multiply = (num1, num2) => +mathjs.format(mathjs.divide(1, 2), {
  precision: 16,
})
```

### 链式计算

支持输入一个初始值进行链式计算

```javascript
import { create, all } from "mathjs";

const mathjs = create(all, {
  number: "BigNumber",
  precision: 20,
});

// 111
console.log(mathjs.format(mathjs.chain(1.11).multiply(100).done(), {precision: 16}));
```
### 配置

`mathjs`支持配置来创建实例

```javascript
import {} from 'mathjs';

const maht = create(all, {
  epsilon: 1e-12,
  matrix: 'Matrix',
  number: 'number',
  precision: 64,
  predictable: false,
  randomSeed: null
})
```

支持的配置有

- `epsilon`，用于测试两个比较值之间是否相等的最小相对差异。所有关系功能都使用该值。默认值为 `1e-12`

- `matrix`，函数的矩阵输出的默认类型。可用值为：（ `'Matrix'`默认值）或`'Array'`。在可能的情况下，函数的矩阵输出类型取决于函数输入：将数组作为输入将返回数组，将矩阵作为输入将返回矩阵。如果没有矩阵作为输入，则输出类型由option决定`matrix`。对于混合矩阵输入，将始终返回矩阵。

- `number`，指定实例的输入输出类型，默认值为`number`，可选值为：`number | BigNumber`

- `precision`，BigNumbers的最大有效位数。此设置仅适用于BigNumbers，不适用于数字。默认值为 `64`。

- `predictable`，功能的可预测输出类型。如果为true，则输出类型仅取决于输入类型。如果为false（默认），则输出类型可以根据输入值而变化。例如，当predictable为false时 `math.sqrt(-4)` 返回 `complex('2i')`，为true `NaN`时返回。以编程方式处理计算结果时，可能需要可预测的输出，但对于评估动态方程式的用户可能不方便。

- `randomSeed`，将此选项设置为种子伪随机数生成，使其具有确定性。每次设置此选项时，都会使用提供的种子重置伪随机数生成器。例如，将其设置为每次设置该选项`'a'` 后将导致在第一次呼叫时 `math.random()` 返回 `0.43449421599986604`。设置为 `null` 使用随机种子为伪随机数生成器提供种子。默认值为 `null`。