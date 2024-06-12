---
title: 利用windows powershell 隐藏执行后门
category: 关于渗透的那些事
updatedAt: 2024-03-16T11:15:41.441Z
createdAt: 2024-03-16T11:06:19.273Z
---

# 利用windows powershell 隐藏执行后门
运行后门时，有些后门不能中断。双击运行这种后门会产生一个黑框。 一条命令就能使其在后台执行。
![1](http://byte2023.icu/static/img/dee90b0ff6180bef52e2e28193f76586.7ab6051426bba7619db6a4c898328e5b.image.webp)

<!-- more -->


命令解释： 
```cmd
start-process   -windowstyle hidden
 启动一个进程      窗口样式   隐藏

```