---
title: 构建博客系统
date: 2021-08-03 09:33:43
tags: blog
categories: jottings
---

### 概述

第一篇博客写什么，首先想到的就是

Hello world!

哈哈

后面也没有想出有什么特别的好的主题，所以就写一下如何搭建的目前的这个博客系统。算是感言及分享类型，并不算教程，所以希望学习教程的同学可以移步了。
### 选型
博客系统有很多现成的博客，最常见的是CSDN和博客园，平台并不重要，甚至如果你愿意，微博上组织自己的博客都可以。
那为啥还要搭建自己的博客系统呢? 作为一个优秀的程序员，当然要

**帅！！！**

常用的博客框架，hugo hexo，我选择的是hexo，为什么呢？你以为有一堆的参数对比，然而并没有，只是因为我一开始搜索到的就是hexo。
hugo是go语言开发，hugo更年轻，使用hugo可能会更帅
hexo nodejs开发，hexo的主题可能更多，社区小伙伴可能更多

### 本地环境搭建
安装nodejs
安装git客户端

### 构建发布
#### 启动本地服务
```nodejs
# 安装hexo并配置hexo-cli到环境变量
npm install hexo-cli
# 初始化博客环境
hexo init 
# 生成代码
hexo g
# 启动服务
hexo s
```
#### 部署到远程

远程服务提供，一般依赖代码仓库的pages服务(free!)。常用的pages服务包括github / gitLab / gitee / coding, 其中gitLab pages服务需要配置流水线生成静态代码，但是流水线会让你去注册信用卡信息(国内卡不识别)，gitee pages服务目前关闭了(什么清网行动)，coding配置很麻烦，而且自己定义的仓库不会生效(黑心的小腾讯)，配置第三方仓库可以通过，但是访问还没有试过。所以终上，pages服务只能选择github，看起来是多选题，实际上是个单选。
​    
当然如果你有钱，买一个ECS主机，或者直接部署到真实主机，以上当我没说。
​    
github建库 xxx.github.io.git，xxx为用户名
配置根目录下 _config.yml

```
deploy:
  type: git
  repo: git@github.com:xxx/xxx.github.io.git
  branch: master
```
```bash
# 部署到github(实际上就是把public文件提交到库)　，需要先下载插件
hexo d
```
验证: 访问https://xxx.github.io

### 发布到自己的域名   
申请(buy)一个自己的域名，我是在阿里云购买的。备案:个人域名实名认证即可。解析域名:CNAME填写xxx.github.io(该地址重定向到自己的域名)，A类解析到github地址，以下是我的配置。
![](../pic/domain-mapping.png)
地址信息

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

本地项目source目录下添加CNAME文件，内容是你申请的域名，发布到github
​    
github pages配置下添加上你自己申请的域名，校验通过即可访问

### 博客主题
hexo常用的主题，一般是next或yilia, 个人风格上更喜欢yilia，yilia风格更简洁。但是yilia安装node-sass装不上，而且yilia要自己自定义样式。
所以还是先用一段时间next，用一段时间yilia，然后看看哪个更顺手。

主题配置
站点目录下_config文件配置 theme: next
source目录下，新建_data/next.yml文件，文件内容复制于themes/next/_config文件，override: true
剩余配置文档中有注释，yilia同理

### 博客写作
新建文章hexo new article，语法遵循mark down语法，但是好像一些比如像数学公式之类的支持需要安装额外的插件。
文章归类 tags: blog，categories: jottings 
新建归档页面, tags/index.md
```markdown
---
title: categories
date: 2021-08-03 18:15:42
type: "categories"
comments: false
---
```

### 不可或缺的打赏功能
然后就缺了

### 不可或缺的评论功能



###  源码管理

将本地的源码提交至代码库(新建一个代码库，不是xxx.github.io)，这样就可以实现分布的文件编辑了。

### 下一步计划
优化一下整体的风格，然后坚持每周一篇博客:black_flag:

### 最后感言
能够自己搭建一个博客网站，确实是有一定的成就感。从难易程度上来讲，并没有自己想象的那么简单，回头看确实蛮简单的，但还是耗费了很多精力。

从实用价值上来讲，我的第一篇文章是vscode写的，并不是很方便，但如果网站主题，结构这些定型之后直接用typora进行可视化编辑可能简单些。作为自己的文档管理库，写写随笔，还是挺好的。最主要的是，这个是自己github的门户的门槛，谁不想自己的github主页面好看点呢。

最最最重要的是，这是一份见证。一份虽然很渺小，但也很重要的见证，这就足够了，对吧。







​    



