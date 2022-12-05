---
title: Grid布局
excerpt: Grid布局则是将容器划分成"行"和"列"，产生单元格，然后指定**项目**所在的单元格，可以看作是二维布局，比Flex布局更强大
toc: true
tag: CSS
categories:
- 前端
- CSS
---

## 1.什么是Grid布局
**Flex**布局是轴线布局，只能指定"项目"针对轴线的位置，可以看作是**一维布局**，**Grid**布局则是将容器划分成"行"和"列"，产生单元格，然后指定**项目**所在的单元格，可以看作是**二维布局**，Grid布局远比Flex布局强大
![](/images/grid1.png)
### 常用的三种布局

- 传统布局：利用position+display+float属性布局，兼容性最好，但效率低
- FlexBox：一维布局方案，有自己的一套属性，效率高，学习成本低，兼容性强
- Grid布局：网格布局是最强大的CSS布局方案，但是知识点较多，学习成本相对困难些，目前兼容性不如FlexBox
### 兼容性
![](/images/grid2.png)
## 2.基本概念

- 容器：有容器属性

![](/images/grid3.png)

- 项目：有项目属性

![](/images/grid4.png)
![](/images/grid5.png)

## 3.容器属性

- grid-template-columns
- grid-template-rows
- row-gap
- column-gap
- _gap(上面两个的简写)_
- grid-template-areas
- grid-auto-flow
- justify-items
- align-items
- _place-items(上面两个的简写)_
- justify-content
- align-content
- _place-content(上面两个的简写)_
- grid-auto-columns
- grid-auto-rows
### 3.1.grid-template-*
设置Grid布局的行列属性(几行，几列)
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Grid</title>
  <style>
    * {
      margin: 0;
      padding: 0;
    }

    .root {
      width: 600px;
      height: 600px;
      border: 1px solid cadetblue;
      display: grid;
      grid-template-columns: 100px 100px 100px;
      grid-template-rows: 100px 100px 100px 100px;
    }

    .item1 {
      background-color: red;
    }

    .item2 {
      background-color: gold;
    }

    .item3 {
      background-color: aqua;
    }

    .item4 {
      background-color: beige;
    }

    .item5 {
      background-color: blueviolet;
    }

    .item6 {
      background-color: brown;
    }

    .item7 {
      background-color: green;
    }

    .item8 {
      background-color: blanchedalmond;
    }

    .item9 {
      background-color: violet;
    }

    .item10 {
      background-color: thistle;
    }
  </style>
</head>

<body>
  <div class="root">
    <div class="item item1">1</div>
    <div class="item item2">2</div>
    <div class="item item3">3</div>
    <div class="item item4">4</div>
    <div class="item item5">5</div>
    <div class="item item6">6</div>
    <div class="item item7">7</div>
    <div class="item item8">8</div>
    <div class="item item9">9</div>
    <div class="item item10">10</div>
  </div>
</body>

</html>
```
#### repeat()：第一个参数是重复次数，第二个参数是需要重复的值
```css
grid-template-columns: repeat(3, 100px); // 重复三次，每个项目100px
grid-template-rows: repeat(4, 100px); // 重复四次，每个项目100px
```
#### auto-fill：有时候项目大小是固定的，但是容器大小不确定，这个属性就会自动填充
```css
grid-template-columns: repeat(auto-fill, 100px)
```
#### fr：为了方便表示比例关系，网格布局提供fr关键字(意为片段)
```css
grid-template-columns: repeat(4, 1fr) // 宽度被平均分成4份
```
#### minmax()：函数产生一个长度范围，表示长度就在这个范围之中，它接受两个参数，分别为最小值和最大值
```css
grid-template-columns: 1fr minmax(15px, 1fr)
```
#### auto：表示由浏览器自己决定宽度(自适应)
```css
grid-template-columns: 100px auto 100px; // 两端固定，中间自适应
```
#### 网格线：可以用方括号定义网格线名称，方便以后引用
```css
grid-template-columns: [c1]100px [c2]100px [c3]100px [c4]
```
### 3.2.*-gap
规定网格中行列之间的间距
> column-gap row-gap grid-gap(row-gap | column-gap)

```css
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  column-gap: 20px;
  row-gap: 20px;
  gap: 20px 10px;
```
### 3.3.grid-template-area
用来划分模板的区域
```css
grid-template-areas: "a b c" "d e f" "g h i" "j";
```
### 3.4.grid-auto-flow
规定容器中项目的排列顺序
![](/images/grid6.png)
如果出现如下图位置的情况，为了充分利用空间，可以加上dense属性
![](/images/grid7.png)
### 3.5.justify-items/align-items
设置**单元格内容**的水平和垂直的对齐方式
```css
justify-items: start | end | center | stretch;
align-items: start | end | center | stretch;
```
![](/images/grid9.png)
![](/images/grid10.png)
#### place-items
place-items属性是align-items属性和justify-items属性的合并简写
```css
place-items: <align-items> <justify-items>
```
### 3.6.justify-content/align-content
设置**整个内容**区域的水平和垂直对齐方式
```css
justify-content: start | end | center | stretch | space-around | space-between | space-evenly;
align-content: start | end | center | stretch | space-around | space-between | space-evenly;
```
#### place-content
place-contend属性是align-contend属性和justify-contend属性的合并简写
```css
place-content: <align-content> <justify-content>
```
### 3.7.grid-auto-columns/grid-auto-rows
 用来设置**多出来的项目**的宽和高
![](/images/grid11.png)
## 4.项目属性

- grid-column-start
- grid-column-end
- _grid-column(上面两个的简写)_
- grid-row-start
- grid-row-end
- _grid-row(上面两个的简写)_
- grid-area
- justify-self
- align-self
- _place-self(上面两个的简写)_
### 4.1.grid-column-start/grid-column-end/grid-row-start/grid-row-end
用来指定item在网格线中的开始网线和结束网线
![](/images/grid12.png)

-  简写
```css
grid-column: 1 / 3
grid-row: 1 / 3
```

- span写法

规定项目直接占据的行/列数量
![](/images/grid13.png)
```css
grid-column: span 3; // 跨越3列
grid-row: span 1; // 跨越1行
```
### 4.2.grid-area
指定项目放在哪一个区域

- 配合容器属性`grid-template-area`使用

![](/images/grid14.png)

- 用做上面四个属性的简写

grid-area属性可以用作grid-row-start，grid-column-start，grid-row-end，grid-column-end的合并简写形式，直接指定项目的位置
```css
/* grid-area: <row-start> / <column-start> / <row-end> / <column-end> */
grid-areaL 1 / 1 / 3 / 3;
```

![](/images/grid15.png)

### 4.3.justify-self/align-self
justify-self属性用来**单独设置**单元格内容的水平位置，跟justify-items属性的用法完全一致
align-self属性用来**单独设置**单元格内容的垂直位置，跟align-items属性的用法完全一致
#### place-self
place-self属性是align-self属性和justify-self属性的合并简写形式
```css
place-self: <align-self> <justify-self>
```
