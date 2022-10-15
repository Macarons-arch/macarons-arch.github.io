---
layout: post
title:  "从埃筛到欧拉筛"
categories: ACM
tags:  质数
author: 何勇
---

* content
{:toc}


## 前言

埃式筛法是第一个比较先进的筛法，以后的所有筛法大多都是以埃筛为基础推进的
埃筛的思想也很简单，筛掉所以素数的倍数，最后还剩的就是素数

```c
bool isprime[maxn];
void Eratosthenes_prime(){
    memset(isprime,true,sizeof isprime);
    isprime[0]=isprime[1]=false;
    for(int i=2;i<maxn;i++){
        if(isprime[i])
            for(int j=i+i;j<maxn;j+=i)
                isprime[j]=false;
    }
}
```
```c
bool isprime[maxn];
int prime[maxn/10],tot;
void Euler_prime(){
    memset(isprime,true,sizeof isprime);
    isprime[0]=isprime[1]=false;
    for(int i=2;i<maxn;i++){
        if(isprime[i])prime[tot++]=i;
        for(int j=0;j<tot&&prime[j]<=maxn/i;j++){
            isprime[i*prime[j]]=false;
            if(i%prime[j]==0)break;
        }
    }
}
```

欧拉筛唯一亮点所在在于if(i%prime[j]==0)break;这句，是从埃筛提升到欧拉筛的关键
欧拉筛的时间是O（n）。

上面这个欧筛中的isprime数组其实是作用不大的，我们可以把它换成欧拉函数，适当的我们也可以添加莫比乌斯函数

```cpp
int prime[maxn/10],phi[maxn],mu[maxn],tot;
void Euler(){
    phi[1]=1;
    for(int i=2;i<maxn;i++){
        if(!phi[i]){
            phi[i]=i-1;
            prime[tot++]=i;
            mu[i]=-1;
        }
        for(int j=0;j<tot&&prime[j]*i<maxn;j++){
            if(i%prime[j]==0){
                phi[i*prime[j]]=phi[i]*prime[j];
                mu[i*prime[j]]=-mu[i];
                break;
            }
            phi[i*prime[j]]=phi[i]*(prime[j]-1);
            mu[i*prime[j]]=0;
        }
    }
}
```

除此之外，比较先进的素筛算法还有Min_25筛，杜教筛，洲阁筛
三种筛法时间都在O（n）之下，有些出题人就喜欢把数据故意整到1e10，就看你会不会这三种先进筛法

