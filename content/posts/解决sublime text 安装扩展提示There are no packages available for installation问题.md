---
title: "解决sublime text 安装扩展提示There are no packages available for installation问题"
date: 2019-05-28T08:57:00+08:00
draft: false
categories: ["开发工具"]
tags: ["sublime"]
---

最近想给sublime编辑器装个插件，发现总是报这个错误

![](https://oscimg.oschina.net/oscnet/e95d7078ef679f8c95b9f7b172f511ac8c5.jpg)

百度一下，发现是设置Preferences->Package settings -> Package control -> Settings-User里面的"channels": "[https://packagecontrol.io/channel_v3.json](https://packagecontrol.io/channel_v3.json)" 地址被墙了。

解决方法：

1.  将channel_v3.json下到本地，用node启一个服务，然后修改sublime设置：preferences->package settings -> package control -> settings-user，具体修改见下图，地址改为本地地址，也可以使用下面的地址。
2.  我在个人服务器上开了一个服务，开放出来，方便不想麻烦的小伙伴们使用。（[http://139.224.135.43:8000/channel_v3.json](http://139.224.135.43:8000/channel_v3.json)）

![](https://oscimg.oschina.net/oscnet/e6215dd05195a69e5985311b85945502ec8.jpg)