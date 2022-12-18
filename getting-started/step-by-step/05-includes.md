---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 5
title: Includes
permalink: /getting-started/step-by-step/05-includes/
---
站点已经初具规模，但是我们却没有办法在页面之间导航跳转。接下来我们解决这个问题。

导航应该每个页面都有，所以我们应该将其放入版式之中。我们不会直接将其放入版式，正好我们利用这个机会学习一下关于 includes 的知识。

## Include Tag

`include` Tag 允许您将存储在 `_includes` 文件夹的文件内容导入。Includes 对于站点中重复出现的源码文件或者提高源码可读性很有用。

导航源码可能会很复杂，所以有时使用 include 方法很有用。

## Include 用法

用下面内容创建导航文件 `_includes/navigation.html`：

```
<nav>
  <a href="/">Home</a>
  <a href="/about.html">About</a>
</nav>
```

试着使用 `include` Tag 将其添加到 `_layouts/default.html`：

{% raw %}
```liquid
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>
```
{% endraw %}

在您的浏览器打开 <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>，试着在页面间转换。

## 高亮当前页面

让我们进一步做好——在导航中高亮当前页面。

`_includes/navigation.html` 需要知道它插入页面的 URL 以便可以添加样式。Jekyll 的[变量](/site-structure/variables/)中，就有一个 `page.url` 具有此功能。

使用 `page.url` 可以检查链接是否是当前页面，如果是可以将其变为红色：

{% raw %}
```liquid
<nav>
  <a href="/" {% if page.url == "/" %}style="color: red;"{% endif %}>
    Home
  </a>
  <a href="/about.html" {% if page.url == "/about.html" %}style="color: red;"{% endif %}>
    About
  </a>
</nav>
```
{% endraw %}

打开 <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>
看一看当前页面的链接是否为红色。

这里还有一些重复——如果您要添加一些新项目或者修改高亮颜色。接下来我们就解决这个问题。
