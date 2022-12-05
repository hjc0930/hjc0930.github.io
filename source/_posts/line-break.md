---
title: line-break
excerpt: line-break
toc: true
tag: CSS
categories:
- 前端
- CSS
---

用于设置中日韩三种语言遇到标点符号时的换行规则
```css
.class {
  /* Keyword values */
  line-break: auto;  /* 使用默认的断行规则分解文本 */
  line-break: loose; /* 使用尽可能松散（least restrictive）的断行规则分解文本。一般用于短行的情况，如报纸 */
  line-break: normal; /* 使用最一般（common）的断行规则分解文本。 */
  line-break: strict; /* 使用最严格（stringent）的断行原则分解文本。 */
  line-break: anywhere; /* 在每个印刷字符单元（typographic character unit）的周围，都有一个自动换行（soft wrap）的机会，包括任何标点符号（punctuation character）或是保留的空白字符（preserved white spaces），或是单词之间。但忽略任何用于阻止换行的字符，即使是来自 GL、WJ 或 ZWJ 字符集的字符，或是由 word-break 属性强制的字符。不同的换行机会拥有相同的优先级。也不应用断字符（hyphenation，可能是 "-"）*/

  /* Global values */
  line-break: inherit;
  line-break: initial;
  line-break: unset;
}
```
