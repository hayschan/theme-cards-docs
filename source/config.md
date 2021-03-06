---
title: 基本配置
type: docs
permalink: config/
date: 2020-04-24 10:30:08
---

请使用 Notepad++，VS Code，Vim 等编辑器打开主题配置文件。对于 Windows 用户，**不建议** 使用自带记事本打开配置文件，因为可能会带来难以预测的编码错误。

## Head

生成 HTML 的头部信息 `<head>`。

### favicon

站点图标。

```yaml
favicon: /favicon.ico
```

默认为网页目录下的 `/favicon.ico`（根据 Hexo 生成规则也就是 `source/favicon.ico`），可以替换为其他路径，如：

```yaml
favicon: https://cdn.jsdelivr.net/npm/chrdnx@1.0.5/icon/favicon-32-transparent.png
```

这样便无需再将图标下载至站点目录中。

### opengraph

社交链接分享协议，开启后某些社交平台（如 Twitter、Facebook、Telegram 等）粘贴文章链接便能自动生成分享卡片。也有助于爬虫更好地理解你的内容。

```yaml
opengraph: 
  enable: true
  type: 
  twitter_card: summary_large_image
  twitter_id: 
  twitter_site: 
  image: page.thumbnail
  fb_admins: 
  fb_app_id: 
```

### custom_text

可以在此处随意添加信息，所有内容会被追加到 `<head>` 内，例如搜索引擎所有权验证等。

```yaml
custom_head: 
  - '<meta name="xxxx-site-verification" content="xxxxxxxxxxxxxxxx" />'
  - '<meta name="xxxx-site-verification" content="xxxxxxxxxxxxxxxx" />'
  ...
```

## NavBar

导航栏配置，默认显示在页面最上方。

### sitename

显示在导航栏左侧的名称。若此处留空将自动默认显示站点配置文件的 `title`。

```yaml
sitename: [ name ]
```

### menu

导航栏右侧的按钮菜单，通常用于站内导航。

```yaml
menu: 
  - name: 首页
    url: /
  - name: 标签
    url: /tags/
  - name: 归档
    url: /archives/
  - name: 友链
    url: /friends/
  - name: RSS
    url: /atom.xml
```

每个按钮包含两个参数：`name` 和 `url`。前者定义按钮的显示文字，后者定义点击按钮所跳转的链接。

### sticky

启用此项使导航栏永远置于屏幕顶端，不随页面滚动。仅当屏幕宽度不小于 1080px 时生效。

```yaml
sticky: false
```

## Cover

封面配置，默认显示在除了文章页以外任何页面顶部。

### sitename

显示在封面的标题，如已设置 `avatar` 则不展示 `sitename` 。若此处留空将自动默认显示站点配置文件的 `title`。

```yaml
sitename: [ title ]
```

### avatar

站点徽标（注意此项与 `favicon` 不同），展示为以 `96px` 为直径的圆形图标。如已设置 `avatar` 则不展示 `sitename`，如果两项均设置将优先展示 `avatar`。

```yaml
avatar: [ url of your avatar image ]
```

### description

一句话介绍/个性签名，展示在 `sitename`/`avatar` 下方。

```yaml
description: Hi, nice to meet you!
```

## Style

用于控制站点自定义样式。再次提醒：如需自定义样式，请关闭默认 CDN 或更改对应 CDN 配置！

### color

主要颜色样式，控制导航按钮、ToC、归档页面选中下划线颜色。

```yaml
color: 
  main_color: '#eb5757'
```

### radius

圆角设置，控制卡片圆角半径。

```yaml
radius: 
  main_radius: 5px
```

### space

基准间距，防止板块相距过密。

```yaml
space: 
  main_space: 3.5rem
  sm_space: 1.5rem	# 当屏幕宽度小于 650px 时候启用
```

### highlight / hljs / prismjs

