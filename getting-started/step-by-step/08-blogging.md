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

There's currently no way to navigate to the blog post. Typically a blog has a
page which lists all the posts, let's do that next.

Jekyll makes posts available at `site.posts`.

Create `blog.html` in your root (`/blog.html`) with the following content:

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

There's a few things to note with this code:

* `post.url` is automatically set by Jekyll to the output path of the post
* `post.title` is pulled from the post filename and can be overridden by
setting `title` in front matter
* `post.excerpt` is the first paragraph of content by default

You also need a way to navigate to this page through the main navigation. Open
`_data/navigation.yml` and add an entry for the blog page:

```yaml
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
```

## More posts

A blog isn't very exciting with a single post. Add a few more:

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

Open <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>
and have a look through your blog posts.

Next we'll focus on creating a page for each post author.
