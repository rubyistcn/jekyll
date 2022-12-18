---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 4
title: 版式
permalink: /getting-started/step-by-step/04-layouts/
---
Jekyll 编译页面时除了 HTML 外也支持 [Markdown](https://daringfireball.net/projects/markdown/syntax)。Markdown 对于内容结构简单（只是段落、标题和图像）的页面来说是一个好
的选择，而且它比 HTML 语法更简洁。 

在您的站点的 root 目录创建一个新的 Markdown 文件 `about.md`。

您可以复制 `index` 的内容，然后将其修改为 About 页面。然而，当您需要为您的站点添加定制
代码的时候这可能导致代码重复。

例如：为您的站点添加一个样式表——需要为每个页面的 `<head>` 添加个一个样式表的链接。如果站点有很多页面，这将会很浪费时间。

## 创建版式

版式（Layout）就是一个可为站点每个页面封装内容的模板。
它们一般存储在叫做 `_layouts` 的目录内。

在您的站点的 root 目录下创建 `_layouts` 目录，然后在其内创建一个叫做 `default.html` 的文件，其内容如下：

{% raw %}
```liquid
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {{ content }}
  </body>
</html>
```
{% endraw %}

这里的 HTML 同 `index.html` 相比除了没有  Front Matter 和页面内容被 `content`
变量取代外差不多。

`content` 是特殊变量——被调用时返回渲染页面内容。

## 使用版式

让 `index.html` 使用您的新版式，在 Front Matter 中设置 `layout` 变量。文件看起来这样：

{% raw %}
```liquid
---
layout: default
title: Home
---
<h1>{{ "Hello World!" | downcase }}</h1>
```
{% endraw %}

当您重新加载站点时，输出没有变化。

由于版式封装了页面内容，您可以在版式文件中调用 Front Matter 如 `page`。 当您在页面应用版式时，就如同在那页使用 Front Matter 一样。

## 构建 About 页面

添加下面代码到 `about.md`——让您的 About 页面使用新版式：

```markdown
---
layout: default
title: About
---
# About page

This page tells you a little bit about me.
```

在您的浏览器中打开查看您的新页面 <a href="http://localhost:4000/about.html" target="_blank" data-proofer-ignore>http://localhost:4000/about.html</a>。

恭喜，您现在有一个包含两个页面的网站了。

接下里，您将学习如何在您的网站里如何从一个页面导航另一个页面的知识了。