详见 [拓展插件 - 代码高亮](/expand/#%E4%BB%A3%E7%A0%81%E9%AB%98%E4%BA%AE)。

## Meta

设置譬如默认文章标题、日期格式、文章摘要、文章尾部版权声明、自定义 footer 等信息格式。

### title

默认文章标题。当一篇文章不含标题时自动展示此标题顶替。

```yaml
# 默认文章标题，若文章无标题则展示此标题
title: no-title
```

### author

默认作者，现暂主要用于 copyright 声明。日后会考虑添加展示文章作者的功能，方便多用户站点。

```yaml
# 默认文章作者（可在front-matter中覆盖）
author:
  name: ChrAlpha
  url: https://chralpha.com
```

此设置可在文章 `front-matter` 中覆盖。

### date

文章创建日期，通常展示在首页文章摘要下方与文章页标题下方。

```yaml
# 文章创建日期
date:
  title: ''				# 展示在发布日期前的描述
  format: 'YYYY-MM-DD'	# 日期格式 http://momentjs.com/docs/
```

### updated

文章更新日期，通常展示在文章板块最下方。

```yaml
# 文章更新日期
updated:
  title: ''	# 展示在更新日期前的描述
  format: 'YYYY-MM-DD'	# 日期格式 http://momentjs.com/docs/
```

### thumbnail

文章缩略图，可在页面 `front-matter` 中通过 `thumbnail` 字段请求缩略图。当页面未被设置 `thumbnail` 字段时将自动回退至默认缩略图（`default`）。

```yaml
thumbnail: 
  enable: true
  default:
```

### expire

博文也许具备一定时效性，你可以打开 `expire` 自动为距今超过一定时间的文章添加过时提醒。

```yaml
expire: 
  enable: true
  duration: 120
```

其中 duration 单位为「天」，超过该时长则会自动添加过时提醒。

### auto_excerpt

文章默认摘要，可以（且推荐）使用 `<!--more-->` 标记精确截取文章部分作为摘要。

如果你没有设置 `<!--more-->` 标记且没有设置页面 `description` 参数，则会根据 `auto_excerpt` 是否启用来决定截取指定字数（`length`）的摘要。

```yaml
auto_excerpt: 
  enable: true
  length: 150
```

### toc

文章目录，展示在文章页面侧边栏，支持 h2 ~ h5 级标题（不支持 h1）。

```yaml
toc: 
  enable: true
  list_number: false
```

`list_number` 用于控制是否显示编号。

在开启此处全局开关后，仍需在 `layout.post.side` 中添加 `toc` 这一项。而即便全局开启，也可在特定页面 [Front-matter](/write/#Front-matter) 中关闭 ToC 展示。

>   不支持 h1 是经过考量的。无论是为了 SEO 还是为了文章层次性，都不建议在一个页面中添加多个 h1 标题，而文章 title 已是一个 h1 标题。

### copyright

版权声明，若开启将默认文章板块最下方。

```yaml
copyright: 
  enable: true
  
  # 在作者声明和永久链接之后，可以多行，支持 markdown
  custom_text:
    - '文章默认使用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh) 协议进行许可，使用时请注意遵守协议。'
```

可在 `front-matter` 中关闭指定页面的 copyright 组件展示。

```yaml
copyright: false
```

## Footer

网站页脚内容，展示在网页最下方。

### copyright_since

设置站点起始时间，用于底部 copyright 显示。

例如：将此设为 `2018`，那么页脚就会显示 `© 2018 - 2020`（2020 为最后一次页面生成时间）。

如果将此项留空，则单独显示 `© 2020`（2020 为最后一次页面生成时间）。

如果你不想显示任何内容，请将此项设为 `false`。

```yaml
copyright_since:
```

### statistics

网站计数，目前支持 LeanCloud 与不蒜子两种方案，通过 `use` 字段选择。

```yaml
statistics: 

# 选择 LeanCloud/busuanzi 为网站计数。如果你完全不想启用，将 `use` 项留空即可
  use:   # leancloud | busuanzi

  # 如果选择使用 LeanCloud，则需完善下面的配置项
  leancloud: 
    appId: 
    appKey: 
    serverURL:   # REST API 服务器地址，LeanCloud 国际版不填

  # 全站 UV（Unique Viewers）
  site_uv:
    enable: true
    before_text: '' # 展示在数据前的内容，支持 HTML
    after_text: Viewers  # 展示在数据后的内容，支持 HTML
    divider: '&nbsp;&nbsp;&nbsp;|' # 分隔符，HTML 语法支持
  
  # 全站 PV（Page Views）
  site_pv:
    enable: true
    before_text: ''  # 展示在数据前的内容，支持 HTML
    after_text: Views  # 展示在数据后的内容，支持 HTML
    divider: ''  # 分隔符，HTML 语法支持
    
  # 页面 PV
  page_pv:
    enable: true
    before_text: ''
    after_text: Views 
```

`site_uv`/`site_pv` 显示在站点页脚，统计全站访客/访问数。其中：`before_text`（`after_text`）为统计数目之前（之后）显示的内容，支持 HTML；`divider` 问统计数据展示与之后内容的分割符，支持 HTML。

而 `page_pv` 统计单个页面访问数。其中：`before_text`（`after_text`）为统计数目之前（之后）显示的内容，支持 HTML。

### custom_text

自定义页脚，支持 markdown，可用于展示网站备案等。

```yaml
custom_text: 
  # - ''
  # - ''
```

