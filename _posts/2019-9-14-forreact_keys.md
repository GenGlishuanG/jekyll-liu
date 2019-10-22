---
layout: post
title:  "npm start"
categories: Other
tags: Other
author: Liu
description: 
---
# 2019年9月14日

## 一个之前没有解决的问题

src里面的App.js文件,未改动之前在npm start 时没有问题,只要一改动,npm start命令就会报错

## 其他

React 和它的生态是拥抱不可变的。这就是为什么 const 应该是你定义一个变量时的默认
选择。当然，一个复杂的对象中的内容还是可能会被改变，请当心这种改变。

你应该用 const 来代替 var。


import React,{Component}from'react';
import './App.css';
class App extends Component {
    render(){
        const helloWorld='Welcome to the Road to learn React';
        return (
            <div><h2>{helloWorld}</h2></div>
        );
    }
}
export default App;



src/index.js 里的内容
import React from 'react';
imoort ReactDOM from 'react-dom';
import App from './App';
import './index.css';

ReactDOM.render(
    <App />,
    document.getElementById('root')
);
简单来说，ReactDOM.render() 会使用你的 JSX 来替换你的 HTML 中的一个 DOM 节点

code playground 

ReactDOM.render(
    <h1>helloWorld</h1>,
    documnet.getElementById('root')
);
打开 public/index.html 文件，找到 React 应用并放置在你的 HTML 的位置





https://d11.baidupcs.com/file/ed33bec4658147a3f2e363d196fea23f?bkt=en-06f5c65000af0ed664436b289ce56462b6f13ea66b08af294c7645b0f79a7dc412787f87088354b6&xcode=e8024d28054dc3d0230ddee92225b316e138eba0953d154c24d68ff4f9d0dc92babc07f6c130bbe492c8a591117113f99a7e3ac4ae9d7ad8&fid=1343582379-250528-335486848762238&time=1568793629&sign=FDTAXGERLQBHSKf-DCb740ccc5511e5e8fedcff06b081203-RG0qf%2BxYACoKUUga2ISzVqsAL9E%3D&to=d11&size=22891620&sta_dx=22891620&sta_cs=471&sta_ft=flac&sta_ct=5&sta_mt=3&fm2=MH%2CQingdao%2CAnywhere%2C%2Cbeijing%2Ccnc&ctime=1565138564&mtime=1568099585&resv0=cdnback&resv1=0&resv2=&resv3=&vuk=1343447887&iv=0&htype=&randtype=&newver=1&newfm=1&secfm=1&flow_ver=3&pkey=en-ac32714b9d547f88f08e3a89486e55690c482ccc3a132b187fb896688eb68670ffab9e877eaa8d59&sl=76480590&expires=8h&rt=sh&r=307939649&vbdid=4120088065&fin=%E7%8E%8B%E8%B4%B0%E6%B5%AA+-+%E5%BE%80%E5%90%8E%E4%BD%99%E7%94%9F.flac&fn=%E7%8E%8B%E8%B4%B0%E6%B5%AA+-+%E5%BE%80%E5%90%8E%E4%BD%99%E7%94%9F.flac&rtype=1&dp-logid=6045603862485104026&dp-callid=0.1&hps=1&tsl=80&csl=80&csign=JHqMyYdH7w%2BMfaNAPMheYpZxGMs%3D&so=0&ut=6&uter=4&serv=0&uc=1694538685&ti=d8768d13a65657de8472f9e9bca7254dbf6adeb0e52632bb&by=themis