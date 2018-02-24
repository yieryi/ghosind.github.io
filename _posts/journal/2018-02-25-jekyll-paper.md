---
layout: post
title: Jekyll Paper
date: 2018-02-25
categories: [生活杂谈]
tags: [生活杂谈]
excerpt: 宣传一下新做的Jekyll主题Jekyll Paper。
---

这段时间把博客的前端改了一下，做成了类似于书本的样式。因为一开始使用Github Page来建博客时图方便直接fork了Jekyll Now来使用，本着开源分享的精神，也就单独做了个版本上传到了Github，并且打算一直维护下去。因为是做成了模仿纸质文本的样式，所以取名叫做Jekyll Paper，欢迎到[Jekyll Paper][jekyll-paper]的Github页面去围观。

## Jekyll Paper特色

1. 简洁的界面，专注于阅读，仅页面首尾存在其他无关于文章本身的内容。
2. 选择直接打印页面时隐藏了页面首尾，只保留了文章的内容。

## 当前开发状况

Jekyll Paper的主要代码都已经完成了，未来一段时间内（大概一个月左右）主要会将文档补全，以及修改发现的一些问题。新功能目前想到的是准备支持在config中直接设置界面语言，然后通过js加载指定语言文件写入到界面中。另外，打算将css文件改写为sass以及修改类名，方便维护与修改。最后，可能还会修改一下博客中文章的各样式，如字体图片等，有可能会参考一些比较成熟的论文样式来制作。目前计划是在三月中旬前完成计划中主要的内容（主要是完成文档，新功能可能会延后加入），并在三月下旬到四月上旬期间发布Jekyll Paper的第一个release版。

## 如何使用Jekyll Paper

使用Jekyll Paper的方法十分简单，只要到[Jekyll Paper][jekyll-paper]的页面下fork到自己的账户中，并将fork的repo设置中的repo name修改为`Github用户名.github.io`即可。再完成这一步后就可以通过访问`https://Github用户名.github.io`进入博客了。

[jekyll-paper]: https://github.com/ghosind/Jekyll-Paper