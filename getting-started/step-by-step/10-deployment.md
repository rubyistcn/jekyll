---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 10
title: 部署
permalink: /getting-started/step-by-step/10-deployment/
---
最后我们将为生产环境的部署做准备。

## Gemfile

推荐为您的站点使用 [Gemfile](/getting-started/ruby-101/#gemfile)。这会确保 Jekyll 和其他 Gem 的版本即使环境不同也能保持一致。

在 `root` 目录创建一个 `Gemfile` 文件。
该文件只是 'Gemfile'，**不**应该有任何扩展名。
您可以通过 Bundler 创建 `Gemfile`，然后添加 `jekyll` Gem：

```sh
bundle init
bundle add jekyll
```

您的文件看起来应该这样：

```ruby
# frozen_string_literal: true
source "https://rubygems.org"

gem "jekyll"
```

Bundler 安装 Gem，然后创建一个 `Gemfile.lock` —— 用于锁定当前 Gem 的版本号以备 `bundle install` 时用。如果您想要更新您的 Gem 版本，只需 `bundle update` 即可。

当使用 `Gemfile` 时，运行诸如 `jekyll serve` 命令时因该使用 `bundle exec` 前缀。所以完整命令是：

```sh
bundle exec jekyll serve
```

这将限制您的 Ruby 环境只用您的 `Gemfile` 中设定的 Gem 版本。

## 插件

Jekyll 插件允许您针对您的站点创建定制生成内容。这有一些可用[插件](/guides/plugins/)，或者您也可以编写自己的插件。

几乎所有 Jekyll 站点都用的三款官方支持插件：

* [jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap) - 创建一个可以帮助搜索引擎索引内容的站点地图
* [jekyll-feed](https://github.com/jekyll/jekyll-feed) - 为您的帖子创建一个 RSS 供稿
* [jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag) - 添加有助于 SEO 的  meta 标签

第一次使用这些您需要将它们添加到 `Gemfile`。如果您将它们放入了 `jekyll_plugins` 组，它们会自动被 Jekyll `require`：

```ruby
source 'https://rubygems.org'

gem 'jekyll'

group :jekyll_plugins do
  gem 'jekyll-sitemap'
  gem 'jekyll-feed'
  gem 'jekyll-seo-tag'
end
```

然后添加下面代码行到您的 `_config.yml`：

```yaml
plugins:
  - jekyll-feed
  - jekyll-sitemap
  - jekyll-seo-tag
```

现在通过运行 `bundle update` 安装它们。

`jekyll-sitemap` 不需要任何设置，系统在构建时会创建您的站点地图。

对于 `jekyll-feed` 和 `jekyll-seo-tag`，您需要添加 Tag 到
`_layouts/default.html`:

{% raw %}
```liquid
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="/assets/css/styles.css">
    {% feed_meta %}
    {% seo %}
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>
```
{% endraw %}

重启您的 Jekyll 服务器，检查这些 Tag 是否添加到 `<head>`。

## 环境

有些时候，您可能在生产环境需要输出一些东西，但在开发环境不需要。最常见的例子就是分析
脚本，就是这种用法。

要做到这些您需要使用[环境](/build/configuration/environments/)。您可以通过运行命令
时使用 `JEKYLL_ENV` 环境变量来设定当前环境：

```sh
JEKYLL_ENV=production bundle exec jekyll build
```

默认的 `JEKYLL_ENV` 值为开发（development）环境。`JEKYLL_ENV` 值在 Liquid 中可以使用
 `jekyll.environment` 获取。所以要想在只有产品环境时使用分析脚本可以这样：

{% raw %}
```liquid
{% if jekyll.environment == "production" %}
  <script src="my-analytics-script.js"></script>
{% endif %}
```
{% endraw %}

## 部署

最后一步是将站点部署到产品服务器。最基本的方式是运行产品构建：

```sh
JEKYLL_ENV=production bundle exec jekyll build
```

然后复制 `_site` 的内容到您的服务器。

<div class="note warning">
  <h5>站点构建时目标文件间会被清理</h5>
  <p>
    当站点构建时，<code>_site</code> 内容默认会被自动清理。站点构建处理中未创建的文件或者文件夹都会被移除。
  </p>
  <p>
    需要保留的文件可以通过将它们在配置命令指定为 <code>keep_files</code> 来完成。其它需要保留的文件就是 <code>assets</code> 目录的文件了。
  </p>
</div>

更好的方式是用 [CI](/guides/deployment/automated/) 或者[第三方软件](/guides/deployment/third-party/)自动部署。

## 收工

在教程的最后将开始您的 Jekyll 之旅！

* 到[社区论坛](https://talk.jekyllrb.com)报到
* 通过[做贡献](/contributing/)使 Jekyll 变得更好
* 保持构建 Jekyll 站点！
