---
layout: post
title:  "用ajax实现了评论区"
categories: Other
tags: Other
author: Liu
description: 
---

# 用ajax实现了评论区

## 重点和难点

我分了两个服务器,分别是提交评论的接收服务器,和,页面刷新时候请求的服务器.可以使用路由来做到一个服务器当中.  
跨域问题.  
时间转换为格式化时间.  
汉字的解码.  
提交评论后的回调刷新.  

## 关于页面的一点见解

bootstrap3和bootstrap4有较大的差异,导致适用bootstrap3的类名在bootstrap4中不能体现效果,甚至导致页面乱掉.  
我个人认为,bootstrap3中的导航栏比b4提供的导航栏要好用,但是,b4的卡片,的确好用.  

## 页面的ajax完成后的回调函数

ajax方法的书写方式

    $.ajax({
        type:"GET",
        url:"http://127.0.0.1:3001/",
        data:text,
        dataType:"text",
        success:function(data){
        location.reload(true);
        window.location.reload();
        }
    });    

`dataType:"text"`漏掉了这句话,导致了success:后的函数无法调用.  

## 将两个服务器合并成一个

过程:

1. 将两个服务端的功能实现的代码封装成2个函数
2. 命名两个函数
3. 写路由
4. 用if else 分发路由分别调用两个函数

## 其他

算法:
O(1)称为常量时间,理解为,不管操作n个数据或n亿个数据,总是消耗同样的时间.该时间不是一个具体数值.
字典的名词:散列表(hash table)、散列映射、字典、关联数组。
图的应用的示例：最短步数，从一个地点到另一个地点倒公交车的最少换乘方式。

2019年08月27日14:33:36
