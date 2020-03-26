---
layout: post
title: 利用Clash代理加速Switch下载
slug: clashrtoswitch
date: 2020-03-21 23:30
status: publish
author: KOI
categories: 
  - clash
tags:
  - Switch
  - ClashR
excerpt: 优雅的使用Clash
---

## 前言

鉴于现在Switch在线下载游戏的速度实在是太慢，更换dns效果也不是很明显。经过一番折腾，用Clash(R)成功给Switch连上了代理，这里我就简单分享下。

### 电脑端配置

1.首先要先获取你的Clash(R)订阅，在Profiler处一键导入到你的Clash(R)客户端。再切换到Proxies界面，选择合适的节点。

![](.\images\clashr01.png)

选完节点以后回到General主界面。将Allow LAN和System Proxyz开关打开。

![](.\images\clashr02.png)

接着鼠标移至Allow LAN处查看本机局域网IP并记下，稍后会用到。

![](.\images\clashr03.png)

### Switch主机配置



1.打开Switch 并在设置里找到互联网，更改当前连接wifi的设置，代理服务器设为启用，服务器ip填写刚刚记住的本机局域网IP，端口一般默认为7890.DNS设置可改可不改，这里推荐阿里的DNS：233.5.5.5 谷歌的：8.8.8.8

![](.\images\switch01.jpg)

设置完毕后点击保存，连接到此网络，提示连接成功即可。

![](.\images\switch02.jpg)

来跑下测速把！

![](.\images\switch03.jpg)

可以看到下载速度比之前快了不少。

