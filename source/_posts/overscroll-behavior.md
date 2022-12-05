---
title: min max clamp函数
excerpt: overscroll-behavior CSS 属性是 overscroll-behavior-x 和overscroll-behavior-y 属性的合并写法，让你可以控制浏览器过度滚动时的表现——也就是滚动到边界
toc: true
tag: CSS
categories:
- 前端
- CSS
---

**overscroll-behavior** CSS 属性是 [overscroll-behavior-x](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overscroll-behavior-x) 和 [overscroll-behavior-y](https://developer.mozilla.org/zh-CN/docs/Web/CSS/overscroll-behavior-y) 属性的合并写法，让你可以控制浏览器过度滚动时的表现——也就是滚动到边界。
```css
/* 关键字的值 */
overscroll-behavior: auto; /* 默认 */
overscroll-behavior: contain;
overscroll-behavior: none;

/* 使用 2 个值 */
overscroll-behavior: auto contain;

/* Global values */
overflow: inherit;
overflow: initial;
overflow: unset;
```
