---
layout: post
title:  "jQuery"
categories: Other
tags: jQuery
author: Liu
description: 
---
# 2019年08月07日22:51:51

## 选择元素

jQuery最基本的概念是“选择一些元素并用它们做点什么”  
jQuery支持大多数CSS3选择器，以及一些非标准选择器。 
id选择器，`$("#myID");`  
类选择器，`$(".myClass");`  
属性选择器，`$("input[name='first_name']");`  
按复合css选择器选择元素，`$("#contents ul.people li");`
使用逗号分隔的列表选择元素，`$("div.myClass, ul.people");`
伪类选择器，`$("a.external:first");`  
`$("tr:odd");`
`$("#myForm:input");`
`$("div:visible");`
`$("div:gt(2)");`
`$("div:animated");`

## $

个人理解，这个`$` 就代表了`jQuery`这几个字。$用作快捷方式jQuery  

## 精炼和过滤选择

        // Refining selections.
        $( "div.foo" ).has( "p" );         // div.foo elements that contain <p> tags
        $( "h1" ).not( ".bar" );           // h1 elements that don't have a class of bar
        $( "ul li" ).filter( ".current" ); // unordered list items with class of current
        $( "ul li" ).first();              // just the first unordered list item
        $( "ul li" ).eq( 5 );              // the sixth

## 获取或设置元素信息

`.html()` - 获取或设置HTML内容  
`.text()` - 获取或设置文本内容；HTML将被剥离  
`.attr()` - 获取或设置听的属性的值  
`.width()` - 以整数的形式获取或设置选区中的第一个元素的宽度，以像素为单位
`.height()` - 以整数形式获取或设置选区中第一个元素的高度，像素为单位  
`.position()` - 获取一个对象，其中包含选择中第一个元素相对于其第一个定位祖先的位置信息This is a getter only  
`.val()` - 获取或设置表单元素的值  



