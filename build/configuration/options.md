---
layout: default
parent: 配置
grand_parent: 构建
nav_order: 1
title: 配置选项
permalink: "/build/configuration/options/"
---

下表列出了 Jekyll 的可用设置，以及各种控制设置的<code
class="option">选项（Option）</code>（配置文件中定义）和<code
class="flag">标记（Flag）</code>（命令行中指定）。

### 全局配置

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>设置</th>
      <th>
        <span class="option">选项</span>和<span class="flag">标记</span>
      </th>
    </tr>
  </thead>
  <tbody>
    {% for setting in site.data.config_options.global %}
      <tr class="setting">
        <td>
          <p class="name">
            <strong>{{ setting.name }}</strong>
            {% if setting.version-badge %}
              <span class="label label-yellow fs-1" title="Introduced in v{{ setting.version-badge }}">{{ setting.version-badge }}</span>
            {% endif %}
          </p> 
          <p class="description">{{ setting.description }}</p>
        </td> 
        <td class="align-center">
          <p><code class="option">{{ setting.option }}</code></p>
          {% if setting.flag %}
            <p><code class="flag">{{ setting.flag }}</code></p>
          {% endif %}
        </td>
      </tr>
    {% endfor %}
    <tr>
      <td>
        <p class='name'><strong>默认值</strong></p>
        <p class='description'>
            为 <a href="{{ '/content/front-matter/' | relative_url }}" title="front matter">Front Matter</a> 变量设置默认值。
        </p>
      </td>
      <td class='align-center'>
        <p>see <a href="{{ '/build/configuration/front-matter-defaults/' | relative_url }}" title="details">见后面</a></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note warning">
  <h5>站点构建时会清理目标文件夹</h5>
  <p>
    站点构建时 <code>&lt;destination&gt;</code> 文件夹默认会被自动清理。并非由 Jekyll 创建的文件文件夹也会被删除。想要保留的文件可以通过配置命令 <code>&lt;keep_files&gt;</code> 留下来。
  </p>
  <p>
    不要将 <code>&lt;destination&gt;</code> 放在重要位置；相反，用临时区域来生成并拷贝文件到您的服务器即可。
  </p>
</div>

### Build 命令选项

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>设置</th>
      <th><span class="option">选项</span>和<span class="flag">标记</span></th>
    </tr>
  </thead>
  <tbody>
    {% for setting in site.data.config_options.build %}
      <tr class="setting">
        <td>
          <p class="name">
            <strong>{{ setting.name }}</strong>
            {% if setting.version-badge %}
              <span class="label label-yellow fs-1" title="Introduced in v{{ setting.version-badge }}">{{ setting.version-badge }}</span>
            {% endif %}
          </p> 
          <p class="description">{{ setting.description }}</p>
        </td> 
        <td class="align-center">
          {% if setting.option %}<p><code class="option">{{ setting.option }}</code></p>{% endif %}
          {% if setting.flag %}<p><code class="flag">{{ setting.flag }}</code></p>{% endif %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
</div>

### Serve 命令选项

In addition to the options below, the `serve` sub-command can accept any of the options
for the `build` sub-command, which are then applied to the site build which occurs right
before your site is served.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>设置</th>
      <th><span class="option">选项</span>和<span class="flag">标记</span></th>
    </tr>
  </thead>
  <tbody>
    {% for setting in site.data.config_options.serve %}
      <tr class="setting">
        <td>
          <p class="name">
            <strong>{{ setting.name }}</strong>
            {% if setting.version-badge %}
              <span class="label label-yellow fs-1" title="Introduced in v{{ setting.version-badge }}">{{ setting.version-badge }}</span>
            {% endif %}
          </p> 
          <p class="description">{{ setting.description }}</p>
        </td> 
        <td class="align-center">
          {% if setting.option %}
            <p><code class="option">{{ setting.option }}</code></p>
          {% elsif setting.options %}
            <p>
              {% for option in setting.options %}
                <code class="option">{{ option }}</code><br>
              {% endfor %}
            </p>
          {% endif %}
          {% if setting.flag %}
            <p><code class="flag">{{ setting.flag }}</code></p>
          {% elsif setting.flags %}
            <p>
            {% for flag in setting.flags %}
              <code class="flag">{{ flag }}</code><br>
            {% endfor %}
            </p>
          {% endif %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
</div>

<div class="note warning">
  <h5>配置文件中不要使用 Tab</h5>
  <p>
    This will either lead to parsing errors, or Jekyll will revert to the
    default settings. Use spaces instead.
  </p>
</div>
