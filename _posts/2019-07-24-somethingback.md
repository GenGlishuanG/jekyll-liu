---
layout: post
title:  "Vim"
categories: Other
tags: Other
author: Liu
description: 
---
# 2019年07月24日

## 操作部分

关于快捷键，vim内置快捷键，shell常用命令，需要掌握熟练：

        cd
        ll
        mv
        mkdir
        cat
        pwd print working directory
        rm
        touch
        cp
        vi/vim

vim内置快捷键：

        dd
        yy
        20dd
        u
        zf
        zd
        gg
        G

## js JavaScript

通过学习《JavaScript DOM编程艺术》(中文第2版)前6章，自己制作了文中提到的”图片库“网页。网页插入若干个小标题，设置链接；插入同等数量的图片，点击每个小链接切换显示不同的图片，且要求显示在预设好的位置。  
思路整理：在当前页面显示出预设图片，并且设置该图片的宽高，给定的`<img>`标签src属性指向预设的图片即可；陈列出需要的小链接，每个设置好href属性；在js中，对每个链接设置点击事件，点击后调用切换图片的方法，使用getAttribute方法获取链接的href链接，并且赋给`<img>`标签的src属性，就达到了更换图片的效果。  
实际代码中，执行完切换src路径的函数后，给一个return值”false“，该值会拒绝浏览器的默认链接打开方式（相当于告诉浏览器，没有打开网页，也就不会切换到其他页面）。

## js高阶

从csdn上找到一片比较使用的js代码，实现轮播图，复制后改写，作为对js的更深一层的理解。  
原理：
1.设置4个div，class相同设置为banner-slide，css类选择器选择该类，属性值设置为不显示（或用js将该类的图片display属性改为”none“），利用js的setInterval方法，定时切换这些图片的属性，使其中一个的display属性为”block“就可以被显示出来。（随本片文档有该网页的.html文档）  

## js验证邮箱

原理：设置一个`<input>`框，用getElementById获取元素，用.value方法直接获取值，赋给变量a。用正则去匹配a，if方法进行验证，true 则在一个空的p标签内写入预设的文本。  
预设的文本是在js开始的时候声明了一个dict，用正则拿到邮箱的后缀做键去获取dict内的值。  
`<button>`设置一个submit按钮，绑定一个onclick事件，点击后执行上述js代码。

## js 获取时间戳

原理和验证邮箱非常类似。只是在p标签内写入的内容不同。利用(new Data).ValueOf()方法得到时间戳，赋给变量即可，写入该变量。  

2019年07月24日10:04:35
