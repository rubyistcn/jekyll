---
layout: default
parent: 构建
nav_order: 1
title:  命令行用法
---

Jekyll Gem 使 `jekyll` 成为可在终端执行的命令。

`jekyll` 程序有一些结构类似的命令：

```
jekyll command [argument] [option] [argument_to_option]

Examples:
    jekyll new site/ --blank
    jekyll serve --config _alternative_config.yml
```

最典型的用法如您在本地做开发的时候用 `jekyll serve` 和您需要为产品生成站点是用 `jekyll build`。

对于所有选项和它们的参数，查阅[构建命令选项](/docs/configuration/options/#build-command-options)。

这有一些常用命令：

* `jekyll new PATH` - 用默认 Gem 主题在指定路径创建新的 Jekyll 站点。目录依需要创建。
* `jekyll new PATH --blank` - 在指定路径创建一个空的 Jekyll 站点框架。
* `jekyll build` 或 `jekyll b` -  执行该命令在 `./_site`（默认）一次性构建您的站点。
* `jekyll serve` 或 `jekyll s` - 任何时间只要源文件修改就重新构建站点，然后在本地启动服务。
* `jekyll clean` - 移除所有生成文件：目标文件夹、元数据文件、Sass 和 Jekyll 缓存。
* `jekyll help` - 显示帮助，选项为一个设定的子命令，例如，`jekyll help build`。
* `jekyll new-theme` - 创建一个新的 Jekyll 主题框架。
* `jekyll doctor` - 输出所有过时或者配置的问题。

要改变 Jekyll 的默认构建行为可以查看[配置选项](/docs/configuration/)。
