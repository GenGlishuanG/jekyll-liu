---
layout: post
title:  "sass快速入门"
categories: Other
tags: sass
author: Liu
description: 
---
# 2019年8月16日

## sass

阅读sass快速入门的文章.同时敲里面的代码段.  

    混合器在某些方面跟css类很像。都是让你给一大段样式命名，所以在选择使用哪个的时候可能会产生疑惑。最重要的区别就是类名是在html文件中应用的，而混合器是在样式表中应用的。这就意味着类名具有语义化含义，而不仅仅是一种展示性的描述：用来描述html元素的含义而不是html元素的外观。而另一方面，混合器是展示性的描述，用来描述一条css规则应用之后会产生怎样的效果。

摘抄这一段.因为这一段是对混合器和css类的综述.

## 关于git

没有什么好写的了.详见今天另一个.md文件 

## sass难点

接下来的这段代码定义了一个名为disabled的类，样式修饰使它看上去像一个灰掉的超链接。通过继承a这一超链接元素来实现：

    .disabled {
    color: gray;
    @extend a;
    }

假如一条样式规则继承了一个复杂的选择器，那么它只会继承这个复杂选择器命中的元素所应用的样式。举例来说， 如果.seriousError@extend.important.error ， 那么.important.error 和h1.important.error 的样式都会被.seriousError继承， 但是.important或者.error下的样式则不会被继承。这种情况下你很可能希望.seriousError能够分别继承.important或者.error下的样式。
如果一个选择器序列（#main .seriousError）@extend另一个选择器（.error），那么只有完全匹配#main .seriousError这个选择器的元素才会继承.error的样式，就像单个类 名继承那样。拥有class="seriousError"的#main元素之外的元素不会受到影响。
像#main .error这种选择器序列是不能被继承的。这是因为从#main .error中继承的样式一般情况下会跟直接从.error中继承的样式基本一致，细微的区别往往使人迷惑。