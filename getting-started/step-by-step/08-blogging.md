---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 8
title: 博客
permalink: /getting-started/step-by-step/08-blogging/
---
您可能奇怪没有数据库怎么可能有博客功能。实际上，Jekyll 的博客只需文本文件。

## 帖子

博客帖子放在一个叫做 `_posts` 的文件夹中。帖子文件名有特定格式：发布日期，然后是标题，然后是扩展名。

创建您的第一篇帖子 `_posts/2018-08-20-bananas.md`，内容如下：

```markdown
---
layout: post
author: jill
---
A banana is an edible fruit – botanically a berry – produced by several kinds
of large herbaceous flowering plants in the genus Musa.

In some countries, bananas used for cooking may be called "plantains",
distinguishing them from dessert bananas. The fruit is variable in size, color,
and firmness, but is usually elongated and curved, with soft flesh rich in
starch covered with a rind, which may be green, yellow, red, purple, or brown
when ripe.
```

这同您前面创建的 `about.md` 除了它有一个作者和不同的版式之外没什么不同。`author` 是一个定制的变量，不是必需，也可以叫做其它名字如 `creator`。

## 版式

版式 `post` 不存在，所以您需要创建它——`_layouts/post.html`，内容如下：

{% raw %}
```liquid
---
layout: default
---
<h1>{{ page.title }}</h1>
<p>{{ page.date | date_to_string }} - {{ page.author }}</p>

{{ content }}
```
{% endraw %}

这是一个继承的版式示例。帖子版式输出默认版式封装的标题、日期、作者和内容主体。

注意 `date_to_string` Filter 的使用将输出一个更漂亮的日期格式。

## 帖子列表

目前还没有办法导航到博客帖子。一般来说一个博客会有一个列出所有帖子的页面，接下来我们就做这件事。

Jekyll 通过 `site.posts` 获取所有帖子。

在您的 `root` 目录创建 `blog.html`（`/blog.html`），内容如下：

{% raw %}
```liquid
---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      {{ post.excerpt }}
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

这段代码要注意的事情：

* `post.url` 是由 Jekyll 自动设置的帖子输出路径
* `post.title` 是从帖子的文件名自动拉取的，但是可以通过 Front Matter 中的 `title` 设置覆盖
* `post.excerpt` 默认使用内容的第一段

您可能还需要通过主导航导航到此页。打开 `_data/navigation.yml` 然后添加博客页面的导航项：

```yaml
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
```

## 更多帖子

一个博客不可能只有一篇帖子，所以要添加更多：

`_posts/2018-08-21-apples.md`:

```markdown
---
layout: post
author: jill
---
An apple is a sweet, edible fruit produced by an apple tree.

Apple trees are cultivated worldwide, and are the most widely grown species in
the genus Malus. The tree originated in Central Asia, where its wild ancestor,
Malus sieversii, is still found today. Apples have been grown for thousands of
years in Asia and Europe, and were brought to North America by European
colonists.
```

`_posts/2018-08-22-kiwifruit.md`:

```markdown
---
layout: post
author: ted
---
Kiwifruit (often abbreviated as kiwi), or Chinese gooseberry is the edible
berry of several species of woody vines in the genus Actinidia.

The most common cultivar group of kiwifruit is oval, about the size of a large
hen's egg (5–8 cm (2.0–3.1 in) in length and 4.5–5.5 cm (1.8–2.2 in) in
diameter). It has a fibrous, dull greenish-brown skin and bright green or
golden flesh with rows of tiny, black, edible seeds. The fruit has a soft
texture, with a sweet and unique flavor.
```

打开 <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>
查看您的博客帖子。

接下来我们将聚焦为每一个帖子的作者创建一个页面。
