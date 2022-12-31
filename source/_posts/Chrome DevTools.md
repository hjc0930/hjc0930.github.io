---
title: Chrome DevTools简介
excerpt: 调试就是通过某种信道（比如 WebSocket）把运行时信息传递给开发工具，做 UI 的展示和交互，辅助开发者排查问题、了解代码运行状态等。
toc: true
tag: Chrome调试
categories:
- 前端
---

Chrome DevTools分为两部分，backend和frontend

- backend和Chrome集成，负责把Chrome的网页运行时状态通过调试协议暴露出来。
- frontend是独立的，负责对接调试协议，做UI的展示和交互

两者之间的调试协议叫做Chrome DevTools Protocol，简称CDP。
传输协议数据的方式叫做信道(message channel)，有很多种，比如Chrome DevTools嵌入在Chrome里时，两者通过全局的函数通信；当Chrome DevTools远程调试某个目标代码时，两者通过WebSocket通信。
frontend、backend、调试协议(CDP)、信道，这是Chrome DevTools的4个组成部分。

![](/images/chromeDevTools.png)

backend 可以是 Chromium，也可以是 Node.js 或者 V8，这些 JS 的运行时都支持 Chrome DevTools Protocol。
这就是 Chrome DevTools 的调试原理。
除了 Chrome DevTools 之外，VSCode Debugger 也是常用的调试工具

调试就是通过某种信道（比如 WebSocket）把运行时信息传递给开发工具，做 UI 的展示和交互，辅助开发者排查问题、了解代码运行状态等。
