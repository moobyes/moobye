---
layout: post
title: web性能之prefetch和preload
categories: [fontEnd]
tags: [前端, 性能优化, API]
description: 最近在做性能优化的方案，一来用来记录思路，二来将这个过程中的demo记录下来！
fullview: false
comments: true
---
前言

Web 性能--MDN文档地址：[传送门](https://developer.mozilla.org/zh-CN/docs/Web/Performance "web性能")

prefetch，中文名叫链接预取，比较拗口，其实可以叫链接预加载。具体概念见：[prefetch](https://developer.mozilla.org/zh-CN/docs/Glossary/Prefetch)

preload, 是标签 `<link>` 的一个属性，一般在html的head里。具体概念见:  [preload](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Attributes/rel/preload)

这两个都有助于优化 TTI、FCP ( First Content Paint )。

我们通过具体例子来看看它们是怎么优化web性能的。

### prefetch

prefetch的使用如下：

```html
<link rel="prefetch" as="script" href="a.js">
<link rel="prefetch" as="style" href="a.css">
```

- href表示需要预加载的资源路径
- as属性指定预加载资源的类型， 有document、style、script、images
- rel后面跟 **prefetch**

在webpack里，import资源的时候，做如下配置即可

```js
import(/*webpackPrefetch: true */ 'a.js')
```

但我们在工程里使用的时候，可能不会这么直接使用，一般都是在webpack或者vite里配置，使其在打包的过程中自动添加上。

> 忙，后续补上
