# yanbo's blog

仓库是github page的静态托管库，本地采用jekyll的render，目录结构也很清晰，模板的复用让md的编写指专注于文章即可。不仅是仓库，也是网站。

本地linux配置和使用jekyll的教程看[这里](./_posts/2020-06-04-using-jekyll.md)。

### 项目结构

目录结构一般是像这样的：

```
.
├── _config.yml
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _site
├── .jekyll-metadata
└── index.html
```

文件作用：文件 / 目录	描述

_config.yml

保存配置数据。很多配置选项都可以直接在命令行中进行设置，但是如果你把那些配置写在这儿，你就不用非要去记住那些命令了。

```
# Site settings
title: Hux Blog             # 你的博客网站标题
SEOTitle: Hux Blog			# 在后面会详细谈到
description: "Cool Blog"    # 随便说点，描述一下

# SNS settings      
github_username: huxpro     # 你的github账号
weibo_username: huxpro      # 你的微博账号，底部链接会自动更新的。

# Build settings
# paginate: 10              # 一页你准备放几篇文章
```

_includes

你可以加载这些包含部分到你的布局或者文章中以方便重用。可以用这个标签 {% include file.ext %} 来把文件 _includes/file.ext 包含进来。

_layouts

layouts（布局）是包裹在文章外部的模板。布局可以在 YAML 头信息中根据不同文章进行选择。 标签 {{ content }} 可以将content插入页面中。

> 可以理解_includes是一个个组件，而_layouts是使用一些组件来组织一个页面

_posts

这里放的就是你的文章了。文件格式很重要，必须要符合: YEAR-MONTH-DAY-title.MARKUP。 永久链接 可以在文章中自己定制，但是数据和标记语言都是根据文件名来确定的。我选择md书写文件，可以在本地使用typora书写完成后直接放进这个文件夹中。命名格式yyyy-MM-dd-title-name.md。使用连接符连接，只使用数字和小写字母。

_data

格式化好的网站数据应放在这里。jekyll 的引擎会自动加载在该目录下所有的 yaml 文件（后缀是 .yml, .yaml, .json 或者 .csv ）。这些文件可以经由 ｀site.data｀ 访问。如果有一个 members.yml 文件在该目录下，你就可以通过 site.data.members 获取该文件的内容。

_site

一旦使用 Jekyll 完成转换，就会将生成的页面放在这里（默认）。这个目录放进 .gitignore 文件。

.jekyll-metadata

该文件帮助 Jekyll 跟踪哪些文件从上次建立站点开始到现在没有被修改，哪些文件需要在下一次站点建立时重新生成。该文件不会被包含在生成的站点中。将它加入到 .gitignore 文件。

index.html and other HTML, Markdown, Textile files

如果这些文件中包含 YAML 头信息 部分，Jekyll 就会自动将它们进行转换。当然，其他的如 .html, .markdown, .md, 或者 .textile 等在你的站点根目录下或者不是以上提到的目录中的文件也会被转换。

Other Files/Folders

其他一些未被提及的目录和文件如 css 还有 images 文件夹， favicon.ico 等文件都将被完全拷贝到生成的 site 中。

### 更新日志

2020-06-05 修改readme，修改文章列表预览文字过多问题。

2020-06-04 初始化项目提交