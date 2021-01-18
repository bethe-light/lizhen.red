---
title: Promise基础分析小结
aplayer: true
date: 2018-02-10
updated:
tags: javascript
categories:
keywords: javascript、promise
description:
top_img: /img/promise/promise.png
comments:
cover: /img/promise/promise.png
toc:
toc_number:
copyright:
copyright_author:
copyright_author_href:
copyright_url:
copyright_info:
mathjax:
katex:
highlight_shrink:
aside:
---

**Promise**最基础分析与理解

> * 同步与异步 
>
>   同步是当发起一个请求后，如果未得到结果，会一直等待，知道结果出现；
>
>   异步是当发起一个请求后，不会等待请求的结果，而直接执行后面的代码
>
> * Promise的请求结果 3种
>
>     1 pending 请求中
>
>     2 resolve 得到结果 继续执行
>
>     3 reject 错误结果 拒绝执行
>
> * Promise 解决回调地狱问题,Promise链式流
>
>    回调地狱：不停地嵌套回调函数，确保下一接口所需参数的正确性
>
> * Promise 的then 与 catch 方法
>
>   .then 处理resolved 的逻辑(返回的仍然是Promise 对象 可以继续嵌套处理)
>
>   .catch处理rejected 的逻辑
>
>   then方法有两个参数 第一个处理resolved第二个处理rejected
>
>   所以.catch 方还可以这样表示 
>
>   then(null, function(err) {….})  ===  catch(){...}

> * 存在一个绝望的陷阱
>
>   为了避免丢失被忽略和抛弃的Promise错误，一个最佳实践？？？是最后总是以catch结束，
>
> ```javascript
> var p = Promise.resolve(7);
> p.then(
>     function resolve(res) {
>         console.log(res.toLowerCase);//number 无string函数 报错
>     }
> )
> .catch( handleError );
> ```
>
> 因为前面没有给出错误处理函数，默认的处理函数被替换掉，继续把错误传给下一个Promise，直到传最后的 handleError();
> 令人绝望的陷阱来了，，，尽管可能性较低，但那如果handleError() 内部出现问题如何处理呢？谁来捕捉？看起来无解？
>
> 但是浏览器有代码不能实现的功能，比如追踪Promise对象，确保未被捕获到的错误；

**Promise.all([...])**

> 同时执行两个或多个操作（并行执行），其数组参数可以是Promise，thenable，或者立即值。
>
> 而且如果参数中有任何一个被拒决，Promise.all()就会立即被拒绝，所以永远记得做好错误处理函数；

**Promise.race([...])**

> 有时场景是需要只响应，“第一个到达终点的Promise”,这种模式为“门闩”，即竞态；
>
> 有任何一个Promise决议完成，Promise.race() 就完成，一旦任何一个决议被拒绝，Promise.race()就会拒绝；
>
> 既然竞赛，所以选手必须至少为1，否则为空时，Promise永远处于为决议状态；
>
> ```javascript
> var p1 = Promise.resove(1);
> var p2 = Promise.resove("hi");
> var p3 = Promise.reject("Oops");
> 
> Promise.all([p1,p2,p3])
>     .then(null,function(res) {
>     	console.log(res); //"Oops"
> });
> Promise.race([p1,p2,p3])
>     .then(function(res){
>     	console.log(res); //1
> })
> Promise.all([p1,p2])
>     .then(function(res){
>     	console.log(res); //[1,"hi"]
> })
> ```
>
>

**Promise的局限性** 

> * 顺序错误处理
>
>   Promse链中的错误很容易被忽略，且无外部方法可以观察可能发生的错误，大多说开发者的最佳实践，总是在最后一个promise加上catch() 进行错误捕获；
>
> * 单一值
>
>   Promise只能有一个值，resolve的值，或则 reject的值，在复杂情境中，就会有局限性；
>
>   解决方法：封装一个对象或数组来保存多个这样的信息
>
> * 单决议
>
>   Promise区别于单一值，单决议指Promise只能被决议一次，**只能获取一个值（完成或拒绝）一次**，但如果出现像 **按钮点击**的情景，多次点击的话，就只能获取到第一次点击的值，而其他的都被忽略，
>
>   解决方法：在每次点击时加上id值，为每次点击创建一个·新的promise(可能有点蠢？？？)
>
>   ```javascript
>   click("#btn",function(event) {
>       var btnId = event.currentTarget.id;
>       request("url?id=" + btnId)
>       .then(function(){});
>   })
>   ```
>
> * 惯性  （ 不是很理解这个局限性  :(
>
> * 无法取消Promise
>
>   如果出现没有情况时任务处于未决议状态，是没有办法停止他的进程的；
>
>   解决方法： 使用第三方Promise抽象库asynqueue提供的工具解决，但好像违背了（外部不变性）