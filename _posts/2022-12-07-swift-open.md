---
layout: post
title:  "swift中的open关键字"
categories: swift
tags:  swift
author: 何勇
---

* content
{:toc}

#open
    swift 3.0之后，访问权限加入open
    权限由低到高分别是<font color="#dd4433">open</font>（公开权限）、 <font color="#dd4433">public</font>（公有访问权限）、<font color="#dd4433">internal</font>（内部权限也是默认权限）、<font color="#dd4433">fileprivate</font>（文件私有权限）、<font color="#dd4433">private</font>（私有权限）五个
    |Swift Access Control|
    |:----:||:----:|
    |Keywords||Accessible|
    |<font color="#dd4433">private</font>||ClassA|||||||
    |<font color="#dd4433">fileprivate</font>||ClassA|
    |Extension Class A|||||
    |<font color="#dd4433">internal</font>||ClassA||Extension Class A|||||
    |<font color="#dd4433">public</font>||ClassA||Extension Class A|||||
    |<font color="#dd4433">open</font>||ClassA|
    |Extension Class A||Class B:A||Extension Class B|
    
open,internal，defer,public enum

