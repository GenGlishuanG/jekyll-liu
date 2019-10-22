---
layout: post
title:  "JavaScript之四"
categories: Other
tags: JavaScript
author: Liu
description: 
---
# 2019年07月26日21:57:36

## 出现的问题

    'use strict';
    const Koa=require('koa');
    const router=require('koa-router')();
    const app=new Koa();
    app.use(async(ctx,next)=>{
        console.log(`Process ${ctx.request.method} ${ctx.request.url}...`);
        await next();
    });
    router.get('/KoaProj/:name',async(ctx,next)=>{
        var name=ctx.params.name;
        ctx.response.body=`<h1>Hello,${name}</h1>`;
    });
    // router.get('/',async(ctx,next)=>{
    //     ctx.response.body=`<h1>Index</h1>`
    // });
    router.get('/', async (ctx, next) => {
        ctx.response.body = `<h1>Index</h1>
            <form action="/signin" method="post">
                <p>Name: <input name="name" value="koa"></p>
                <p>Password: <input name="password" type="password"></p>
                <p><input type="submit" value="Submit"></p>
            </form>`;
    });
    router.post('/signin',async(ctx,next)=>{
        console.log('///////////////////////////')
        console.log(ctx.request);
        console.log(ctx.request.body);
        console.log(typeof(ctx.request.body));
        var name=ctx.request.url.name || "",
            password=ctx.request.body.password || '';
        console.log(`signin with name:${name},password:${password}`);
        if (name==="Koa" && password==="123456") {
            ctx.response.body=`<h1>Welcom! ${name}</h1>`;
        } else {
            ctx.response.body=`<h1>Try again</h1>
            <p><a href='/'>点击这里</a></p>`;
        }
    });
    // add router middleware:
    app.use(router.routes());
    app.listen(3001);
    console.log("app Running at Port 3001 ...");

以上，是整体的代码，但是出现了一些问题，浏览器点击了submit按钮后导致服务端出错。

    let js_files = files.filter((f)=>{
        return f.endsWith('.js');
    }, files);

equalequaleeequaleequaleequaleequaleequleequaleequaleequaleequaleequaleequaleequaleequaleequaleequealeeuqequaleequaleequaleequaleequaleeeequaleequequequequequequequequaleequaleequaleequaleequaleequdaleequaleequaleequaleequaleequaleequdaleeeqequdaleequequaleequaleqequaleequaleequaleequaleequaleequaleequaleequequaleequaleequaleequaleeequaleequaleequaleequaleequaleequaleequaleequaleequequaleequaleeequelaequaleequaleequaleequaleequaleequaleequaleequaleequaleeaueqlequaleequaleequaleequaleeqequaleequaleequaleequaleequaleeauqequaleequalequququququququuqququqwuuwuwuwwuuwwuu2quuquququququququququququququququququququququequequeuequequeuqequeuqequequequequequequequequequequeuqequeuqequaleequalealalealealealealealealealealtaltatlalttalaltaltaltatlatlaltaltaltaltaltatlaltatlaltatlaltatlaltatlatlaltatlatlatlaltequeequaleqequequequequaltequaltequaleequaleequaleequaleeaequaleqeequalequeequaleequaleequaleeauequaleequaleequaleequaleeaequaleraurequirerequirerequirerequirerequirereququrequireireireireirerequerequirerequireququrequrequirerequirestrstrststestrstrstrstrstrstrstrictstrictstrictequaleequaleequalestrictstrictbenotingisequalestrictstrictctctctctccctctctstrictbibeautifulbeautifulululullululullulululullulkkillkillalivealivealivealivetypetypeprintsunksumsunsumsumsumsumsumsunhuyouimportantlearnenglishlearnlearnenglishlearn  

it('test async function')