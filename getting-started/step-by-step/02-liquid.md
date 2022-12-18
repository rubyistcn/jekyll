---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 2
title: Liquid
permalink: /getting-started/step-by-step/02-liquid/
---

Liquid 使 Jekyll 开始变得有意思——它是有三种组件的模板语言：
  * [object](#object)
  * [tag](#tag) 
  * [filter](#filter)

## Object

Object 告诉 Liquid 将预定义[变量](../../site-structure/variables/)做为内容输出到页面。使用双层花括号引用 object：{% raw %}`{{`{% endraw %} 和 {% raw %}`}}`{% endraw %}。

例如：{% raw %}`{{ page.title }}`{% endraw %} 显示 `page.title` 变量。

## Tag

Tag 为模板定义逻辑和控制流。用花括号和百分号封装 Tag：{% raw %}`{%`{% endraw %} 和
{% raw %}`%}`{% endraw %}。

例如：

{% raw %}
```liquid
{% if page.show_sidebar %}
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}
```
{% endraw %}

如果页面变量 `show_sidebar` 的值是 `true` 将显示 `sidebar` 内容。 

学习更多 Tag 知识参阅 Jekyll 文档的[这里](/site-structure/liquid/tags/)。

## Filter

Filter 改变 Liquid Object 的输出。它们常用于被 `|` 隔开的输出。 

例如：

{% raw %}
```liquid
{{ "hi" | capitalize }}
```
{% endraw %}

这将显示 `Hi`，而不是 `hi`。

[学习更多 Filter](/site-structure/liquid/filters/) 知识。

## 使用 Liquid

现在，用 Liquid 让您的 `Hello World!` 文本从[设置](../01-setup/)中的大写变为小写：

{% raw %}
```liquid
...
<h1>{{ "Hello World!" | downcase }}</h1>
...
```
{% endraw %}

要让 Jekyll 处理您的修改，添加 [front matter](../03-front-matter/) 到页面顶端：

```yaml
---
# front matter 告诉 Jekyll 处理 Liquid
---
```

您的 HTML 文档看起来应当是：

{% raw %}
```html
---
---

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
```
{% endraw %}

当您刷新浏览器时会看到 `hello world!`。

Jekyll 的强大来自组合 Liquid 和其它功能。给页面添加了 frontmatter，就会使 Jekyll 处理页面内的 Liquid。

接下来，您会学习更多 frontmatter 知识。
