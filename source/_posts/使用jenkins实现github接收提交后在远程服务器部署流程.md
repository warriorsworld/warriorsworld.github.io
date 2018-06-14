---
title: 使用jenkins实现github接收提交后在远程服务器部署流程
date: 2018-06-14 09:28:01
tags:
    - jenkins
    - github
categories: 持续集成
---

## 引言

首先简单科普一下[持续集成](https://baike.baidu.com/item/%E6%8C%81%E7%BB%AD%E9%9B%86%E6%88%90/6250744)(Continuous Integration, 简称CI)的概念。

<blockquote style="padding: 16px;background: #EEF0F4;border-left: 8px solid #DDDFE4;">
持续集成是一种软件开发实践，即团队开发成员经常集成他们的工作，通常每个成员每天至少集成一次，也就意味着每天可能会发生多次集成。每次集成都通过自动化的构建（包括编译，发布，自动化测试)来验证，从而尽快地发现集成错误。 --- Martin Fowler
</blockquote> 

从应用的角度来说，也就是在我们的项目开发中，任何人对代码库的修改，都会触发CI服务器对项目的自动构建，自动运行测试，甚至到最后的测试环境部署。这样做的好处是，随时的发现问题，随时修复，可以让产品快速的迭代，同时还能保证代码质量。常用的持续集成软件有:
- Travis CI：是一个在线托管的CI服务，和github强关联。使用它来持续集成，不需要自己搭建服务器，对开源项目免费，对github的私有项目需有偿使用。

- Jenkins CI：需要自己搭服务器，功能与Travis类似，免费的CI提供商。

除此之外还有 [CodeShip](https://codeship.com/)，[QuickBuild](https://www.pmease.com/) 等常见的构建工具，大家有兴趣可以学习了解一下。

### 本文实现目标

本文将从 jenkins 的安装，配置，插件安装以及最终实现在 github 提交代码后，经过 jenkins 的自动化构建将最终打包好的代码部署在远程的测试服务器的整个流程为目标来讲解前端代码自动化部署的过程。

1. [jenkins的安装](#cmd_1)
2. [相关插件的安装](#cmd_2)
3. [jenkins的相关配置](#cmd_3)
4. [jenkins与github的webhook的挂载](#cmd_4)
5. [构建模式的详解](#cmd_5)
6. [实例项目的集成部署实例](#cmd_6)

<!--more-->

### 1. <span id="cmd_1">jenkins的安装</span>