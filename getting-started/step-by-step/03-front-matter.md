---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 3
title: Front Matter
permalink: /getting-started/step-by-step/03-front-matter/
---

Front matter 是一段 [YAML](http://yaml.org/) 格式的代码片段，通常放置于文件开始的两段三个短横线之间。

您可以使用 Front Matter 设置页面变量：

```yaml
---
my_number: 5
---
```

您可以通过 Liquid 使用 `page` 调用 Front Matter 中定义的变量。例如：输出上面定义的 `my_number` 变量值：

{% raw %}
```liquid
{{ page.my_number }}
```
{% endraw %}

## 使用 Front Matter

使用 Front Matter 修改站点 `<title>`：

{% raw %}
```liquid
---
title: Home
---
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
```
{% endraw %}

{: .note .info }
您**必须**在页面中包含 Front Matter，Jekyll 才能通过 Liquid Tag 处理它。

要使 Jekyll 处理页面，可以通过使用无定义变量的 Front Matter，如：

```yaml
---
---
```

接下来，您会学习更多关于版式以及为什么您的页面要用更多的源代码而不是 HTML。
