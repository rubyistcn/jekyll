---
layout: default
title: 快速起步
parent: 起步
nav_order: 1
permalink: /getting-started/quickstart/
---

# 快速起步

Jekyll 是一款静态站点生成器——用您喜欢的标记语言编写文字内容，然后再加上模板就可以创建静态站点。
您可以根据需要调整站点的外观、URL、页面的数据等等。 

## 预装软件

Jekyll 需要：

* Ruby 版本为 **{{ site.data.ruby.min_version }}** 或者更高
* RubyGems
* GCC 和 Make

查阅[需求]({{ '/getting-started/installation/#requirements' | relative_url }})有关指南，获取更多细节。

## 说明

1. 安装所有的[预装软件]({{ '/getting-started/installation/' | relative_url }})。
2. 安装 Jekyll 和 bundler [gems]({{ '/getting-started/ruby-101/#gems' | relative_url }})。
```sh
gem install jekyll bundler
```
3. 在 `./myblog` 创建一个新的 Jekyll 站点。
```sh
jekyll new myblog
```
4. 进入新目录。
```sh
cd myblog
```
5. 构建站点，使其可本地预览。
```sh
bundle exec jekyll serve
```
6. 浏览 [http://localhost:4000](http://localhost:4000){:target="_blank"}

{: .warning}
如果您使用 Ruby 版本 3.0.0 或更高，第 5 步[可能会失败](https://github.com/github/pages-gem/issues/752)。您可以通过添加 `webrick` 到依赖项 `bundle add webrick` 来修复它。

{: .info}
给 `serve` 传递 `--livereload` 参数可实现自动刷新页面的元文件的修改： `bundle exec jekyll serve --livereload`


如果期间您遇到任何错误，检查您是否已经根据[需求]({{ '/getting-started/installation/#requirements' | relative_url }})安装了所有预装软件。如果您还有问题，查看[问题聚焦]({{ '/troubleshooting.html#配置问题' | relative_url }})。

{: .info}
安装情况视操作系统不同而不同。查阅我们的[指南]({{ '/getting-started/installation/#指南' | relative_url }})获取针对不同操作系统的说明。
