---
title: Hexo教程
---

# 前沿
------
利用Github 和开源博客系统Hexo 搭建个人博客
Hexo支持Markdown 官网介绍Hexo 是一个:
> A fast, simple & powerful blog framework

# 准备工作

创建Github 账号 ,并新建一个 命明格式为账号名称 + .github.io 的repository
比如你的账号名称为 zhang123, 就创建一个名称为 zhang123.github.io 的仓库
验证是否创建成功，可以访问 http://zhang123.github.io 查看是否有内容

# 搭建步骤

## 安装git 和 npm

>1.$ brew install git

>2.$ brew install npm
>如果mac上没有安装brew 移步到mac-setup

## 安装Hexo

>1. $ npm install -g hexo

>2. $ npm install -g hexo-cli


## 初始化Hexo
>1.$ hexo init

初始化完成以后当前的目录结构如下


tree . -L 1
.
├── _config.yml  // 项目的配置文件
├── db.json
├── debug.log
├── node_modules
├── package-lock.json
├── package.json
├── public
├── scaffolds // 一些脚手架模版
├── source
└── themes   // 主题文件夹

这里的_config.yml是项目的全局配置

除了默认的主题，更多的主题可以在https://hexo.io/themes/ 查找喜欢的主题
比如想更换成next 主题 先先cd到blog的根目录, 然后安装

>1.$cd your-hexo-site

>1.$ git clone https://github.com/iissnan/hexo-theme-next themes/next

主题下载完成以后我们就可以启用主题了, 编辑项目的_config.yml 文件找到 theme: 这一行修改成:

>1.theme: next

注意 修改插件的配置 在theme/next 等相关theme目录下面, 而不是项目根目录下面的_config.yml 文件

## 新建一篇文章

新建文章的命令为hexo new [layout] blog_title , 其中layout 可以为 post，page
如果不填写 则为默认配置，默认的配置在全觉的_config.yml配置文件中

>1.$ hexo new  我的第一篇博客

>2.INFO  Created: ~/code/blog/source/_posts/我的第一篇博客.md

默认会在 项目的 source/_posts 目录下创建 blog_title.md 的 文件
##生成静态文件

>1.$ hexo generate

命令简写成 hexo g 也可以 此时hexo会将source 下的.md 文档生成到public文件夹下面
生成以后可以执行
>1.hexo server

然后更具提示访问本地http://localhost:4000/ 查看效果

## 部署上线

在部署之前需要选择部署方式, hexo 支持 git、rsync 等方式
以git 为例 需要修改项目配置文件_config.yml, 找到deploy 相关配置
并且 需要额外安装插件

>1.$ npm install hexo-deployer-git --save

修改相关配置


>1.# Deployment
>2.## Docs: https://hexo.io/docs/deployment.html
>3.deploy:
>4.type: git
>5.repo: https://github.com/your-github-name/your-github-name.github.io.git
>6. branch: master

然后执行

>1.$ hexo deploy

在github上查看 这样上传成功啦!



