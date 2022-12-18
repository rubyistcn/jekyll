---
layout: default
parent: 手把手教程
grand_parent: 起步
nav_order: 1
title: 设置
permalink: /getting-started/step-by-step/01-setup/
---

欢迎来到 Jekyll 的手把手教程。本教程将带领您不依赖默认的 Gem 主题，而是从只需有些前端
网页开发经验到构建您的第一个 Jekyll 站点的实战。

## 安装

Jekyll 是一个 Ruby Gem。首先，在您的机器上安装 Ruby。
跳到[安装]({{ '/getting-started/installation/' | relative_url }})部分，按照针对您的操作系统的说明操作。

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

现在您可以使用教程中列出的所有 Jekyll 命令了，前提是使用 `bundle exec` 前缀加上命令，
这样才能确保您使用的是您的 `Gemfile` 定义的 Jekyll 版本。

## 创建站点

是时候该创建一个站点了！创建一个新的站点目录——目录名字如您所愿即可。教程中我们将其叫做 **root**。

这时您也可以将其初始化为一个 Git 源码库。

Jekyll 一个最伟大的功能就是不使用数据库。所有的站点内容和结构都是 Git 控制的源码库文件。
使用源码库进行版本控制只是可选功能，但是推荐使用。更多 Git 相关信息参阅
[Git 手册](https://guides.github.com/introduction/git-handbook/)。

让我们添加您的第一个文件。在 **root** 目录用下面内容创建 `index.html`：

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

## 构建

由于 Jekyll 是一个静态站点生成器，所以在我们看到站点前需要构建。运行下列任意命令都可
以构建您的站点：

* `jekyll build` - 构建站点，输出静态站点到指定 `_site` 目录。
* `jekyll serve` - 除了完成 `jekyll build` 的任务外，还要将站点在本地服务器运行在 `http://localhost:4000`，您做出任何修改都需要重新构建站点。

{: .note .info}
当您开发站点时，用 `jekyll serve`。强制浏览器刷新修改内容使用 `jekyll serve --livereload`。
如果出现 URL 或者 端口冲突，您最好如 [serve 命令选项]({{ '/docs/configuration/options/#serve-command-options' | relative_url }})所述使用 `--host` 和 `--port` 参数使 Jekyll 将开发站点的 URL 或者端口错开。

{: .note .warning}
通过 `jekyll serve` 在 `_site` 目录构建的站点并不适合部署。用 `jekyll serve` 生成的站点链接和网站资源的 URL 都是 `https://localhost:4000` 或者来自命令行传递的值，而不是来自于[您的站点配置文件]({{ '/build/configuration/' | relative_url }})。当您的站点准备好部署时可以学习教程有关[部署]({{ '/getting-started/step-by-step/10-deployment/' | relative_url }})部分资料。


运行 `jekyll serve` 然后在您的浏览器中浏览
<a href="http://localhost:4000" target="_blank" data-proofer-ignore>http://localhost:4000</a>。您会看到“Hello World!”。

此时，您可能会想：“啥？”。折腾半天，Jekyll 就是从一个地方拷贝 HTML 文件到另一个地方。

别慌，年轻人，要了解的东西还很多！

接下来，您会学习关于 Liquid 和模板。
