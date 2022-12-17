---
layout: default
parent: 站点结构
has_children: true
nav_order: 2
title: Liquid
---

Jekyll 使用 [Liquid](https://shopify.github.io/liquid/) 模板语言处理模板。

通常在 Liquid 中输出内容使用双层花括号，例如
{% raw %}`{{ variable }}`{% endraw %} ；执行逻辑声明通过花括号加百分号包裹，例如
{% raw %}`{% if statement %}`{% endraw %}。要学习更多 Liquid 知识，查阅[官方 Liquid 文档](https://shopify.github.io/liquid/)。

Jekyll 提供了一些用用的 Liquid 扩展来帮助您构建站点：

* [Filter]({{ '/docs/liquid/filters/' | relative_url }})
* [Tag]({{ '/docs/liquid/tags/' | relative_url }})
