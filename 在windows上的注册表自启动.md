---
title: 在windows上的注册表自启动
category: 关于渗透的那些事
updatedAt: 2024-04-14T08:58:58.941Z
createdAt: 2024-04-14T08:40:37.970Z
---

# 在Windows上的注册表自启动

### 在内网或者渗透中，我们时常需要自启动或者基于主机的持久化有基于注册表的自启动或者基于文件夹的自启动`shell:startup`


在通过注册表自启动，主要是有 `Run` 和 `RunOnce` ，其中RunOnce和Run区别在于RunOnce的键值只作用一次，执行完毕后会自动删除。
- 操作方式如下：

<!-- more -->

- 按`Windows + R`输入`regedit`进入注册表
- 有以下这几个位置
```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnceEx
```