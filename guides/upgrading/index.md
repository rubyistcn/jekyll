---
layout: default
parent: 指南
nav_order: 3
has_children: true
title: 升级
---

从旧版升级 Jekyll？升级
Jekyll 主办本（例如，从 v2.x 到 v3.x）可能令人头疼。查看下面的指南来辅助您升级：

- [从 0.x 到 1.x 和 2.x](/guides/upgrading/0-to-2/)
- [从 2.x 到 3.x](/guides/upgrading/2-to-3/)
- [从 3.x 到 4.x](/guides/upgrading/3-to-4/)

## 次版本升级

<div class="note">
  <h5>保持随时更新</h5>
  <p>我们推荐您尽可能经常更新 Jekyll，以便能保证能够获得最新的问题修复。
  </p>
</div>

如果您按照我们的设置推荐并安装了 [Bundler](http://bundler.io/)，运行 `bundle update jekyll` 或者简单的
运行 `bundle update`，您的所有 Gem 都会更新到最新版。

如果您没有安装 Bundler，运行 `gem update jekyll`。

[如果您用 `github-pages` Gem](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/#keeping-your-site-up-to-date-with-the-github-pages-gem)，过程类似。
