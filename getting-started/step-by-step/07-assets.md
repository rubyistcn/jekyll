---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 7
title: 资源
permalink: /getting-started/step-by-step/07-assets/
---
在 Jekyll 中使用 CSS、JS 和图像以及其他资源直接使用即可。将它们放在您站点的文件夹内，在构建站点时就会直接拷贝过去。

Jekyll 站点通常使用这个结构组织资源：

```
.
├── assets
│   ├── css
│   ├── images
│   └── js
...
```
所以，在您的 `assets` 文件夹内创建 `css`，`images` 和 `js` 文件夹。
另外，在 `root` 文件夹直接创建 '_sass' 文件夹，稍后会用。

## Sass

`_includes/navigation.html`（添加和设置都在同一个文件）使用的行内嵌入样式并不是推荐的样式表使用方式。相反，我们要创建一个新的 CSS 文件，还要定义我们的第一个类来美化当前页面链接。

要做到这些，首先需要定义类（稍后我们会配置），然后在 `navigation.html` 文件中删除先前添加的代码（将当前页链接设为红色）然后插入下面代码：

{% raw %}
```liquid
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}class="current"{% endif %}>{{ item.name }}</a>
  {% endfor %}
</nav>
```
{% endraw %}

您可以使用一个标准 CSS 文件，我们将本步骤进行深化，使用 [Sass](https://sass-lang.com/) 文件。Sass 是 CSS 的很棒的一个扩展，Jekyll 支持 Sass。

首先创建 Sass 文件 `assets/css/styles.scss`，内容如下：

```sass
---
---
@import "main";
```

页面顶部的空 Front Matter 告诉 Jekyll 该文件需要处理。`@import "main"` 告诉 Sass 在 sass 目录（`_sass/`，该文件夹默认在您的站点 `root` 文件夹内已创建）找到叫做 `main.scss` 的文件。

这里您只有一个主 CSS 文件。对于大项目而言，这是一种组织 CSS 的很好的方式。

创建上面提到的当前类，使其颜色为绿色。创建 Sass 文件 `_sass/main.scss`，内容如下：

```sass
.current {
  color: green;
}
```

您还需要在您的版式中引用样式表。

打开 `_layouts/default.html` 然后添加样式表到 `<head>` 部分：

{% raw %}
```liquid
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="/assets/css/styles.css">
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>
```
{% endraw %}

这里引用的 `styles.css` 文件是由 Jekyll 从早期您在 `assets/css/` 中创建的 `styles.scss` 文件生成。

查看 <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>
，检查导航中的活跃电解是否为绿色。

接下来，我们看看 Jekyll 做流行的功能之一——博客功能。
