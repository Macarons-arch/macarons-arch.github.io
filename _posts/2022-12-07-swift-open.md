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
    
# frozen
Library evolution:动态库的链接时间推迟到运行时（违背静态语言特性）。build library for distribution置为yes，针对动态库的配置
冻结。结构体，枚举等在编译时就确定（swift静态语言特性）
    
# @objc
关于swift的动态性，swift是静态语言，但在swift中所有继承自NSObject的类都保留了OC的动态性。如果想使用它的动态性，就必须加上@objc关键字。以下情况需要用到@objc
1.Protocol如果是optional的，必须加上@objc
    ```swift
    @objc protocol PlayerDelegate: class {
    
        @objc optional func playerReadyToPlay(player: CustomMediaPlayer, totalTime: Double)
        
        @objc optional func playerCacheProgress(player: CustomMediaPlayer, progress: Float)
            
        func playerPlayProgress(player: CustomMediaPlayer, currentTime: Double)
    }
    ```
2.利用#selector调用的方法，被调用的方法必须加上@objc
3.使用kvc时
4.NSPredicate筛选
5.oc与swift混合开发，swift方法/属性需要被oc调用的，要加上@objc
6.swift的枚举需要被oc使用的
    
# @objcMembers
在Swift中，继承自NSObject的类如果有比较多的属性或方法都需要加上@objc的话，会多比较多的代码。那么可以利用@objcMembers减少代码。被@objcMembers修饰的类，会默认为类、子类、类扩展和子类扩展的所有属性和方法都加上@objc。当然如果想让某一个扩展关闭@objc，则可以用@nonobjc进行修饰。
