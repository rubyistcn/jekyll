---
layout: default
parent: 配置
grand_parent: 构建
nav_order: 8
title: WEBrick 选项
permalink: /build/configuration/webrick/
---
You can provide custom headers for your site by adding them to `_config.yml`

```yaml
# File: _config.yml
webrick:
  headers:
    My-Header: My-Value
    My-Other-Header: My-Other-Value
```

### Defaults

Jekyll provides by default `Content-Type` and `Cache-Control` response
headers: one dynamic in order to specify the nature of the data being served,
the other static in order to disable caching so that you don't have to fight
with Chrome's aggressive caching when you are in development mode.
