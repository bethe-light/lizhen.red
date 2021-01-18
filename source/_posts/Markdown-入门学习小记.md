---
title: Markdown--入门学习小记
aplayer: true
date: 2018-01-08 01:51:44
updated:
tags: web
categories:
keywords: markdown
description:
top_img: /img/markdown/markdown.jpg
comments:
cover: /img/markdown/markdown.jpg
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

## 一 · 初识markdown

>很早前就被室友强烈安利Markdown，于是网上看个大概，开始不明白为什么一个编辑文档的为啥还会有很多语法，当时可能接触到的东西比较有>限，也没有需要用到markdown 的地方，而且做笔记都是用微软的官方Onenote，所以并不是很在意。
>现在搭建了自己的博客，也使用了部分社区的后台编辑器，都是不同程度的支持markdown，emmmmm 原来这么好用，简洁大方，很是优雅！

>[Markdown](https://zh.wikipedia.org/wiki/Markdown) 是一种可以使用普通文本编辑器编写的标记语言，通过简单的标记语法,使普通文本内容具有一定的格式。
一般会使用markdown写博客，用 [latex](https://www.latex-project.org/) 写论文。  

## 二·markdown 语法指南  

> * 这里是创始人的[markdown syntax](https://daringfireball.net/projects/markdown/syntax) （膜）
> * 优点：简约 直观 高效 方便 简直神器
> * 工具： 笔者现在使用 vscode 的mrakdown 插件，已经符合我的要求；当然还有一些吊炸天的神器,比如：[typora](https://typora.io/#) （很强大很cool 保你用一次就会爱上它，不吹不黑。。。）

## 换行
两个空格 + 换行 即可 不要忘记  
否则效果会很不尽人意  

## 标题  
**语法**：  
> 使用 # 一级  ## 二级 ###三级  共有六级

**效果**：  
# #一级标题
## ##二级标题
### ###三级标题
#### ####四级标题
##### #####五级标题
***
### 粗体斜体划线
**语法**：

> 内容左右两侧各两个* 表示粗体  
>内容左右两侧各一个* 表示斜体  
>内容左右两侧各三个* 粗体加斜体  
>内容左右两侧各两个~~ 表示划线  

**效果**：

> **我是粗体**   
> *我是斜体*   
> ***粗体加斜体***  
> ~~我是删除的内容~~ 

## 超连接

**语法**：  
> 分为行内式 与 参考式 很少用到参考式<br>[内容]（URL）
<br> 内容在[ ]内,URL地址放在（）内

**效果**：
> [baidu]（www.baidu.com）-> [百度](https://www.baidu.com)

## 图片

**语法**:
> 与超链接特别像，区别是 在前面加上 ！  
！[图片alt]（URL "图片title"）  

## 引用  
**语法**：   
> 在需要引用的语句前面加 >  
即   > 引用内容  

**效果**：  
> >我是引用内容  

## 分割线  
**语法**：  
> 三个以上的 * 即可  

**效果**：  
  
***    

## 列表  
**语法**：  
> 无序 -/*/+ 三个符号均可以，看个人习惯使用  
有序 1. 2. 像这样使用即可  
注意： 无序时 符号与内容见需要一个空格  
有序时 加空格与无空格区别是 缩进  
**嵌套列表** 二级列表在前面加 两个空格   

**效果**：  
> - nsanicad（-）    
> * jasbd（*）  
> + akndiwn（+）  
> * 一级  
    * 二级无序（前面加俩空格）  
    2. 二级有序    

## 代码  
**语法**：  
> 行代码使用 `  反引号包含自己的行代码即可  
块代码的话 ```  六个反引号包含代码即可 上下个三个反引号 必须都单独占  据一行，否则此行代码不显示

**效果**：  

` console.log("I love you!") `  

***  

```  
  (function f() {  
     console.log(but,where are you?)  
   })();  
```  
## 表格  
**语法**：  
> 第一行：表头，用 | 管道符分割  name | age | gender  
> 第二行：格式，-|：-：|-:  
> 右侧加 ： 则右对齐，两侧加 ： 则居中  
> 中间短横线至少一个即可  
> 第三行：表格内容，默认左对齐

**效果**： 
> name|age|gender  
> ---|:-:|-----:  
> json|18|man  
> john|18|women  

## 流程图  
**语法**：  
> flow (真正使用时不要忘记在flow前,后面各添加三个``` 反引号)  
s=>start: start  
o=>operation: Operation  
c=>condition: Yes or No?  
e=>end  
s->o->c  
c(no)->o  
c(yes)->e  

**效果**:
> 我的博客系统貌似不支持流程图（哭 :_: ）  
```  flow   
st=>start: start  
op=>operation: My Operation  
cond=>condition: Yes or No?  
e=>end  
st->op->cond  
cond(no)->op  
cond(yes)->e  
```  
***  
## 原生HTML语法  
> 支持部分HTML原生的语法使用 <br/>  可用 br 表示换行  
h1 一级标题 等等 HTML语法可以直接markdown中使用，cool

## 小结  
表格语法有点烦，如果想要更多样式，可以通过HTML的语法格式
流程图可能不太会用到，但时常梳理自己逻辑也是不赖的一件事 
慢慢培养记笔记并形成博客总结的习惯，即使费点时间但是收获也是很大的，加油，21天养成习惯！