---
layout: default
parent: Liquid
grand_parent: 站点结构
nav_order: 1
title: Liquid 的 Filter
permalink: "/docs/liquid/filters/"
shopify_filter_url: https://shopify.github.io/liquid/filters/
shopify_filters:
- abs
- append
- at_least
- at_most
- capitalize
- ceil
- compact
- concat
- date
- default
- divided_by
- downcase
- escape
- escape_once
- first
- floor
- join
- last
- lstrip
- map
- minus
- modulo
- newline_to_br
- plus
- prepend
- remove
- remove_first
- replace
- replace_first
- reverse
- round
- rstrip
- size
- slice
- sort
- sort_natural
- split
- strip
- strip_html
- strip_newlines
- times
- truncate
- truncatewords
- uniq
- upcase
- url_decode
- url_encode
---

支持所有标准的 Liquid [Filter](#standard-liquid-filters)（见后面）。

为更容易完成常见任务，Jekyll 甚至添加了一些自己的方便的 Filter，本页稍后您会看到。您
也可以利用[插件](/docs/plugins/)创建自己的 Filter。

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>简介</th>
      <th><span class="filter">Filter</span> 和 <span class="output">输出</span></th>
    </tr>
  </thead>
  <tbody>
    {% for filter in site.data.jekyll_filters %}
      <tr>
        <td>
          <p id="{{ filter.name | slugify }}" class="name"><strong>{{ filter.name }}</strong></p>
          <p>
            {{- filter.description -}}
            {%- if filter.version_badge %}
              <span class="version-badge" title="This filter is available from version {{ filter.version_badge }}">
                {{- filter.version_badge -}}
              </span>
            {% endif -%}
          </p>
        </td>
        <td class="align-center">
          {%- for example in filter.examples %}
            <p><code class="filter">{{ example.input }}</code></p>
            {% if example.output %}<p><code class="output">{{ example.output }}</code></p>{% endif %}
          {% endfor -%}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
</div>

### `slugify` filter 的参数

The `slugify` filter accepts an option, each specifying what to filter.
The default is `default`. They are as follows (with what they filter):

- `none`: no characters
- `raw`: spaces
- `default`: spaces and non-alphanumeric characters
- `pretty`: spaces and non-alphanumeric characters except for `._~!$&'()+,;=@`
- `ascii`: spaces, non-alphanumeric, and non-ASCII characters
- `latin`: like `default`, except Latin characters are first transliterated (e.g. `àèïòü` to `aeiou`) {%- include docs_version_badge.html version="3.7.0" -%}.

### Detecting `nil` values with `where` filter {%- include docs_version_badge.html version="4.0" -%}

You can use the `where` filter to detect documents and pages with properties that are `nil` or `""`. For example,

{% raw %}
```liquid
// Using `nil` to select posts that either do not have `my_prop`
// defined or `my_prop` has been set to `nil` explicitly.
{% assign filtered_posts = site.posts | where: 'my_prop', nil %}
```
{% endraw %}

{% raw %}
```liquid
// Using Liquid's special literal `empty` or `blank` to select
// posts that have `my_prop` set to an empty value.
{% assign filtered_posts = site.posts | where: 'my_prop', empty %}
```
{% endraw %}

### Binary operators in `where_exp` filter {%- include docs_version_badge.html version="4.0" -%}

You can use Liquid binary operators `or` and `and` in the expression passed to the `where_exp` filter to employ multiple
conditionals in the operation.

For example, to get a list of documents on English horror flicks, one could use the following snippet:

{% raw %}
```liquid
{{ site.movies | where_exp: "item", "item.genre == 'horror' and item.language == 'English'" }}
```
{% endraw %}

Or to get a list of comic-book based movies, one may use the following:

{% raw %}
```liquid
{{ site.movies | where_exp: "item", "item.sub_genre == 'MCU' or item.sub_genre == 'DCEU'" }}
```
{% endraw %}

### Standard Liquid Filters

For your convenience, here is the list of all [Liquid filters]({{ page.shopify_filter_url }}) with links to examples in the official Liquid documentation.

{% for filter in page.shopify_filters %}
- [{{ filter }}]({{ filter | prepend: page.shopify_filter_url | append: '/' }})
{% endfor %}
