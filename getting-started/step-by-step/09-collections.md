---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 9
title: 专题
permalink: /getting-started/step-by-step/09-collections/
---
让我们看看如何充实作者信息，让每个作者都有自己的简介和他们发表的帖子。

要做到这些您需要使用专题。专题类似于帖子列表但内容不是以日期分类的。

## 配置

建立专题，您需要告知 Jekyll。Jekyll 在 `_config.yml`（默认）中配置。

在 `root` 目录创建 `_config.yml`，内容如下：

```yaml
collections:
  authors:
```

要（重新）加载配置，需要重启 Jekyll 服务器。在终端中点击 `Ctrl`+`C` 停止服务器，然后 `jekyll serve` 重启。

## 添加作者

文档（专题内的条目）聚在站点 `root` 目录下一个叫做  `_*collection_name*` 的目录内。本例中就是 `_authors`。

为每个作者创建一个文档：

`_authors/jill.md`:

```markdown
---
short_name: jill
name: Jill Smith
position: Chief Editor
---
Jill is an avid fruit grower based in the south of France.
```

`_authors/ted.md`:

```markdown
---
short_name: ted
name: Ted Doe
position: Writer
---
Ted has been eating fruit since he was baby.
```

## Staff（作者们）页面

让我们添加一个站点所有作者的列表页面。Jekyll 通过 `site.authors` 获得专题数据。

创建 `staff.html`，然后通过 `site.authors` 循环输出所有作者：

{% raw %}
```liquid
---
layout: default
title: Staff
---
<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2>{{ author.name }}</h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

由于 `content` 格式是 Markdown，您需要通过 `markdownify` Filter 输出。输出时使用
{% raw %}`{{ content }}`{% endraw %} 就会自动将其嵌入版式。

您还需要通过主导航导航到这个页面。打开
`_data/navigation.yml`，为 Staff 页面添加一个入口：

```yaml
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
- name: Staff
  link: /staff.html
```

## 输出一个页面

默认情况下，专题不会为文档输出一个页面。本例中我们想要为每个作者给出一个专属页面，所以需要修改一些专题配置。

打开 `_config.yml`，为作者专题配置添加 `output: true`：

```yaml
collections:
  authors:
    output: true
```

再次重启 Jekyll 服务器以使配置修改生效。

您可以用 `author.url` 链接到作者页面。

为 `staff.html` 页面添加链接：

{% raw %}
```liquid
---
layout: default
title: Staff
---
<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2><a href="{{ author.url }}">{{ author.name }}</a></h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>
```
{% endraw %}

就像帖子一样您需要为作者创建一个版式。

创建 `_layouts/author.html`，内容如下：

{% raw %}
```liquid
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}
```
{% endraw %}

## 默认 Front Matter

现在您需要配置作者文档使用 `author` 版式。这可以如前面所做在 Front Matter 中完成，只是有些重复。

您真正想要的是所有帖子自动使用 `post` 版式，作者使用 `author` 版式，其它的使用 `default` 版式。

您可以通过使用 `_config.yml` 中的 [Front Matter 默认值](/build/configuration/front-matter-defaults/)实现。您需要设定默认值覆盖范围，然后默认的 Front Matter 就开始发挥作用了。

添加版式默认值到 `_config.yml`，

```yaml
collections:
  authors:
    output: true

defaults:
  - scope:
      path: ""
      type: "authors"
    values:
      layout: "author"
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
  - scope:
      path: ""
    values:
      layout: "default"
```

现在您可以从所有页面和帖子的 Front Matter 中移除版式设置了。记住：任何时候您修改了 `_config.yml`，都需要重启 Jekyll 才能看到修改后的效果。

## 列出作者的帖子

让我们在作者页列出该作者所有已发布的帖子。要做到这步您需要匹配作者的 `short_name` 同帖子的 `author`。这可以过滤出作者的帖子。

在 `_layouts/author.html` 中循环输出过滤完的作者的帖子：

{% raw %}
```liquid
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}

<h2>Posts</h2>
<ul>
  {% assign filtered_posts = site.posts | where: 'author', page.short_name %}
  {% for post in filtered_posts %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
```
{% endraw %}

## 链接到另一个页面

帖子需要知道作者，所以我们链接到作者页面。
这可以在 `_layouts/post.html` 中通过类似过滤技术实现：

{% raw %}
```liquid
---
layout: default
---
<h1>{{ page.title }}</h1>

<p>
  {{ page.date | date_to_string }}
  {% assign author = site.authors | where: 'short_name', page.author | first %}
  {% if author %}
    - <a href="{{ author.url }}">{{ author.name }}</a>
  {% endif %}
</p>

{{ content }}
```
{% endraw %}

打开i <a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>，查看 `staff` 页面和帖子的作者链接等是否正确。

接下来就是我们这个教程的最后一步，打磨润色我们的网站，为生产环境部署做准备。
