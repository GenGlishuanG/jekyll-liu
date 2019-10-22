---
layout: post
title:  "刚开始看react"
categories: Other
tags: Other
author: Liu
description: 
---
# 刚开始看react

## 对不理解的名词的注解

单页Web应用
（single page web application，SPA）
就是只有一张Web页面的应用。单页应用程序 (SPA) 是加载单个HTML 页面并在用户与应用程序交互时动态更新该页面的Web应用程序。[1]  浏览器一开始会加载必需的HTML、CSS和JavaScript，所有的操作都在这张页面上完成，都由JavaScript来控制。

·速度：更好的用户体验，让用户在web app感受native app的速度和流畅，
·MVC：经典MVC开发模式，前后端各负其责。
·ajax：重前端，业务逻辑全部在本地操作，数据都需要通过AJAX同步、提交。
·路由：在URL中采用#号来作为当前视图的地址,改变#号后的参数，页面并不会重载。
·用到的技术其实还是HTML+CSS+JavaScript

## 单页web应用开发流程

用循环的视角审视Web应用开发
框定一个一致的SPA图形用户界面（GUI）和模型
将SPA的原则带回服务器端
聚集于对合适的应用进行早期SPA开发

## 搜罗到的其他点

React中的组件可以通过两种方式定义：ES6类组件和功能无状态组件。后者只是将输入和返回元素作为输出的函数。它们仍然是组件。它们是没有任何样板的组件，因为您只需定义常规JavaScript函数。我不能说Angular使定义组件变得容易。





## 以下都是瞎敲出来的小示例

    function Button ({onclick,children}){
        back(
            <button onClick={onClick} type="button">
                {children}
            </button>
        )
    }


    <input
        value={this.state.value}
        onChange={(event) => this.setState({value:event.tatget.value})}
        type="text"
    />
单向数据流使React状态管理可预测和可维护。


