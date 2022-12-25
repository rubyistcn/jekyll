---
layout: default
parent: 配置
grand_parent: 构建
nav_order: 3
title: Front Matter 默认值
permalink: /build/configuration/front-matter-defaults/
---

使用 [Front Matter](/content/front-matter/) 是您可以指定您站点的页面和帖子的配置参数的方式之一。像指定默认版式、定制标题、指定更精准的帖子日期时间等都可以添加到您的页面或者帖子的 Front Matter。

很多时候，您会发现很多选项您在不断的重复——为每个文件设置同样的版式，为每个帖子添加通用的分类 等等。甚至您可能添加的个性化变量，如作者名字，在您的博客中也是帖子中没什么变化的重复。

去除每次创建新帖子或者页面时的重复操作，Jekyll 提供了一种在站点配置中设置默认值的处理方式。要使用这种方式，您可以指定站点级默认值——在您站点根目录的 `_config.yml` 文件中设定 `defaults` 值。

`defaults` 值是一个定义对应路径和选项以及该路径文件类型的 scope/values 对。

让我们假设您想为您站点的所有页面和帖子添加一个默认版式。您可以这样修改 `_config.yml`：

```yaml
defaults:
  -
    scope:
      path: "" # 一个空的字符串表示项目内所有文件
    values:
      layout: "default"
```

<div class="note info">
  <h5>停止和重启 <code>jekyll serve</code> 命令。</h5>
  <p>
    <code>_config.yml</code> 主配置文件包含全局配置和执行时被一次性读取的变量定义。一点修改了 <code>_config.yml</code> 并不会自动读取，必须下次启动执行时才能加载。
  </p>
  <p>
    注意当自动重构时<a href="{{ '/content/datafiles/' | relative_url }}">数据文件</a>也被自动导入和重载。
  </p>
</div>

这里，我们映射 `values` 到所有 `scope` 范围内的文件。由于路径设置为空字符串，所以会映射到项目的**所有文件**。您可能不想为项目的每个文件设置同一个版式——例如同样的 CSS 文件——所以您可以在 `scope` 内指定一个 `type` 值。

```yaml
defaults:
  -
    scope:
      path: "" # 空字符串表示项目内所有文件
      type: "posts" # 以前使用 `post` 是在 Jekyll 2.2 里
    values:
      layout: "default"
```

现在，只设置 `posts` 的版式了。类型有 `pages`、`posts`、`drafts` 或者任何站点内的专题。`type` 是可选项，当创建 `scope/values` 对时必须制定 `path` 值。

如同前面所说，`defaults` 可设置多组 scope/values 对。

```yaml
defaults:
  -
    scope:
      path: ""
      type: "pages"
    values:
      layout: "my-site"
  -
    scope:
      path: "projects"
      type: "pages" # previously `page` in Jekyll 2.2.
    values:
      layout: "project" # overrides previous default layout
      author: "Mr. Hyde"
```

根据这些默认值，所有页面使用 `my-site` 版式，所有 `projects/` 文件夹的 HTML 文件使用 `project` 版式（如果存在）。这些文件的 `page.author`
[liquid 变量]({{ '/site-structure/variables/' | relative_url }}) 设置为 `Mr. Hyde`。

```yaml
collections:
  my_collection:
    output: true

defaults:
  -
    scope:
      path: ""
      type: "my_collection" # a collection in your site, in plural form
    values:
      layout: "default"
```

此例中，名字为 `my_collection` 的[专题]({{ '/content/collections/' | relative_url }})的 `layout` 设置为 `default`。

### Glob 模式在 Front Matter defaults 中使用

It is also possible to use glob patterns (currently limited to patterns that contain `*`) when matching defaults. For example, it is possible to set specific layout for each `special-page.html` in any subfolder of `section` folder. {%- include docs_version_badge.html version="3.7.0" -%}

```yaml
collections:
  my_collection:
    output: true

defaults:
  -
    scope:
      path: "section/*/special-page.html"
    values:
      layout: "specific-layout"
```

<div class="note warning">
  <h5>Globbing and Performance</h5>
  <p>
    Please note that globbing a path is known to have a negative effect on
    performance and is currently not optimized, especially on Windows.
    Globbing a path will increase your build times in proportion to the size
    of the associated collection directory.
  </p>
</div>

### Precedence

Jekyll will apply all of the configuration settings you specify in the `defaults` section of your `_config.yml` file. You can choose to override settings from other scope/values pair by specifying a more specific path for the scope.

You can see that in the second to last example above. First, we set the default page layout to `my-site`. Then, using a more specific path, we set the default layout for pages in the `projects/` path to `project`. This can be done with any value that you would set in the page or post front matter.

Finally, if you set defaults in the site configuration by adding a `defaults` section to your `_config.yml` file, you can override those settings in a post or page file. All you need to do is specify the settings in the post or page front matter. For example:

```yaml
# In _config.yml
...
defaults:
  -
    scope:
      path: "projects"
      type: "pages"
    values:
      layout: "project"
      author: "Mr. Hyde"
      category: "project"
...
```

```yaml
# In projects/foo_project.md
---
author: "John Smith"
layout: "foobar"
---
The post text goes here...
```

The `projects/foo_project.md` would have the `layout` set to `foobar` instead
of `project` and the `author` set to `John Smith` instead of `Mr. Hyde` when
the site is built.
