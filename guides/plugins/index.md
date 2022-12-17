---
layout: default
parent: 指南
nav_order: 1
has_children: true
title: 插件
---

Jekyll has a plugin system with hooks that allow you to create custom generated
content specific to your site. You can run custom code for your site without
having to modify the Jekyll source itself.

{: .note .info}
You can add specific plugins to the `whitelist` key in `_config.yml` to allow them to run in safe mode.

* [Installation]({{ '/guides/plugins/installation/' | relative_url }}) - How to install plugins
* [Your first plugin]({{ '/guides/plugins/your-first-plugin/' | relative_url }}) - How to write plugins
* [Generators]({{ '/guides/plugins/generators/' | relative_url }}) - Create additional content on your site
* [Converters]({{ '/guides/plugins/converters/' | relative_url }}) - Change a markup language into another format
* [Commands]({{ '/guides/plugins/commands/' | relative_url }}) - Extend the `jekyll` executable with subcommands
* [Tags]({{ '/guides/plugins/tags/' | relative_url }}) - Create custom Liquid tags
* [Filters]({{ '/guides/plugins/filters/' | relative_url }}) - Create custom Liquid filters
* [Hooks]({{ '/guides/plugins/hooks/' | relative_url }}) - Fine-grained control to extend the build process
