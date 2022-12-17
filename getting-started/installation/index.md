---
layout: default
title: 安装
parent: 起步
nav_order: 2
has_children: true
description: 在 macOS、GNU/Linux 或者 Windows 上安装 Jekyll 的官方指南。
---

Jekyll 是一个能安装在大部分操作系统上的 [Ruby Gem]({{ '/getting-started/ruby-101/#gems' | relative_url }})。

## 需求

* [Ruby](https://www.ruby-lang.org/en/downloads/) 版本 **{{ site.data.ruby.min_version }}** 或更高，包含所有开发标头文件（检查您的 Ruby 版本使用 `ruby -v` 命令）
* [RubyGems](https://rubygems.org/pages/download)（检查您的 Gems 版本使用 `gem -v` 命令）
* [GCC](https://gcc.gnu.org/install/) 和 [Make](https://www.gnu.org/software/make/) （检查版本使用 `gcc -v`、`g++ -v` 和 `make -v`）

## 指南

详细安装说明，根据操作系统不同选择：

* [macOS]({{ '/getting-started/installation/macos/' | relative_url }})
* [Ubuntu]({{ '/getting-started/installation/ubuntu/' | relative_url }})
* [其它 Linux]({{ '/getting-started/installation/other-linux/' | relative_url }})
* [Windows]({{ '/getting-started/installation/windows/' | relative_url }})
