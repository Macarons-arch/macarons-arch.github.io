---
layout: post
title:  "fishhook之msg_send"
categories: iOS
tags:  反汇编
author: 何勇
---

* content
{:toc}



# hook_objc_msgSend的实现

```C
__attribute__((__naked__))
static void hook_objc_msgSend() {
    //before之前保存objc_msgSend的参数
    save()
    
    //将objc_msgSend执行的下一个函数地址传递给before_objc_msgSend的第二个参数x0 self, x1 _cmd, x2: lr address
    __asm volatile ("mov x2, lr\n");
    __asm volatile ("mov x3, x4\n");
    
    // 执行before_objc_msgSend   blr 除了从指定寄存器读取新的 PC 值外效果和 bl 一...
    call(blr, &before_objc_msgSend)
    
    // 恢复objc_msgSend参数，并执行
    load()
    call(blr, orig_objc_msgSend)
    
    //after之前保存objc_msgSend执行完成的参数
    save()
    
    //调用 after_objc_msgSend
    call(blr, &after_objc_msgSend)
    
    //将after_objc_msgSend返回的参数放入lr,恢复调用before_objc_msgSend前的lr地址
    // x0 是整数/指针args的第一个arg传递寄存器 x0 是整数/指针值的（第一个）返回值寄存器
    __asm volatile ("mov lr, x0\n");
    
    //恢复objc_msgSend执行完成的参数
    load()
    
    //方法结束,继续执行lr
    ret()
}
```
