---
layout: post
title:  "swift中的一些陌生关键字"
categories: swift
tags:  swift
author: 何勇
---

* content
{:toc}

# open
    swift 3.0之后，访问权限加入open
    权限由低到高分别是<font color="#dd4433">open</font>（公开权限）、 <font color="#dd4433">public</font>（公有访问权限）、<font color="#dd4433">internal</font>（内部权限也是默认权限）、<font color="#dd4433">fileprivate</font>（文件私有权限）、<font color="#dd4433">private</font>（私有权限）五个


# defer
    defer被执行后，块内代码不会立刻执行，而是等待当前作用域结束后执行。
    defer块甚至晚于catch。
    多个derfer块会以栈的形式存储，最后的defer先执行。
