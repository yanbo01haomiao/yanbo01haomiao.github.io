---
layout:     post
title:      "使用jekyll搭建blog有感"
subtitle:   " \"Hello World, Hello Blog\""
date:       2020-06-05 00:01:00
author:     "yanbo"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 生活
    - Meta
    - 博客
---

## Intro

[Jekyll](http://jekyllcn.com/) 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如 Markdown）和其的 Liquid渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 [GitHub Page](http://pages.github.com/) 上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是**完全免费**的。

安装环境以Linux环境为例。我这里使用腾讯云来进行安装。

## 事先准备

安装 Jekyll 相当简单，但是你得先做好一些准备工作。开始前你需要确保你在系统里已经有如下配置。

- [Ruby](http://www.ruby-lang.org/en/downloads/)（including development headers, Jekyll 2 需要 v1.9.3 及以上版本，Jekyll 3 需要 v2 及以上版本）
- [RubyGems](http://rubygems.org/pages/download)
- Linux, Unix, or Mac OS X
- [NodeJS](http://nodejs.org/), 或其他 JavaScript 运行环境（Jekyll 2 或更早版本需要 CoffeeScript 支持）。
- [Python 2.7](https://www.python.org/downloads/)（Jekyll 2 或更早版本）

下面对于这些环境项配置安装。记录我的个人安装过程。

### Ruby的安装

使用[RVM](https://github.com/rvm/ubuntu_rvm)进行安装。安装细节见github主页。

安装`software-properties-common`库。

```bash
$ sudo apt-get install software-properties-common
```

添加PPA和功能包。

```bash
$ sudo apt-add-repository -y ppa:rael-gc/rvm
$ sudo apt-get update
$ sudo apt-get install rvm
```

写入窗口配置`~/.bashrc`。如果使用zsh需要改成`~/.zshrc`。

```bash
$ echo 'source "/etc/profile.d/rvm.sh"' >> ~/.bashrc
$ source ~/.zshrc
$ rvm install ruby
```

但是这个安装遇到了问题，安装完成之后找不到命令，所以选择源码安装。下载源码压缩包`ruby-2.7.1.tar.gz`然后

```bash
$ tar -xvzf ruby-2.7.1.tar.gz
$ cd ruby-2.7.1
$ ./configure
$ make
$ sudo make install		
```

安装后输入`ruby -v`检查版本为ruby 2.7.1。安装结束。

### RubyGems的安装

[官方地址](https://rubygems.org/pages/download)

使用源码包安装。下载，然后解压，进入目录，运行`ruby setup.rb`，需要root权限。

### NodeJS的安装

```bash
sudo apt-get install nodejs
sudo apt-get install npm
```

检查版本：

```bash
➜  ubuntu nodejs -v
v8.10.0
➜  ubuntu npm -v
3.5.2
```

版本太老了，需要更新：

```bash
//更新npm为指定版本
$ npm i -g npm@6.14.4  
//安装node版本管理工具n
$ npm i -g n
//安装node最新版本
$ n latest
//查看安装的版本
$ n
```

```bash
➜  ubuntu nodejs -v
v14.4.0
➜  ubuntu npm -v
6.14.5
```


### Python2.7的安装

检测python版本满足要求即可。

```bash
$ python -V
Python 2.7.15+
```

## 用 RubyGems 安装 Jekyll

安装 Jekyll 的最好方式就是使用RubyGems. 打开终端输入：

```bash
$ gem install jekyll -V
```

会出现安装速度很慢的情况，使用清华的源

使用以下命令替换 gems 默认源

```bash
# 添加 TUNA 源并移除默认源
$ gem sources --add https://mirrors.tuna.tsinghua.edu.cn/rubygems/ --remove https://rubygems.org/
# 列出已有源
$ gem sources -l
# 应该只有 TUNA 一个
```

在使用Jekyll开发之前，检查一下Jekyll是不是最新版本，执行下面命令之一：

```bash
$ jekyll --version
$ gem list jekyll
```

官方推荐安装bundler。

```bash
$ gem install bundler
```

更换默认源：使用以下命令替换 bundler 默认源

```bash
$ bundle config mirror.https://rubygems.org https://mirrors.tuna.tsinghua.edu.cn/rubygems
```

## 配置vscode与远程腾讯云

参考文章：https://zhuanlan.zhihu.com/p/64849549

