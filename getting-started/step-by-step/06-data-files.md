---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 6
title: 数据文件
permalink: /getting-started/step-by-step/06-data-files/
---
Jekyll 支持从 `_data` 目录加载 YAML、JSON 和 CSV 格式文件数据。数据文件是从与源码中分离内容使网站容易维护的一种很好的方式。

在这一步中我们将在数据文件中存储导航内容，然后在导航包含中通过循环数据来使用它。

## 数据文件用法

[YAML](http://yaml.org/) 是 Ruby 生态系统中常见的的一种格式。您将用它存储导航项目（每项有一个名字和一个链接）数列。

在 `_data/navigation.yml` 用下面内容创建导航数据文件：

```yaml
- name: Home
  link: /
- name: About
  link: /about.html
```

Jekyll 通过 `site.data.navigation` 使用此导航数据文件。不同于 `_includes/navigation.html` 的输出每个导航项目，现在您可以利用数据文件进行循环使用数据：

{% raw %}
```liquid
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}style="color: red;"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}
</nav>
```
{% endraw %}

输出是一样的。这么做的不同之处就是您可以更容易地添加导航项目和修改 HTML 结构了。

一个好的网站怎么能少的了 CSS、JS 和图像？接下来让我们看看 Jekyll 如何处理网站所需的资源。
