---
layout: post
title:  "vscode 配置 python 环境"
categories: tools
tags:  vscode 配置 python
author: HanCruise
---

* content
{:toc}

#### 准备
***
- 安装vscode，加入环境变量
- 安装python，加入环境变量




#### 配置
***
- 新建一个文件夹作为工作区，在vscode中打开；
- 新建一个.py文件，点击扩展安装python插件（下载量最高那个，Microsoft出品）。  
至此已经基本配置完成，点击F5运行会让选择代码运行环境python或python experimental，选择python代码编译通过。网上很多教程的配置到此为止。  
但我在调试python代码的时候发现每次编译都需要选择代码运行环境，每次都要手动点一下python，很烦！但网上的其它人貌似没有此问题，他们只需要在代码第一次运行时选中一次，以后每次都只需按F5就行。查了诸多教程文档，继续配置：  

- 点击菜单调试->添加配置->选择python，会在工作区文件夹生成配置文件夹.vscode，里面有个launch.json是配置调试环境的。
- 切换到代码页面，点击F5，此时不需选择运行环境，编译通过，done！

#### 拓展
***
需要指出的是，此处虽然只用到了launch.json，实际上vscode配置工作区的文件有三个，都放在.vscode内，可参考上篇文章配置c/c++环境也分别设置了这三个文件，分别为：  
- tasks.json  
配置运行环境的文件，输入ctrl+shift+p在命令栏输入tasks在下拉框中选中tasks configuration，然后选择others，在.vscode内生成tasks.json，此处无需配置。
- launch.json  
配置调试环境的文件，见上。
- settings.json  
为当前工作区的配置文件，配置一些文档属性，优先级>用户设置>默认设置，点击首选项>设置>工作区设置就会在.vscode内生成此文件，此处未配置。

#### 结语
***
开始愉快的玩耍吧！
