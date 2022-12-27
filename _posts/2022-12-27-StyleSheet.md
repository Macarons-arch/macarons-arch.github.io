---
layout: post
title:  "RN开发-StyleSheet"
categories: React native
tags:  StyleSheet
author: 何勇
---

* content
{:toc}


# RN中的样式与CSS的不同

    ·没有继承性（声明在父元素的样式会作用在子元素上，div标签样式作用p标签。rn中只有text具有继承性）
    ·样式名采用小驼峰命名（CSS:font-size, RN:fontSize）
    ·所有尺寸都是没有单位
    ·有些特殊的样式名（marginHorizontal水平外边距, marginVertical垂直外边距）
    
# RN样式的声明方式
    ·通过style属性直接声明
        ·属性值为对象:<组件 style={{样式}}/>
        ·属性值为数组:<组件 style={[{样式1}, ..., {样式N}]}>。如果样式重叠，后面的样式会覆盖前面的
    ·在style属性中调用StyleSheet声明的样式
        ·引入:import {StyleSheet, View} from 'react-native'
        ·声明:const styles = StyleSheet.create({ foo: {样式1}, bar: {样式2}})
        ·使用:<View style = {[ styles.foo, styles.bar]}>内容</View>

