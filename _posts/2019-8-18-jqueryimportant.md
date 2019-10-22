---
layout: post
title:  " jQuery重难点"
categories: Other
tags: jQuery
author: Liu
description: 
---
# 2019年8月18日

## jQuery重难点

    $("p:first")    选取第一个 <p> 元素  
    $("ul li:first")    选取第一个 <ul> 元素的第一个 <li> 元素  
    $("ul li:first-child")  选取每个 <ul> 元素的第一个 <li> 元素,但当<ul> 里第一个标签不是<li>标签,则不会命中到该元素.
    $("[href]")     选取带有 href 属性的元素
    $("a[target='_blank']") 选取所有 target 属性值等于 "_blank" 的 <a> 元素,条件还可以是等于,不等于
    $("tr:even")    选取偶数位置的 <tr> 元素  
    $("tr:odd") 选取奇数位置的 <tr> 元素

