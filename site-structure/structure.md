---
layout: default
parent: 站点结构
nav_order: 1
title: 目录结构
---
一个基本的 Jekyll 站点看起来这样：

```
.
├── _config.yml
├── _data
│   └── members.yml
├── _drafts
│   ├── begin-with-the-crazy-ideas.md
│   └── on-simplicity-in-technology.md
├── _includes
│   ├── footer.html
│   └── header.html
├── _layouts
│   ├── default.html
│   └── post.html
├── _posts
│   ├── 2007-10-29-why-every-programmer-should-play-nethack.md
│   └── 2009-04-26-barcamp-boston-4-roundup.md
├── _sass
│   ├── _base.scss
│   └── _layout.scss
├── _site
├── .jekyll-cache
│   └── Jekyll
│       └── Cache
│           └── [...]
├── .jekyll-metadata
└── index.html # can also be an 'index.md' with valid front matter
```

<div class="note">
  <h5>基于 Gem 主题的 Jekyll 站点目录结构</h5>
  <p>
    从 {% include docs_version_badge.html version="3.2"%} 版本开始，基于 <a href="/docs/themes/"> Gem 主题</a> 启动一个新的 Jekyll 项目时只需 <code>jekyll new</code> 即可生成一个比较规范的站点结构。这就导致了一个更轻量的目录结构： <code>_layouts</code>、<code>_includes</code> 和 <code>_sass</code> 默认都保存在 Gem 主题内。
  </p>
  <br />
  <p>
     <a href="https://github.com/jekyll/minima">minima</a> 是当前默认主题，<code>bundle info minima</code> 会显示 minima 主题文件在您的计算机的存储位置。
  </p>
</div>

目录结构内文件/文件夹概览：

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>文件 / 文件夹</th>
      <th>简介</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>_config.yml</code></p>
      </td>
      <td>
        <p>
          Stores <a href="/docs/configuration/">configuration</a> data. Many of
          these options can be specified from the command line executable but
          it’s easier to specify them here so you don’t have to remember them.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_drafts</code></p>
      </td>
      <td>
        <p>
          Drafts are unpublished posts. The format of these files is without a
          date: <code>title.MARKUP</code>. Learn how to <a href="/docs/posts/#drafts">
          work with drafts</a>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_includes</code></p>
      </td>
      <td>
        <p>
          These are the partials that can be mixed and matched by your layouts
          and posts to facilitate reuse. The liquid tag
          <code>{% raw %}{% include file.ext %}{% endraw %}</code>
          can be used to include the partial in
          <code>_includes/file.ext</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_layouts</code></p>
      </td>
      <td>
        <p>
          These are the templates that wrap posts. Layouts are chosen on a
          post-by-post basis in the
          <a href="/docs/front-matter/">front matter</a>,
          which is described in the next section. The liquid tag
          <code>{% raw %}{{ content }}{% endraw %}</code>
          is used to inject content into the web page.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_posts</code></p>
      </td>
      <td>
        <p>
          Your dynamic content, so to speak. The naming convention of these
          files is important, and must follow the format:
          <code>YEAR-MONTH-DAY-title.MARKUP</code>.
          The <a href="/docs/permalinks/">permalinks</a> can be customized for
          each post, but the date and markup language are determined solely by
          the file name.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_data</code></p>
      </td>
      <td>
        <p>
          Well-formatted site data should be placed here. The Jekyll engine
          will autoload all data files (using either the <code>.yml</code>,
          <code>.yaml</code>, <code>.json</code>, <code>.csv</code> or
          <code>.tsv</code> formats and extensions) in this directory,
          and they will be accessible via `site.data`. If there's a file
          <code>members.yml</code> under the directory, then you can access
          contents of the file through <code>site.data.members</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_sass</code></p>
      </td>
      <td>
        <p>
          These are sass partials that can be imported into your <code>main.scss</code>
          which will then be processed into a single stylesheet
          <code>main.css</code> that defines the styles to be used by your site.
          Learn <a href="{{ '/docs/assets/' | relative_url }}">how to work with assets</a>. 
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>_site</code></p>
      </td>
      <td>
        <p>
          This is where the generated site will be placed (by default) once
          Jekyll is done transforming it. It’s probably a good idea to add this
          to your <code>.gitignore</code> file.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>.jekyll-cache</code></p>
      </td>
      <td>
        <p>
          Keeps a copy of the generated pages and markup (e.g.: markdown) for
          faster serving. Created when using e.g.: <code>jekyll serve</code>.
          Can be disabled with
          <a href="/docs/configuration/options/">an option and/or flag</a>.
          This directory will not be included in the generated site. It’s
          probably a good idea to add this to your <code>.gitignore</code>
          file.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>.jekyll-metadata</code></p>
      </td>
      <td>
        <p>
          This helps Jekyll keep track of which files have not been modified
          since the site was last built, and which files will need to be
          regenerated on the next build. Only created when using
          <a href="/docs/configuration/incremental-regeneration/">
          incremental regeneration</a> (e.g.: with <code>jekyll serve -I</code>).
          This file will not be included in the generated site. It’s probably
          a good idea to add this to your <code>.gitignore</code> file.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>index.html</code> or <code>index.md</code> and other HTML,
        Markdown files</p>
      </td>
      <td>
        <p>
          Provided that the file has a <a href="/docs/front-matter/">front
          matter</a> section, it will be transformed by Jekyll. The same will
          happen for any <code>.html</code>, <code>.markdown</code>,
          <code>.md</code>, or <code>.textile</code> file in your site’s root
          directory or directories not listed above.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p>Other Files/Folders</p>
      </td>
      <td>
        <p>
          Except for the special cases listed above, every other directory and 
          file—such as <code>css</code> and <code>images</code> folders,
          <code>favicon.ico</code> files, and so forth—will be copied verbatim
          to the generated site. There are plenty of <a href="/showcase/">sites
          already using Jekyll</a> if you’re curious to see how they’re laid
          out.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

`source` 文件夹中每个以字符 `.`、`_ `、`#`或`~`开始的文件或者文件夹都不会包含在 `目标（destination）`文件夹。有些路径必须通过配置文件的 `include` 命令明确定义以确保它们被复制：

```yaml
include:
 - _pages
 - .htaccess
 ```
