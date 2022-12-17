---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 1
title: 设置
---

欢迎来到 Jekyll 的手把手教程。本教程将带领您不依赖默认的 Gem 主题，而是从有些前端
网页开发经验到构建您的第一个 Jekyll 站点的实战。

## 安装

Jekyll 是一个 Ruby Gem。首先，在您的机器上安装 Ruby。
跳到[安装]({{ '/docs/installation/' | relative_url }})部分，按照针对您的操作系统的
说明操作。

安装完 Ruby，从终端安装 Jekyll：

```sh
gem install jekyll bundler
```

创建一个新 `Gemfile`，列出您的项目的依赖软件：

```sh
bundle init
```

在一个文本编辑器里编辑 `Gemfile`，添加 jekyll 为依赖软件：

```ruby
gem "jekyll"
```

运行 `bundle` 为您的项目安装 jekyll。

You can now prefix all jekyll commands listed in this tutorial with `bundle exec`
to make sure you use the jekyll version defined in your `Gemfile`.

## Create a site

It's time to create a site! Create a new directory for your site and name
it whatever you want. Through the rest of this tutorial we'll refer to this
directory as **root**.

You can also initialize a Git repository here.

One of the great things about Jekyll is there's no database. All content and
site structure are files that a Git repository can version. Using a repository
is optional but is recommended. You can learn more
about using Git by reading the
[Git Handbook](https://guides.github.com/introduction/git-handbook/).

Let's add your first file. Create `index.html` in **root** with the following
content:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

## Build

Since Jekyll is a static site generator, it has to build the site
before we can view it. Run either of the following commands to build your site:

* `jekyll build` - Builds the site and outputs a static site to a directory
called `_site`.
* `jekyll serve` - Does `jekyll build` and runs it on a local web server at `http://localhost:4000`, rebuilding the site any time you make a change.

{: .note .info}
When you're developing a site, use `jekyll serve`. To force the browser to refresh with every change, use `jekyll serve --livereload`.
If there's a conflict or you'd like Jekyll to serve your development site at a different URL, use the `--host` and `--port` arguments,
as described in the [serve command options]({{ '/docs/configuration/options/#serve-command-options' | relative_url }}).

{: .note .warning}
The version of the site that `jekyll serve` builds in `_site` is not suited for deployment. Links and asset URLs in sites created
with `jekyll serve` will use `https://localhost:4000` or the value set with command-line configuration, instead of the values set
in [your site's configuration file]({{ '/docs/configuration/' | relative_url }}). To learn about how to build your site when it's
ready for deployment, read the [Deployment]({{ '/docs/step-by-step/10-deployment/' | relative_url }}) section of this tutorial.


Run `jekyll serve` and go to
<a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a> in
your browser. You should see "Hello World!".

At this point, you might be thinking, "So what?". The only thing that happened was that Jekyll copied an
HTML file from one place to another. 

Patience, young grasshopper, there's
still much to learn!

Next. you'll learn about Liquid and templating.
