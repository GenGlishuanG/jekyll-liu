---
layout: post
title:  "chrome插件安装"
categories: Other
tags: Other
author: Liu
description: 
---
# chrome插件安装

## 下载插件包

示例：百度截屏翻译插件。

## 改名并解压

将插件包后缀名改为.zip，就可以使用自带解压软件打开并将文件提取出来。我放到了这个名为`jiepingfanyi`的文件夹里。

![img](http://wx3.sinaimg.cn/mw690/c3f99ef9ly1g5ia2l8ertj20kq0c6q3g.jpg)

## 再改名

`_metadata` 文件夹下划线去掉。

![img](http://wx2.sinaimg.cn/mw690/c3f99ef9ly1g5ia2y46hgj20on0h075q.jpg)

## chrome设置

自定义设置（右上角三个点） ☞ 更多工具 ☞ 扩展程序  
打开“开发者模式”  
加载已解压的扩展程序  
找到刚刚的文件夹，我的文件夹是`jiepingfanyi` 

![img](http://wx1.sinaimg.cn/mw690/c3f99ef9ly1g5ia350888j20hw0ieaby.jpg)
![img](http://wx1.sinaimg.cn/mw690/c3f99ef9ly1g5ia37tg0zj21810nomyi.jpg)

## 另外

该文件夹（`jiepingfanyi`）一旦被chrome设置好，就不能移动或者删除了，否则就不能用了。所以我喜欢放到chrome安装目录下，再加载到chrome设置，目的是chrome被卸载的时候该文件夹一并会删除。Linux系统的chrome安装目录不同于windows，在`/opt/google/chrome`这个目录。但是想要将`jiepingfanyi`文件夹拷贝到这个目录下，没有权限！我使用命令行加了sudo 权限，搞定！

![img](http://wx2.sinaimg.cn/mw690/c3f99ef9ly1g5iaww91vhj20qd0ksgnd.jpgv)
