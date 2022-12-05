---
title: min max clamp函数
excerpt: CSS新增的计算函数
toc: true
tag: CSS
categories:
- 前端
- CSS
---

## padding和父元素宽度的关系
子元素不设置宽高，它的`padding-bottom`的比例是以父元素的宽度为参照的，相当于可以使用子元素来撑开父元素，实现元素的宽高等比效果
```css
.parent {
  width: 600px
}

.parent > .child {
  padding: 0 0 50% 0; // 相当于父元素宽度的50%
}
```
## min()
min函数用来设置元素的最小返回值，例如`min(50%, 500px)`，浏览器会在50%和500px中取一个最小值，当视口宽度的50%大于500px时，取500px，否则就使用50%
```css
width: min(50%, 500px)
// 相当于
width: 50%
max-width: 500px;
```
## max()
max()函数用来设置元素的最大返回值，例如`max(50%, 600px)`，当视口宽度的50%大于600px时，取50%的值，否则取600px
```css
width: max(50%, 600px)
// 相当于
width: 50%
min-width: 600px
```
## clamp()
设置一个区间范围值，即最小值，首选值和最大值
```css
width: clamp(600px, 80%, 1200px)
```
