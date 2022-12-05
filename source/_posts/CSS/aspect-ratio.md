---
title: aspect-ratio
excerpt: CSS用来定义容器的宽高比
toc: true
tag: CSS
categories:
- 前端
- CSS
---

- 用来定义容器的宽高比

示例
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
  <style>
    .box {
      width: 200px;
      background-color: aqua;
      height: auto;
      aspect-ratio: 1/2;
    }
  </style>
</head>

<body>
  <div class="box"></div>
</body>

</html>
```
