---
layout: post
title:  "vscode 配置 c/c++ 环境"
categories: tools
tags:  vscode 配置 c
author: HanCruise
---

* content
{:toc}

#### 准备
***
vscode只是代码编辑器，编译调试需要安装编译器，这里编译器为MinGW
- [Visual Studio Code下载](https://code.visualstudio.com/download)  
选择对应系统下载，有32位及64位之分
- [MinGW](http://www.mingw.org/)  
点击右上角不起眼的小按钮*Download Installer*会自动识别系统下载  




#### 安装
***
- vscode按提示操作安装；
- MinGW按提示操作安装，加入系统环境变量。  

#### 设置
***
- vscode设置  
1. 插件选择c/c++ Microsoft出品，安装，重新加载；
2. 创建一个工作文件夹，用vscode打开；
3. 新建.c文件，键入代码，按照提示配置三个json文件，如下：  
*c_cpp_properties.json*  
找到win32部分，配置includePath如下  
```
"includePath": [
    "${workspaceFolder}",
    "C:\\MinGW\\lib\\gcc\\mingw32\\6.3.0\\include",
    "C:\\MinGW\\lib\\gcc\\mingw32\\6.3.0\\include\\c++",
    "C:\\MinGW\\include"
],
```
*launch.json*  
修改program/miDebuggerPath/preLaunchTask参数如下，其中miDebuggerPath为刚才安装的MinGW中gdb.exe路径，preLaunchTask参数为gcc，如为c++项目改为g++。  
```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/a.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": true,
            "MIMode": "gdb",
            "miDebuggerPath": "C:/MinGW/bin/gdb.exe",
            "preLaunchTask": "gcc",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}
```
*Tasks.json*  
修改label/command参数为gcc，c++项目修改为g++；修改args如下：  
```
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "gcc",
            "type": "shell",
            "command": "gcc",
            "args": [
                "-g","${file}"
            ]
        }
    ]
}
```
配置完成会在项目文件夹生成一个.vscode文件夹，以后的c/c++项目直接复制此文件夹，免去配置步骤。  
- MinGW设置
1. 打开MinGW Installation Manager；
2. 选中Basic Setup将右侧的Package右键全部Mark for Installation；
3. 点击菜单Installation选择Apply Changes开始配置，需要几分钟即完成。  

#### 调试  
***
代码编写好，点击左侧调试按钮进入调试，至此vscode配置c/c++编译环境完成！
