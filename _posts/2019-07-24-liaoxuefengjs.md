---
layout: post
title:  "Javascrip之二"
categories: Other
tags: Javascrip
author: Liu
description: 
---

# 运算符

&&
||
比较运算符
当我们对Number做比较时，可以通过比较运算符得到一个布尔值：  

    2 > 5; // false
    5 >= 2; // true
    7 == 7; // true
    false == 0; // true
    false === 0; // false

JavaScript的设计者希望用null表示一个空的值，而undefined表示值未定义。事实证明，这并没有什么卵用，区分两者的意义不大。大多数情况下，我们都应该用null。undefined仅仅在判断函数参数是否传递的情况下有用。

JavaScript的对象是一组由键-值组成的无序集合，例如：

    var person = {
        name: 'Bob',
        age: 20,
        tags: ['js', 'web', 'mobile'],
        city: 'Beijing',
        hasCar: true,
        zipcode: null
    };

JavaScript对象的键都是字符串类型，值可以是任意数据类型。上述person对象一共定义了6个键值对，其中每个键又称为对象的属性，例如，person的name属性为'Bob'，zipcode属性为null。

要获取一个对象的属性，我们用对象变量.属性名的方式：

    person.name; // 'Bob'
    person.zipcode; // null

声明变量的方式：

    var a; // 申明了变量a，此时a的值为undefined
    var $b = 1; // 申明了变量$b，同时给$b赋值，此时$b的值为1
    var s_007 = '007'; // s_007是一个字符串
    var Answer = true; // Answer是一个布尔值true
    var t = null; // t的值是null

ASCII字符可以以\x##形式的十六进制表示，例如：

    '\x41'; // 完全等同于 'A'

由于多行字符串用\n写起来比较费事，所以最新的ES6标准新增了一种多行字符串的表示方法，用反引号 * ... * 表示：

    `这是一个
    多行
    字符串`;

要获取字符串某个指定位置的字符，使用类似Array的下标操作，索引号从0开始：

    var s = 'Hello, world!';
    s[0]; // 'H'
    s[6]; // ' '
    s[7]; // 'w'
    s[12]; // '!'
    s[13]; // undefined 超出范围的索引不会报错，但一律返回undefined

indexOf()会搜索指定字符串出现的位置，如果是在array中使用同理：

    var arr = [10, 20, '30', 'xyz'];
    arr.indexOf(10); // 元素10的索引为0
    arr.indexOf(20); // 元素20的索引为1
    arr.indexOf(30); // 元素30没有找到，返回-1
    arr.indexOf('30'); // 元素'30'的索引为2

    var s = 'hello, world';
    s.indexOf('world'); // 返回7
    s.indexOf('World'); // 没有找到指定的子串，返回-1

请注意，直接给Array的length赋一个新的值会导致Array大小的变化：

    var arr = [1, 2, 3];
    arr.length; // 3
    arr.length = 6;
    arr; // arr变为[1, 2, 3, undefined, undefined, undefined]
    arr.length = 2;
    arr; // arr变为[1, 2]

Array可以通过索引把对应的元素修改为新的值，因此，对Array的索引进行赋值会直接修改这个Array：

    var arr = ['A', 'B', 'C'];
    arr[1] = 99;
    arr; // arr现在变为['A', 99, 'C']

请注意，如果通过索引赋值时，索引超过了范围，同样会引起Array大小的变化：

    var arr = [1, 2, 3];
    arr[5] = 'x';
    arr; // arr变为[1, 2, 3, undefined, undefined, 'x']

pop() 删除最后一个；
shift() 删除第一个；
unshift() 在第一个插入；
push() 在最后一个插入；  

关于箭头函数不理解的一个代码：

        var arr = [10, 20, 1, 2];
        arr.sort((x, y) => {
            ???
        });
        console.log(arr); // [1, 2, 10, 20]



    location.protocol; // 'http'
    location.host; // 'www.example.com'
    location.port; // '8080'
    location.pathname; // '/path/index.html'
    location.search; // '?a=1&b=2'
    location.hash; // 'TOP'

要加载一个新页面，可以调用location.assign()。如果要重新加载当前页面，调用location.reload()方法非常方便。

通常，上传的文件都由后台服务器处理，JavaScript可以在提交表单时对文件扩展名做检查，以便防止用户上传无效格式的文件：

    var f = document.getElementById('test-file-upload');
    var filename = f.value; // 'C:\fakepath\test.png'
    if (!filename || !(filename.endsWith('.jpg') || filename.endsWith('.png') || filename.endsWith('.gif'))) {
        alert('Can only upload image file.');
        return false;
    }

if判断不理解  

    if (file.type !== 'image/jpeg' && file.type !== 'image/png' && file.type !== 'image/gif') {
            alert('不是有效的图片文件!');
            return;

这样或许更明白清晰  

## node.js

安装node.js;
node -v;
node 进入node交互界面；
npm Node pack package manager，管理工具包；
npm -v;



