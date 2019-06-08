---
title: "HTML简介"
date: 2019-06-03T14:09:19+08:00
draft: true
Categories: ["html"]
Tags: ["html", "教程"]
---

### 实例
```html
<html>
<body>

<h1>我的第一个标题</h1>

<p>我的第一个段落。</p>

</body>
</html>
```

------

### 什么是HTML？
HTML 是用来描述网页的一种语言。

* HTML 指的是超文本标记语言 (Hyper Text Markup Language)
* HTML 不是一种编程语言，而是一种标记语言 (markup language)
* 标记语言是一套标记标签 (markup tag)
* HTML 使用标记标签来描述网页

------

### HTML 标签
HTML 标记标签通常被称为 HTML 标签 (HTML tag)。

* HTML 标签是由尖括号包围的关键词，比如 <html>
* HTML 标签通常是成对出现的，比如 <b> 和 </b>
* 标签对中的第一个标签是开始标签，第二个标签是结束标签
* 开始和结束标签也被称为开放标签和闭合标签

------

### HTML 文档 = 网页
* HTML 文档描述网页
* HTML 文档包含 HTML 标签和纯文本
* HTML 文档也被称为网页  

Web 浏览器的作用是读取 HTML 文档，并以网页的形式显示出它们。浏览器不会显示 HTML 标签，而是使用标签来解释页面的内容：
```html
<html>
<body>

<h1>我的第一个标题</h1>

<p>我的第一个段落。</p>

</body>
</html>
```
#### 例子解释
&lt;html> 与 &lt;/html> 之间的文本描述网页  
&lt;body> 与 &lt;/body> 之间的文本是可见的页面内容  
&lt;h1> 与 &lt;/h1> 之间的文本被显示为标题  
&lt;p> 与 &lt;/p> 之间的文本被显示为段落  