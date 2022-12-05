---
title: pointer-events
excerpt: 用于禁用指定元素的事件流
toc: true
tag: CSS
categories:
- 前端
- CSS
---

**pointer-events** CSS 属性指定在什么情况下 (如果有) 某个特定的图形元素可以成为鼠标事件的**target**;
**pointer-events 属性值**

- auto | none | inherit => HTML
- visiblePainted | visibleFill | visibleStroke | visible | painted | fill | stroke | all => SVG

**针对HTML元素**

- none：该元素永远不会成为鼠标事件的 target。但是，当其后代元素的 pointer-events 属性指定其他值时，鼠标事件可以指向后代元素，在这种情况下，鼠标事件将在捕获或冒泡阶段触发父元素的事件侦听器 (鼠标的动作将不能被该元素及其子元素所捕获，但是能够被其父元素所捕获)。
- auto：默认值，表示指针事件已启用；此时元素会响应指针事件，阻止这些事件在其下面的元素上触发。对于 SVG 内容，该值与 visiblePainted 效果相同。
- inherit：将使用 pointer-events 元素的父级的值。

**注意：使用pointer-events来阻止元素成为鼠标事件目标不一定意味着元素上的事件侦听器永远不会触发。如果元素后代明确指定了pointer-events属性并允许其成为鼠标事件的目标。**
